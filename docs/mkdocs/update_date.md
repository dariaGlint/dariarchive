## 日付を導入する

## やること
記事の一番下のフッター部分に記事の公開日や更新日を載せる

## 導入
この記事を参考に導入する
[mkdocs-git-revision-date-plugin で MkDocs のページに更新日を表示する](https://qiita.com/hitsumabushi845/items/b4af60766a8852b08964)

導入が問題なく出来たら一番下のフッター部分に日付が表示される


## ハマったこと
この記事の通りにやったらエラーが出た

```Bash
jinja2.exceptions.UndefinedError: 'None' has no attribute 'meta'
```
調べたらこの記事の所に解決方法があった
[jinja2.exceptions.UndefinedError: 'None' has no attribute 'meta'](https://github.com/zhaoterryy/mkdocs-git-revision-date-plugin/issues/1)


```html
{% if page.meta.revision_date %}
<small><br><i>Updated {{ page.meta.revision_date }}</i></small>
{% endif %}
```
を
```html
{% if page and page.meta.revision_date %}
<br><i>Updated {{ page.meta.revision_date }}</i>
{% endif %}
```
にしたら解決した

## 未解決

1. `mkdocs.yml`に以下を追加
```yaml
plugins:
- git-revision-date:
    as_datetime: true
```

2. `main.html`の日付変更部分を下記に変更
```html
<small><br><i>Updated {{ page.meta.revision_date.strftime("%Y年%m月%d日") }}</i></small>
```

3. bashで`mkdocs build`をすると以下のエラーが出る
```Bash
ERROR   -  Error reading page 'index.md': decoding to str: need a bytes-like object, datetime.datetime found
```

日付が出ていれば目的は達しているので、フォーマットは一旦保留にしてあるので気になったら実装する
