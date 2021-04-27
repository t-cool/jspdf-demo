# jsPDF Demo

[jsPDF](https://github.com/MrRio/jsPDF) を利用して、フロントエンドで PDF を生成するデモ。

## フォントの準備

UTF-8 のフォントを読み込むために、ttf ファイルを Base64に変換して読み込む必要があります。[https://rawgit.com/MrRio/jsPDF/master/fontconverter/fontconverter.html](https://rawgit.com/MrRio/jsPDF/master/fontconverter/fontconverter.html) で ttf ファイルからBase64に変換できます。詳細は [https://artskydj.github.io/jsPDF/docs](https://artskydj.github.io/jsPDF/docs) を参照してください。


## 使い方

```js
// コンストラクタで doc という名前で document を作成する    
var doc = new jsPDF();

// フォントの設定
// この箇所とは別に、予めフォントデータ(font.js)を読み込んでおく
doc.addFileToVFS("./libs/KosugiMaru-Regular.ttf", KosugiMaruRegular);
doc.addFont('./libs/KosugiMaru-Regular.ttf', 'KosugiMaru', 'normal');
doc.setFont('KosugiMaru', 'normal');    
doc.setFontSize(15);

// PDF の生成
// PDF にテキストを埋め込む: doc.text(表示する文字列, x座標, y座標)
// 生成した PDF をブラウザで表示する: doc.output("dataurlnewwindow");
// 生成した PDF をダウンロードする: doc.save("result.pdf");
function generate() {
    doc.text("No.", 10, 10);
    doc.text("英語", 30, 10);
    doc.text("発音", 70, 10);
    doc.text("日本語", 120, 10);

    var result = [["dog", "ドグ", "イヌ"],
                  ["cat", "キャット", "ネコ"],
                  ["elephant", "エレファント", "ゾウ"]];

    for(var i = 0, len = result.length; i < len; i++){
        doc.text((i+1).toString(), 10, 20 * (i+1));
        doc.text(result[i][0], 30, 20 * (i+1));
        doc.text(result[i][1], 70, 20 * (i+1));
        doc.text(result[i][2], 120, 20 * (i+1));
    }
    doc.output("dataurlnewwindow");              
    doc.save("result.pdf");
}
```

## ライセンス

MIT
