### サービス概要
Ruby on Railsで作られた個人開発アプリを投稿、検索できる他、Railsに関する情報を収集できるサービス兼ファンサイトです。
Railsで作られた個人開発アプリ、Railsに関するXのポスト、Railsの技術記事、Railsに関する動画、Railsで作られたサービス/採用されている企業などの情報を集約して検索できるようにすることで、Railsユーザーの最新の動向を確認したり、Railsに関する情報を収集できるようになります。
ユーザー登録することで、Railsで作られた個人開発アプリを投稿したり、他のRailsユーザーの方と繋がったり、投稿されたアプリや他のサービスの記事などをお気に入り登録できます。

### このサービスへの思い・作りたい理由
プログラミングスクールのRailsのカリキュラムとRailsチュートリアルで学習し、はじめてRailsで個人開発のアプリを作った時に、開発するのがとても楽しく、みんなに使ってもらえたことに感動し、心に残っています。
自分は過去に何度か他の言語やフレームワーク学んだものの、アプリを作り切ることができずに挫折してしまいましたが、Railsでは作り切ることができたので、この楽しさや感動を多くの方に知ってもらいたいと思い、Railsの魅力を伝える本サービスを作りたいと考えました。

### ユーザー層について
主にRails初学者に向けたサービスです。
Rails初学者の方が、Railsで実際にどういうアプリが作られているのか、どう言ったサービスで使われているのかを知ることができ、加えて、Railsユーザーの最新の動向を確認したり、Railsに関する情報を収集したりできることによって、安心してRailsを学んでほしいと考えています。
さらに、Railsでアプリを作った方は、自身が作成したアプリを投稿することで、多くの人にアプリや自身のことを知ってもらえるような場になると思います。

### サービスの利用イメージ
Railsユーザーが開発した個人開発アプリや、その他Railsに関する様々な情報を参照できることで、Railsを学習することへのモチベーションを向上させたり、Railsに関する知見を深めることができます。
また、個人開発アプリを投稿することで、アプリがたくさんの人の目に触れられるようになり、他のユーザと繋がる機会になると考えています。

### ユーザーの獲得について
まずは、プログラミングスクールで受講されている方や、個人でRailsチュートリアルなどで学習されている方、その他の駆け出しエンジニアの方に向けて、X（Twitter）などでハッシュタグなどを使って情報を拡散することで、興味を持ってもらえるのではないかと考えています。

### サービスの差別化ポイント・推しポイント
Railsに特化して、Railsで作られたアプリを投稿するサービスやサイトはないと思いますので、Rails初学者の方や、Railsのファンの方の目に注目して楽しんでもらえると考えています。
また、XやQiitaなどの個々のサービスごとにRailsの情報収集することは可能ですが、本サービスではRailsという観点に特化してそれらを集約して管理できるようにすることで、単なるアプリ投稿サイトにとどまらず、Railsの情報が満載のファンサイトとして機能すると考えています。
さらに、ユーザー登録機能をつけてアプリが投稿できたり、フォローできたり、お気に入り登録できるようにすることで、ユーザー同士の交流が生まれるという点も、他のRailsのニュースサイトやサービスとの差別化ポイントです。
これによって、RailsガイドやRailsチュートリアルといった、Railsの主要コンテンツのように、Railsのユーザーであれば知っているコンテンツの一つとして認知されるようにできるのではないかと考えています。

### 機能候補
＜MVPリリース向け＞
・ユーザ登録/編集機能、ログイン機能
・Railsで作られた個人開発アプリを投稿、検索できる機能
・Railsに関する直近で話題のポスト(X:旧Twitter)を表示する機能
・Railsの技術記事(Qiita, Zenn)を検索できる機能
・Railsに関する動画(YouTube)を検索できる機能

＜本リリース向け＞
・Railsで作られたサービス/採用されている企業を参照できる機能
・ユーザ情報編集機能（SNSアカウントの情報を登録できるようにする）
・お気に入り機能（アプリ、サービス、技術記事、動画などをお気に入りし、マイページで一覧化できるようにする）
・フォロー機能
・技術記事(Qiita, Zenn)の最新情報を定期実行で取得し、DBに登録する機能

### 機能の実装方針予定
＜MVPリリース向け＞
・ユーザ登録/編集機能、ログイン機能
Sorceryを使用し、通常のパスワード認証の他、Google認証またはGitHub認証を実装予定です。

・Railsで作られた個人開発アプリを投稿、検索できる機能
基本的なCRUDで実装予定です。
投稿する際、WappalyzerというサービスのAPIを使用して、入力されたアプリのURLからRailsが使用されているかを判定する処理を行い、Railsが使用されていないアプリが登録されることを防ぎます。
この方法だと、バックエンドのみRailsをAPIモードで使用しているアプリは、Railsを使っていると判定することができないので、現時点では、投稿できるのはフロントバック共にRailsで開発されているアプリに限る想定です。

・Railsに関する直近で話題のポスト(X:旧Twitter)を表示する機能
XのAPIを利用する予定です。

・Railsの技術記事(Qiita, Zenn)を検索できる機能
マルチ検索・オートコンプリートを実装予定です。Qiita/ZennのAPIを利用予定です。QiitaやZennのタグで検索できるようにしたいと考えています。

・Railsに関する動画(YouTube)を検索できる機能
手動でDBに登録して表示させる想定です。YouTubeに頻繁にRails関連の情報があがるわけではないので、一旦は自分が有用と思った動画をピックアップして手動で登録する想定です。

＜本リリース向け＞
・Railsで作られたサービス/採用されている企業を参照できる機能
技術スタックとしてRailsを使用していることを公表しているサービスや企業を、手動でDBに登録して表示させる想定です。頻繁に更新があるような情報ではなく、数もそこまでたくさん載せる想定ではないので、手動登録で良いと判断しました。「What we use」や「Top Ruby Companies」というサイトで採用している企業群は見れたりしますが、どこから情報を取ってくるかは検討中です。

・ユーザ情報編集機能（SNSアカウントの情報を登録できるようにする）
基本的なCRUDで実装予定です。

・お気に入り機能（アプリ、サービス、技術記事、動画などをお気に入りし、マイページで一覧化できるようにする）
基本的なCRUDで実装予定です。

・フォロー機能
基本的なCRUDで実装予定です。

・技術記事(Qiita, Zenn)の最新情報を定期実行で取得し、DBに登録する機能
cronまたはAWSのLambdaとEventbridgeなどを用いて、定期的に最新情報を取得してDBに保存する処理を実装したいと考えています。

### 画面遷移図
Figma: https://www.figma.com/design/GcOdJagozB8E5GgBt3P2gS/Rails%E3%82%8B%E3%83%BC%E3%82%80?node-id=0-1&t=zgHp1sywDJmz8c8u-1
