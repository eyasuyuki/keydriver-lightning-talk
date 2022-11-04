キーワード駆動っぽいテストができるツールを開発した話
===
2022-11-02 [@eyasuyuki](https://twitter.com/eyasuyuki)

<!-- paginate: true -->~~

---

# 結論

- キーワード駆動テストの欠点は⭕️⭕️で解決できる


---

# 今回開発したツール

## Keydriver
  [https://github.com/eyasuyuki/keydriver](https://github.com/eyasuyuki/keydriver)
  
- ノーコードでe2eテストができる
- オープンソース
- 商用利用可(MITライセンス)
- 気に入ったら☆(Star)ください🙇

### Zennの記事

[https://zenn.dev/eyasuyuki/articles/a20301d34adce0](https://zenn.dev/eyasuyuki/articles/a20301d34adce0)

---

# キーワード駆動テストとは

- システムテストの技法の一つ
- アクションキーワードとデータからなる表を使ってテストする
- キーワード表を読み込んでSeleniumなどを動かすトライバーを作れば自動化できる

---

# キーワード駆動テストとは

- システムテストの技法の一つ
- アクションキーワードとデータからなる表を使ってテストする
- キーワード表を読み込んでSeleniumなどを動かすトライバーを作れば自動化できる
- ......などとされているが**実践している人を誰も見たことがない幻のテスト技法**である

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
  - システムテストの記述を標準化できる
  - テストデータが各所に分散するのを防止できる

---

# キーワード駆動テストのデメリット

- ドライバーを書くのが大変
- ドライバーのメンテナンスが大変

これらの欠点により幻のテスト技法となってしまったのではなかろうか。

## ではどうするか?

---

# デメリットを⭕️⭕️で解決する

---

# デメリットを頓知で解決する

---

# デメリットを頓知で解決する

- ドライバーを書くのが面倒なら、**キーワード表を拡張して画面依存の情報も含める**のはどうか?

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
    Keydriver ->> POI: テスト結果出力
    POI ->> Excel: テスト結果出力
</div>
<script src="https://unpkg.com/mermaid@8.14.0/dist/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>

---

# 実際のExcel表の例

![Google検索.xlsx](https://raw.githubusercontent.com/eyasuyuki/keydriver-lightning-talk/master/images/excel_worksheet.png)

---

# デモ

[https://youtu.be/Klqx18-cBgw](https://youtu.be/Klqx18-cBgw)

---

# 参考文献(1/2)

- ソフトウエア品質を高める開発者テスト改訂版 (高橋寿一 2022)
  - ISBN978-4-7981-7639-0

![width:500px](https://raw.githubusercontent.com/eyasuyuki/keydriver-lightning-talk/master/images/takahashi22.jpg)


---

# 参考文献(2/2)

- システムテスト自動化標準ガイド (Mark Fewster, Dorothy Graham 1999)
  - ISBN978-4-7981-3921-0

![width:500px](https://raw.githubusercontent.com/eyasuyuki/keydriver-lightning-talk/master/images/fewster99.jpg)
