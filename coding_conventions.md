# コーディング規約

## 命名規則
| 項目| 規則 | 具体例 |
| ---- | ---- |---|
| ディレクトリ名 | スネークケース | hoge_page |
| ファイル名 | スネークケース | home_page.dart |
| クラス名 | アッパーキャメルケース | class HomePage |
| 変数名 | キャメルケース | var userName |
| 定数名 | キャメルケース | final userName |

## 画面、コンポーネント
| 項目| 名命令 | 説明 |
| ---- | ---- |---|
| 画面 | ArticlePage<br> ArticleScreen<br>ArticlesPage<br> ArticlesScreen<br>ArticleListPage<br> ArticleListScreen | 名詞 + Page 名詞 + Screenで構成する<br>一目見てどの画面かわかる名前<br>suffixに画面を示す単語を命名 |
| コンポーネント | ArticleTile<br> ArticleCard<br> ArticleListView | 名詞 + Widgetの種類名 例えばCardをカプセル化した場合、ArticleCardと命名する<br>注意として、ArticleWidgetのようなsuffixにWidgetを付けるのは避ける<br>何のWidgetで構成されているのか分からないため |

## データクラス
| 項目 | 命名例 | 説明 |
|---|---|---|
| 記事 | Article<br> LatestArticle PrivateArticle|名詞 形容詞 + 名詞 名詞 + 名詞 クラス内のプロパティを<br>持つ者として相応しい名前を命名する|

## データソースを扱う層
| 項目 | 命名例 | 説明 |
|---|---|---|
| APIクライアント | GitHubClient　| 名詞 + Clientで構成 |　
| データソース先をカプセル化したクラス | ArticleRepository<br> ArticleDataSource | 名詞 + Repository<br> 名詞 + DataSourceで構成 |

## ビジネスロジック
### １クラス = １ロジックを担うクラス<br>
動詞 + 名詞の構成でクラス名を命名

| 項目 | 命名例 |
|---|---|
| 記事を作成する | CreateArticl UploadArticle SaveArticle|
| 記事を取得する | FetchArticle GetArticle|
| 記事を更新する | UpdateArticle|
| 記事を削除する | DeleteArticle RemoveArticle|

関数名はcallを使う<br>
※callを定義すると、そのクラスオブジェクトは関数として扱われ、1クラス = 1ロジックの粒度として扱いやすくなる<br>
※関数として扱われるので、callを省略して利用できる

### １状態 = 1管理者（操作関数を持つクラス）

名詞 + 名詞の構成でクラス名を命名

| 項目 | 命名例 | 説明 |
|---|---|---|
| 記事の状態管理 + CRUD操作を提供する | ArticleController | 名詞 + Controllerで構成する<br>FlutterではxxxControllerで命名されたものが多い|

関数は 動詞 + 名詞の構成で命名

| 項目 | 命名例 |
|---|---|
| 記事を作成する | createArticle uploadArticle saveArticle |

## boolean
is + 形容詞 has + 過去分詞 三単現動詞 + 名詞 助動詞 + 動詞 で構成し、YES or Noで判断できるよう命名

| 項目 | 命名例	| 説明 |
|---|---|---|
| 読み込み状態	isLoading |	is + 形容詞|
| 有効状態	| isEnabled |	is + 形容詞|
| 表示状態	| isVisible |	is + 形容詞|
| 保持状態	| hasArticled |	has + 過去分詞|
| 存在有無	| existsArticle |	三単現動詞 + 名詞|
| 可否状態	| canUpload |	助動詞 + 動詞|

### その他
|項目	|命名例	|由来|
|---|---|---|
|拡張関数|	StringExtension<br> StringExt|	拡張元 + Extension<br> 拡張元 + Extで構成<br>suffixは拡張関数を示す単語で構成|
|変換クラス| TimestampDateConverter | 名詞 + Converterで構成<br> どのような状態を変換できるのかわかるよう命名|
| ストリームクラス |	ArticleStream |	名詞 + Streamで構成<br>購読すると、どのような状態がストリーム経由で得られるのかわかるよう命名|
| 便利クラス | Validation<br> ValidationUtil<br> ValidationHelper | 名詞のみで完結<br>xxxUtil xxxHelperの命名は最終手段。
| Exceptionクラス | GitHubException	| 名詞 + Exceptionで構成<br>Exceptionの発生元から具体的な名前を命名|

抽象化を採用する場合、抽象クラスを実装したクラス名のsuffixにImpl（Implementationの略称）を付ける<br>Repositoryの場合はその実装部としてDataSourceでも可

| 抽象クラス例 | 実装クラス例 |
|---|---|
|ArticleRepository | ArticleRepositoryImpl<br> ArticleDataSource|
|CreateArticle | CreateArticleImpl|
