Springbootにおいて、Spring Data JPAはJPA(Java Persistence API)を
repositoriesに基づいた実装を容易にしてくれるモジュールです。

Entityを定義してRepositoryをinterfaceで定義すれば、
基本的な実装を省略してデータの入出力を行えます。

また、@Queryでqueryを定義すれば、任意のクエリ作成も行えるので、
柔軟なデータ取得が可能になります。

その中で、実装時にハマった以下の部分について書いていこうと思います。
- 指定のデータのUpdateをする方法
- OneToMany, ManyToOne, ManyToMany


[GenerationTypeの種類について](https://qiita.com/KevinFQ/items/a6d92ec7b32911e50ffe)

[FetchTypeについて](http://itdoc.hitachi.co.jp/manuals/link/cosmi_v0870/APR4/EU260088.HTM)

FetchType.EAGERとFetchType.LAZYは何なのか
EAGER（日本語での意味は「熱心な」）はデータベースからエンティティの情報を読み込む時に、
関連のフィールドやエンティティも含めてロードする。
熱心に関連情報まで集めてくれるといった感じでしょうか。

一方で、LAZY（日本語での意味は「怠惰な」）は個別にフィールドや関連先に初めてアクセスする。
呼びに行くまで起きない怠惰な設定といった感じだと思います。

関連するフィールドが多くなったり、依存関係が複雑な場合はLAZYにしておいた方が無駄な呼び出しは済まさずに済む一方で、
シンプルなデータスキーマを設計している場合はEAGERで先読みしている方が、効率的に読み込むことが出来るかと思います。

