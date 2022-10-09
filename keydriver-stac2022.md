幻のテスト技法「キーワード駆動テスト」を追い求めて
====

2022-12-03 [@eyasuyuki](https://twitter.com/eyasuyuki)

<!-- paginate: true -->

---

# 結論

- キーワード駆動テストは、


---

# 結論

- キーワード駆動テストは、意外に簡単だった

---

# そもそもキーワード駆動テストとは

![width:500px](./images/keyword-driven-example.png)


- 操作を表すアクションキーワードと、その対象となるデータで構成された表を使って行うテスト
- 人間可読のキーワード表と実際の画面を結びつけるドライバーを**書けば**自動化できる

---

# キーワード駆動テストが登場する本その1

- システムテスト自動化標準ガイド (Mark Fewster, Dorothy Graham 1999)
    - ISBN978-4-7981-3921-0

![width:500px](https://raw.githubusercontent.com/eyasuyuki/keydriver-lightning-talk/master/images/fewster99.jpg)

- 概念的なエピソードは書かれているが、具体的なアーキテクチャについては書かれていない

---

# キーワード駆動テストが登場する本その2

- ソフトウエア品質を高める開発者テスト改訂版 (高橋寿一 2022)
    - ISBN978-4-7981-7639-0

![width:500px](https://raw.githubusercontent.com/eyasuyuki/keydriver-lightning-talk/master/images/takahashi22.jpg)

- この本でキーワード駆動テストを知った。ただし概要だけしか書かれていない

---

# キーワード駆動テストを知った頃のツイート

![width:500px](https://raw.githubusercontent.com/eyasuyuki/keydriver-lightning-talk/master/images/eyasuyuki-tweet.png)

[https://twitter.com/eyasuyuki/status/1562708740243337216](https://twitter.com/eyasuyuki/status/1562708740243337216)

---

# 既存のキーワード駆動テストツールその1

## Open2Test

[https://github.com/open2test/Open2Test_Selenium](https://github.com/open2test/Open2Test_Selenium)

### 目的に合わなかった理由

- キーワード表の形式が気に入らない(納品物にならない)
- ソースコードがないので自由に改造できない
- 余計な機能がある(データの読み込みなど)

---

# 既存のキーワード駆動テストツールその2

## Robot framework

[https://robotframework.org](https://robotframework.org)

### 目的に合わなかった理由

- キーワード表の形式が気に入らない(納品物にならない)

---

# あるアイデアがひらめいた💡




