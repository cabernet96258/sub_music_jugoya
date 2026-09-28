# Google Apps Script（GAS）で公開する手順

学校のネットワークで `github.io` がブロックされている場合の代わりの公開方法です。
Google Workspace for Education を使っている学校なら、`script.google.com` はたいてい開けます。

## 手順

1. 先生の学校アカウントで <https://script.google.com/> を開き、「新しいプロジェクト」を作ります。
2. プロジェクト名を「じゅうごやさんのもちつき」などに変えます。
3. 左の「ファイル」の ＋ →「HTML」で、`index` という名前のファイルを作ります（拡張子の `.html` は自動で付きます）。
4. このリポジトリの `index.html` の中身を**すべて**コピーし、作った `index.html` に貼り付けて上書きします。
5. 最初からある `コード.gs`（`Code.gs`）の中身を、次のコードに置き換えます。

   ```javascript
   function doGet() {
     return HtmlService.createHtmlOutputFromFile('index')
       .setTitle('十五夜さんのもちつき リズムづくり')
       .addMetaTag('viewport', 'width=device-width, initial-scale=1');
   }
   ```

6. 右上の「デプロイ」→「新しいデプロイ」を押し、種類で「ウェブアプリ」を選びます。
   - 次のユーザーとして実行：**自分**
   - アクセスできるユーザー：**（学校のドメイン）内の全員**
7. 「デプロイ」を押すと、`https://script.google.com/macros/s/…/exec` の形の URL が出ます。この URL を児童に配布します。

## index.html を更新したとき

手順 4 と同じように貼り直してから、「デプロイ」→「デプロイを管理」→ 鉛筆アイコン →「バージョン：新バージョン」→「デプロイ」を押します。URL は変わりません。

## 注意

GAS の Web アプリは、`googleusercontent.com` の枠（iframe）の中で表示されます。
管理コンソールで「サードパーティ Cookie をブロック」が強く設定されていると、作品の自動保存が効かないことがあります。その場合も、アプリそのものは動きます（ページを閉じると作品は消えます）。
保存が効くかどうかは、カードを置いてからページを再読み込みして確かめてください。
