# 公式サイトのドキュメント

Hinodeテーマを用いた編集方法のドキュメントは、以下のサイトをご覧ください。

* [Hinodeテーマドキュメント](https://gethinode.com/docs/)
  
このサイトの見方について下記のとおりご紹介します。

Getting Started
    : HugoとHinodeのインストール方法、初期設定などが記載されています。WEBサイト編集には必要のない章です。

Content
    : Markdown
        : 記事を作成するための文書フォーマットの基本である、 **Markdown** 記法について示されています。Markdownにはさまざまな方言がありますので、こちらをご一読ください。

    : Contents Management
        : ページ単位でのコンテンツの構成方法について説明されています。Markdown記法によるドキュメントだけではなく、Hugoオリジナル機能を使ったマクロ記述や、ページヘッダの記載方法について説明されています。
    
    : Content Organization
        : 全体のページ配置方法について説明されています。特に重要な項目はサブフォルダへアクセスする際に参照するデフォルトページが `_index.md` というファイルである点です。

    : Links and Cross-References
        : リンクや相互参照の方法について説明されています。

    : Images and Figures
        : 図（image）やキャプション付き図（figure）の掲載方法についての説明です。
    
    : Tables
        : 表の作り方についての説明です。非常に長大な表の場合はページネーションや、任意の列で並び替えが可能な[simple-datatable プラグイン](https://gethinode.com/docs/components/table/)についての紹介もあります。スタート時刻順やチーム別、ナンバーカード順などさまざまな並び替えができるのが便利です。

    : Icons
        : あらかじめ登録されたアイコンを文中に埋め込むことができます。この使い方の説明がされています。

Configuration
    : 全体のレイアウト、メニューナビゲーション、モジュール、Google analytics連携など、システム設定にかかわる項目です。通常ページ編集には使わない項目ですが、どうしてもこの機能の変更を必要とする場合は管理者にお問い合わせください。

Blocks
    : Hinodeには、Hugoから独立した独自のコンテンツレイアウト機能である、[Bookshop](https://github.com/CloudCannon/bookshop)が組み込まれています。これは任意の場所にコンテンツを配置する部品ではなくレイアウトや描画機能も含めて半自動で提供してくれるページフレームワークです。したがってユーザが独自の配置を決める自由度はありません。半面、大規模な機能ページである、ブログ、FAQ、スタッフ紹介ページ、CTAなどを簡単に構築可能です。Markdown文書や次項目のComponentsと合わせて使用することは少々難しいので、まずはここにある機能を一覧いただき、必要なものがあればページには一切記述せず、フレームワークに従ったページ提供を行うのが良いでしょう。

    : wmoc2027公式ページでは、[スケジュール](https://wmoc2027.jp/get_started/schedule/)ページに[Releases](https://gethinode.com/docs/blocks/releases/)ブロック、[トップページ](https://wmoc2027.jp/)に掲載している活動報告（Our activities）に現れるブログページに[Article](https://gethinode.com/docs/blocks/articles/)ブロックなどを活用しています。

Components
    : Componentsは、Markdown文中にも挿入可能で、任意の場所に配置が可能な様々なレイアウト部品を提供しています。


Advanced Settings
    : より進んだ使い方についての説明です。Font awesomeが提供する無償アイコンは [icons](https://gethinode.com/docs/advanced-settings/icons/) で紹介されていて気軽に使えますので、お読みいただくとよいでしょう。
