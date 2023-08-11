# 安全なWebアプリケーションの作り方

## 1. Webアプリケーションの脆弱性とは
- セキュリティバグとセキュリティ機能は異なる
- セキュリティガイドライン
  - [安全なウェブサイトの作り方](https://www.ipa.go.jp/security/vuln/websecurity/about.html)
  - OWASP Top 10

## 2. 実習環境のセットアップ
- 環境
  - Linux(Debian 9)
  - nginx 1.10
  - Apache 2.4
  - PHP 5.3 / PHP 7.0
  - Tomcat 8.5
  - MariaDB 10.1
  - Postfix 3.1

Dockerを用いて環境を作成していく。
[このページ](https://wasbook.org/wasbook-docker.html)を参考にした。
`docker compose up -d`で起動できたら`127.0.0.1:13128`にアクセスすることで各章で検証するページを確認できる。

### OWASP ZAPインストール
- Webアプリケーション脆弱性診断用ツール
- MAC上でプロキシとして動作する
- [ダウンロードサイト](https://www.zaproxy.org/download/)でダウンロード
- Manual Exploreでブラウザを起動を選択し、対象となるURLを入力しサイトに遷移する

## 3. Wevセキュリティの基礎