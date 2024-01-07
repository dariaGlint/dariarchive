## 導入
1. クローンしたリポジトリのディレクトリに`.github/workflows`ディレクトリを作成して、`ワークフロー名.yaml`を追加する
2. `ワークフロー名.yaml`を記載したら、派生ブランチだったらmainブランチにPullRequestを送る
3. `main`ブランチにマージされたら実行できるようになる


## 分かってないこと/調べきれてないこと
### 派生ブランチに`workflows/ワークフロー名.yaml`を追加しても手動で実行できない？

下記の設定ではmainブランチにマージされるまで実行できなかった
```yaml
on:
  push:
    branches:
      - main
```


## ハマったこと

### 権限が足りない

github Actionsを用いて
```Bash
mkdocs gh-deploy
```
を実行しようとしたときに以下のエラーが出た
```Bash
remote: Permission to gitのリポジトリのURL denied to github-actions[bot].
```

エラーの内容で調べたら[こちらのサイト](https://zenn.dev/osawa_koki/articles/a63b96a2707a8f
)で権限が足りないみたいなので、`ワークフロー名.yaml`に以下を追加したら実行できた

```yaml
permissions:
  actions: write
  checks: write
  contents: write
```