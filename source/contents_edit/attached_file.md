# 添付ファイルと図

イメージファイルの埋め込みとファイルダウンロードでは、ファイルの置き場所とページへの表記方法が異なります。次の表をご参照ください。

イメージファイル
    : ページ上にマークアップ記法を記述することで、配置したファイルへの画像を埋め込み表示します。
    : ファイルの置き場所
        : /assets
    : 参照方法
        : /につづいてassetsディレクトリ以下のサブディレクトリパスを記述。/assetsをルートとしたパスで画像ファイルへの参照が可能です。
    : 記述例
        : ファイルパス
            : /assets/posts/20260612/IMG_4335.JPEG
            : /assets/posts/20260612/IMG_4313.JPEG
        : 記述
            : ``` markdown
              ---
              title: IOFよりデービッド・ローチ氏が訪問されました
              author: 村越 真
              date: 2026-06-12
              thumbnail: 
                  url: /posts/20260612/IMG_4335.JPG
                  author: Shin Murakoshi SEAのデービッド・ローチ氏：後ろ左から二人目と実行委員会のコアメンバー
              ---
              　:
              ![](/posts/20260612/IMG_4313.JPEG "香美町にて。地元ではオリエンテーリング競技開催を告知するディスプレーも設置されています。")
              ```
        : 表示
            : [こちらのサイトの写真](https://wmoc2027.jp/ja/posts/20260612/)
        
添付ファイル
    : ページ上に配置したファイルへのダウンロードリンクを作成し、ブラウザ上からクリックするとファイルをダウンロードできます。
    : ファイルの置き場所
        : /static
    : 参照方法
        : /につづいてstaticディレクトリ以下のサブディレクトリパスを記述。/staticをルートとしたパスで画像ファイルへの参照が可能です。
    : 記述例
        : ファイルパス
            : /static/bulletins/Bulletin1.pdf
            : /static/bulletins/Bulletin1_2.pdf
            : /static/bulletins/WMOC2027_oldmap.pdf
        : 記述
            : ``` markdown
              {{< accordion id="accordion-default" >}}
                {{< accordion-item title="Bulletins" show="true" >}}
                |Contents| Release date |
                |--|--|
                |[Bulletin 1 Rev. 1](bulletins/Bulletin1.pdf)|2 Feb 2026|
                |[Bulletin 1 Rev. 2](bulletins/Bulletin1_2.pdf)|26 Feb 2026| 
                |[Old map](bulletins/WMOC2027_oldmap.pdf)|2 Feb 2026|
                {{< /accordion-item >}}
                  :
              {{< /accordion >}}
              ```
        : 表示
            : [このサイトの折り畳みアコーディオンのBulletins項内の記述](https://wmoc2027.jp/competitions/bulletins/)