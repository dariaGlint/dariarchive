# markdown
## 画像の追加
相対パスの画像の追加は![]の後の()の中にカーソルを持ってきて、Ctrl+Spaceを2回押すと全体の候補が出てくる
![](../img/relative_image.png)


## PlantUML
Markdownで設定するには「設定」→「言語&フレームワーク」→「Markdown」
→「PlantUML」にチェックを入れるだけ

![画像](../img/markdown_setting_plantuml.png)

基本的な使い方は以下

```plantuml
@startuml
Bob->Alice : Hello!
'コメントは一行だけならこれ
/' 
複数行コメント書くならこれ
'/
@enduml
```

知らなかったけどマインドマップもかけるらしい
```plantuml

@startmindmap
* root node
    * some first level node
        * second level node
        * another second level node
    * another first level node
@endmindmap
```