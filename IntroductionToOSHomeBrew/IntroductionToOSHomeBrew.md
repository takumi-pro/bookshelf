# はじめてのOS自作入門

## 学びたいこと

- OSの基本的な機能
- OSがどのように実装されているのか

### 第11章

[タイマ割り込み](https://www.wdic.org/w/TECH/%E3%82%BF%E3%82%A4%E3%83%9E%E3%83%BC%E5%89%B2%E3%82%8A%E8%BE%BC%E3%81%BF#:~:text=UNIX-,%E6%A6%82%E8%A6%81,%E3%81%AB%E8%A1%8C%E3%81%AA%E3%81%86%E3%81%93%E3%81%A8%E3%81%8C%E3%81%A7%E3%81%8D%E3%82%8B%E3%80%82)によって一定時間ごとに割り込みを発生させることでマルチタスクにも対応できる。本書ではLocalAPICタイマを使用している。

[LocalAPIC](https://ja.wikipedia.org/wiki/APIC)はCPU内部に実装されている割り込みコントコーラ。

`優先度付きキュー`

要素の優先度に従った順に取り出されるキューのこと。


`ACPI（Advanced Configuration and Power Interface）`

コンピュータの構成や電源を管理するための規格。ACPI PM（Power Management）タイマを使用してLocalAPICタイマの周期を計測する。

ACPI PMタイマを使用するには以下が必要
- FADT
- XSDT
- RSDP

FADTの場所を知るにはXSDTが必要で、XSDTの場所を知るにはRSDPを取得する必要がある。
RSDPの場所はUEFI BIOSが知っているためブートローダ側で取得処理を記述する。カーネル側はRSDP構造体を受け取る引数をメイン関数に追加する。

RSDP構造体
```cpp
struct RSDP {
  char signature[8];
  uint8_t chechsum;
  char oem_id[6]
  uint8_t revision;
  uint32_t rsdt_address;
  uint32_t lenght;
  uint64_t xsdt_address;
  uint8_t extended_checksum;
  char reserved[3];

  bool IsValid() const;
} __attribute__((packed));
```

欲しい情報は`xsdt_address`

## 第12章 キー入力
前章でRSDTを取得したため本章の始まりはXSDTの取得から

キー入力はUSBキーボードを対象とする。マウスと同じくHIDクラスの機器

キーの判別は各キーに割り当てられた数値で行う。その数値をASCIIに変換するキーコードマップを作成して文字に変換する。

Shiftキーの押下状態も受け取ってキーコードマップに反映する（新しいキーコードマップ）。

HID規格ではマウスやキーボードは区別されない。情報はレポートディスクリプタに記載して送受信する。


# 参考資料
- [江添亮のC++入門](https://ezoeryou.github.io/cpp-intro/)