キーワード駆動っぽいテストができるツールを開発した話
===
2022-11-02 [@eyasuyuki](https://twitter.com/eyasuyuki)

<!-- paginate: true -->

---

# 今回開発したツール

[https://github.com/eyasuyuki/keydriver](https://github.com/eyasuyuki/keydriver)

---

# キーワード駆動テストとは

- システムテストの技法の一つ
- アクションキーワードとデータからなる表を使ってテストする
- キーワード表を読み込んでSeleniumなどを動かすトライバーを作れば自動化できる

---

# キーワード駆動テストの例

| No | キーワード | 対象 | 引数 | 備考 |
-----|----------|--------|--------|-------
| 1  | open     |url[https://www.google.com] | | URLをブラウズする |
| 2  | input    | テキストボックス | サルゲッチュ | テキストボックスへの入力 |
| 3  | click    | ボタン[Google 検索] | | ボタンをクリックする |
| 4  | assert   | タイトル | is[サルゲッチュ - Google 検索] | 検索結果ページのタイトル検証 |


---

# キーワード駆動テストのメリット

- 操作を示すキーワードと、その対象となるデータが1つの表で表現できる
- 画面が変更されてもドライバーをメンテナンスするだけで済む
- 発表者が考えるメリット:
  - システムテストの表記方法が統一できる
  - テストデータが各所に分散するのを防止できる

---

# キーワード駆動テストのデメリット

- ドライバーを書くのが大変
- ドライバーのメンテナンスが大変

---

# デメリットを頓知で解決する

- ドライバーを書くのが面倒なら、キーワード表を拡張して画面依存の情報も含めたらどうか?

---

# 拡張したキーワード表

| No | キーワード | 対象 | 引数 | 備考 | **拡張1** | **拡張2** |
-----|----------|--------|--------|------|----------|-----------
| 1  | open     |url[https://www.google.com] | | URLをブラウズする | | |
| 2  | input    | テキストボックス | サルゲッチュ | テキストボックスへの入力 | **name[q]** | |
| 3  | click    | ボタン[Google 検索] | | ボタンをクリックする | **name[btnK]** | |
| 4  | assert   | タイトル | is[サルゲッチュ - Google 検索] | 検索結果ページのタイトル検証 | **xpath[/html/head/title]** | |

---

# 動作概念図

<div class="mermaid" style="font-size: 50%; text-align: center;">
sequenceDiagram
    Keydriver ->> POI: Excelファイル読み込み
    POI ->> Excel: 読み込み
    Excel ->> POI: ワークシート
    POI ->> Keydriver: ワークシート
    Keydriver ->> WebDriver: ブラウザ操作
    WebDriver ->> ブラウザ: ブラウザ操作
    ブラウザ ->> WebDriver: ブラウズ結果
    WebDriver ->> Keydriver: ブラウズ結果
    Keydriver ->> Keydriver: 結果検証
</div>
<script src="https://unpkg.com/mermaid@8.1.0/dist/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>

