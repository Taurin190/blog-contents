アウトプットの重要性を感じ、ブログサイトを作成しました。
Qiitaやはてブを使わずに一から作成することで、一から作れるかを確かめられ、
学び直しと次の課題を考えることが出来ました。
仕事から帰ってからや休日などの時間でSpringbootのアプリをGKE上に置いて公開しました。

## 何を作ったか？
- GKE上にSpringbootのDockerコンテナをデプロイ
  - テンプレートを修正してView作成
  - Cloud SQLを使用し、JPAでデータ読み込み
  - Springbootでデータを修正してフロントに表示
- GCE上にデータを追加するバッチを作成
  - プロフィールのデータをpropertiesファイルから読み込んで追加
  - ブログのデータをjsonから読み込んで追加
  - bodyのhtmlを取得してブログデータとして追加

## GCPでのアプリのデプロイ、各種設定
行ったことは以下です。

1. DockerイメージをContainer Registryに登録
1. Cloud SQLにデータベース作成
1. GKEで登録したDockerイメージを選択してデプロイ

DockerイメージをContainer Registryに登録する方法は、
以下の手順を参考に行えます。

他のDockerのRegistryに登録する方法と同じかと思います。

リポジトリにログインして、Dockerイメージにタグを付けてpushすれば登録できます。
登録するタグは、このように付ければできます。

    docker tag [SOURCE_IMAGE] [HOSTNAME]/[PROJECT-ID]/[IMAGE]
    docker push [HOSTNAME]/[PROJECT-ID]/[IMAGE]

[Docker Registryでのpushとpull](https://cloud.google.com/container-registry/docs/pushing-and-pulling?hl=ja)


Cloud SQLの登録についてもドキュメントがあり、
使用したいDatabaseを選択できます。自分はMySQL5.7を選択しました。

[Cloud SQLでのインスタンス立ち上げ](https://cloud.google.com/sql/docs/mysql/quickstart?hl=ja)


GKEのデプロイも選択していけば、簡単に登録は出来るのですが、
SQLとの接続で注意する部分がありました。
- GKEでクラスタを作る時に、GCEのインスタンスが立ち上がりSQLへの接続権限を付与する
- Role設定をしてSQLへの権限を設定する
- SQLの権限をsecretで登録する

[GKEからCloud SQLへの接続](https://cloud.google.com/sql/docs/mysql/connect-kubernetes-engine?hl=ja)

## 今後の課題
今回、簡単にアプリを作ってGCP上にデプロイしてみましたが、
以下は今後の課題としてやっていこうかと思います。
- https化と構成の変更
- 投稿部分の作成
- コンテンツの拡充

## 最後に
簡単な参照のみのアプリですが作成し、デプロイまでの一連の流れを確認できました。
分からない部分に関しても公式のドキュメントが充実していて非常に有り難かったです。
今回はサイト自体作りましたが、中身も充実出来るようにしていこうと思います。