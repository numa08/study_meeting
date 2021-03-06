!SLIDE

## GitとAndroidのあれこれ

!SLIDE

### おしながき

- Gitについて
- Gitのホスティングサービス、Bitbucketについて
- Androidについて
    - 4大コンポーネントとは
    - ライフサイクルとは
    - バッドパターンについて

!SLIDE

### Gitについて

- そもそもバージョン管理システムって？
- 分散バージョン管理システムって？

!SLIDE
### バージョン管理システム

- バージョン管理システム以前と言えば？
- ファイル名の末尾に日付
- 職人（笑）の目による差分取得
- ｴｸｾﾙに変更履歴の記入

!SLIDE
### バージョン管理システム

- バージョン管理システム以前
    - 誰が
    - いつ
    - 何を
    - どのように

変更をしたのかが不明瞭だった

!SLIDE
### バージョン管理システム

- 変更を明確にした
- 過去に遡れるようにした
- 作業者を明確にした

!SLIDE
### Git

- 分散バージョン管理システム
    - チーム開発用
    - ローカルで変更を貯めていく
    - サーバーに転送して共有する

!SLIDE
### Git

- ローカルリポジトリ
    - 個人の作業リポジトリ
- リモートリポジトリ
    - みんなで共有するリポジトリ
    - サーバー
    - GitHub
    - Bitbucket
    - Gitlab

!SLIDE
### コミット

- commit
    - 変更を適応すること
    - 誰が、いつ、何を、どのように
    - 後から戻れるように

!SLIDE
### コミット

- 誰が？
    - Git configの設定で勝手に入る

!SLIDE
### コミット

- いつ？
    - 日付
    - 変更された「順番」

!SLIDE
### コミット

- 何を？
    - コミットメッセージ
    - 簡潔に
    - 何をやったのかを見ただけで分かるように
    - 日付や名前は不要

!SLIDE
### コミット

- どのように？
    - コードの変更そのもの
    - メッセージと相違無いようにする
    - 大きすぎると見難い

!SLIDE
### コミット

- 後から戻れる
    - コミット時点に戻って作業ができる
    - コミットはビルドが通るものを
    - コミットはテストが通るものを

!SLIDE
### ブランチ

- branch
    - コミットの固まり
    - 意味のある固まり
    - 別のブランチに取り込む

!SLIDE
### ブランチ

- コミットの固まり
    - ブランチ間は基本、作用しあわない
    - 他の人の変更の影響を受けないよう変更できる

!SLIDE
### ブランチ

- 意味のある固まり
    - 機能毎にブランチを用意する
    - 機能の実装が終わるまでのブランチ
    - ブランチの名前は機能を表すものとかにする
    - 何をやってるのかをはっきりさせる

!SLIDE
### ブランチ

- 意味のある固まり
    - バグFix毎にブランチを用意する
    - バグFixが終わるまでのブランチ
    - ブランチの名前はバグの番号
    - 何をやってるのかをはっきりさせる

!SLIDE
### ブランチ

- 別のブランチに取り込む
    - いわゆるマージ
    - 実装が終わった機能を取り込む
    - 修正が終わったバグを取り込む

!SLIDE
### Bitbucket

- リモートリポジトリを提供してくれる
    - プルリクエストできる
    - Issueを管理できる

!SLIDE
### プルリクエスト

- ブランチのマージを依頼する
    - 必ずコードレビューが入る

!SLIDE
### マージの依頼

- リリース用のブランチがある場合
    - リリースされるソースコードを管理できる

!SLIDE
### コードレビューが入る

- 変更をの共有を強制できる
- コードの品質が上がる
- レビュワー、リクエストした人両方の勉強

!SLIDE
### Issue

- 実装予定の機能
- バグ
- チケットとして管理できる

!SLIDE
### Issue

- ブランチと結びつけて運用する
    - 1ブランチ1issue
    - Issue解決毎にプルリクエスト
    - プルリクエスト通過でIssue終了

!SLIDE
### まとめ

- コミット
    - 変更履歴
    - 何をやったのかすぐ分かるようにメッセージをつける
- ブランチ
    - 機能実装やバグFix
    - 何をやってるのかすぐ分かるように名付ける

!SLIDE
### まとめ
- プルリクエスト
    - ブランチの変更の取り込み依頼
    - コードレビューで変更を共有
- Issue
    - 実装予定の機能やバグの管理
    - ブランチとの連携すると便利

!SLIDE
## Androidについての話

- 4大コンポーネント
- 意識するべきライフサイクル
- バッドパターンとか

!SLIDE
### 4大コンポーネント

- Androidアプリを支える4つの要素
    - エントリポイントになりえる
    - データのやり取りの機能が提供されている
    - フレームワークの思想に則ることができる

!SLIDE
### Activity

- 画面要素
    - 一番使う
    - その分、一番勘違いされる

!SLIDE
### Service

- バックグランドとかで実行される
    - UIは基本的に無い
    - ユーザの見えないところでなんかやる

!SLIDE
### BroadcastReceiver

- UIは持たない
    - コンポーネント間の通信とかに利用できる
    - イベントのハンドリングとかにも使う

!SLIDE
### ContentProvider

- データを提供するためのインターフェース
    - データベースやアプリ内のデータとかを管理する

!SLIDE
### Intent

- コンポーネント間でデータをやりとりする仕組み
- コンポーネントからコンポーネントを呼び出すとか
- でかいデータは渡さないのが鉄則
- Intentを介さないデータのやりとりは危険

!SLIDE
### コンポーネントを利用するメリット

- フレームワークが提供する機能を活用できる
- ライフサイクルに則った実装ができる
- コンポーネントとの連動を意識したAPIが割りとある

!SLIDE
### コンポーネントを利用するデメリット

- コードが若干煩雑になる
- 「お約束」的なアレが多いので
- ライフサイクルを勘違いすると落ちる

!SLIDE
### ライフサイクルとは

- コンポーネントはライフサイクルを持っている
- メモリ管理やUXの提供のために存在する
- JVMの動きとはかなり違う

!SLIDE
### Activityのライフサイクル

![](http://developer.android.com/images/activity_lifecycle.png)

!SLIDE
### Activtiyのライフサイクル

- 破棄されるときは全て破棄される
- staticだろうが捨てられる
- 捨てられると困るものはちゃんと保存する
- 再生成された時の動作を決めておく必要がある

!SLIDE
### Serviceのライフサイクル

- 起動に方法によって違ってくる
- システムによって殺される
- 常時起動しておく物ではない
- 仕事が終わったら死ぬものと思っておこう

!SLIDE
### UIのライフサイクル(View)

- Activityのライフサイクルに加えて意識しておこう
    - 必ずしもActivityのそれと一致しない
    - カスタムビューを作るときは状態の保存を心がけよう

!SLIDE
### UIのライフサイクル(Fragment)

- 今どきFragmentが使えないとかw
    - SupportLibraryを利用して活用しよう
    - 非常にトリッキーな動きをします
    - これの話はまた別でやるかも

!SLIDE
### Applicationのライフサイクル

- Application自体もライフサイクルを持っている
- 取り出すインスタンスによってはリークを生み出す

!SLIDE
### バッドパターンについて

- ライフサイクルを無視するパターン
- リークを生み出すパターン
- 画面サイズを考えてないパターン

!SLIDE
### ライフサイクルを無視するパターン

- 要はstaticな変数
- シングルトンパターンとか
- ライフサイクルの遷移によって容赦なくオブジェクトが捨てられる
- JVMのつもりでいるとバグを生み出す

!SLIDE
### ライフサイクルを無視するパターン

- finalじゃないstaticは利用しない
- 保存したい状態は、onSavedInstanceなどを利用する
- コンポーネント間の通信は必ずIntentなどを利用

!SLIDE
### リークを生み出すパターン

- contextオブジェクトの取得でよくやる
- Activityは破棄されたのに、Activityのcontextを利用してるとか
- いい感じにGCの対象にならないコードを書いてしまう

!SLIDE
### リークを生み出すパターン

- ぶっちゃけ全部対処は難しい
- 非staticな内部クラスは作らない
- ライフサイクルの異なるインスタンスを持つ場合は、弱参照にするなど。。。

!SLIDE
### 仮面サイズを考えてないパターン

- UI実装は様々な画面サイズを考慮しましょう
- 考慮をする画面サイズを決めましょう

