# はじめてのOS自作入門

## 学びたいこと

- OSの基本的な機能
- OSがどのように実装されているのか

### 第11章

[タイマ割り込み](https://www.wdic.org/w/TECH/%E3%82%BF%E3%82%A4%E3%83%9E%E3%83%BC%E5%89%B2%E3%82%8A%E8%BE%BC%E3%81%BF#:~:text=UNIX-,%E6%A6%82%E8%A6%81,%E3%81%AB%E8%A1%8C%E3%81%AA%E3%81%86%E3%81%93%E3%81%A8%E3%81%8C%E3%81%A7%E3%81%8D%E3%82%8B%E3%80%82)によって一定時間ごとに割り込みを発生させることでマルチタスクにも対応できる。本書ではLocalAPICタイマを使用している。

[LocalAPIC](https://ja.wikipedia.org/wiki/APIC)はCPU内部に実装されている割り込みコントコーラ。

`優先度付きキュー`

要素の優先度に従った順に取り出されるキューのこと。


# 参考資料
- [江添亮のC++入門](https://ezoeryou.github.io/cpp-intro/)