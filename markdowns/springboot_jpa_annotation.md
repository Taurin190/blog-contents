Springbootにおいて、Spring Data JPAはJPA(Java Persistence API)を
repositoriesに基づいた実装を容易にしてくれるモジュールです。

Entityを定義してRepositoryをinterfaceで定義すれば、
基本的な実装を省略してデータの入出力を行えます。

また、@Queryでqueryを定義すれば、任意のクエリ作成も行えるので、
柔軟なデータ取得が可能になります。

その中で、実装時にハマった以下の部分について書いていこうと思います。
- 指定のデータのUpdateをする方法
- OneToMany, ManyToOne, ManyToMany