# cocoaer

## サービス概要
孝行をもっと身近に。  
孝行に特化したSNSです。

## ユーザーが抱える課題
- 孝行をしたいがきっかけがない。
- 孝行をしたいが何をすればいいかわからない。

## 課題に対する仮説
- 孝行をしたいがきっかけがない。
　　　　- 孝行することに対して費やすコスト（金銭・時間）がない・想像がつかない
  - 改めて孝行することの照れ臭さ
- 孝行をしたいが何をすればいいかわからない。
  - 孝行の具体的なやり方・事例を知らない。

## 解決方法
- アプリを利用してもらい、「アプリに投稿するから」という口実（きっかけ）を提供する。
- 行った孝行を投稿してもらうことで、孝行についてのデータベースとなる。
  - かかったコストも書いてもらうことで、目安にできる（記載は任意）
- フォーラム機能でトピックを立てて質問することができる。 
   - 孝行を受ける側からの意見も聞くことができるかも。

## メインのターゲットユーザー
20~40代
自分のライフステージの変化、親の定年・還暦・銀婚式といったイベントのタイミングで孝行したいと思っている人

## 実装予定の機能
- 非ログインユーザー
  - 孝行
    - 投稿された孝行 
      - 一覧/詳細
        - 閲覧
      - コメント
        - 閲覧
  - フォーラム
    - 一覧の閲覧
- ログインユーザー
  - 孝行
    - 投稿された孝行
      - 一覧/詳細
        - 閲覧
        - 検索
      - コメント
        - 閲覧/投稿
      - ブックマーク機能
    - 新規投稿/編集
  - フォーラム 
    - 一覧/詳細
      - 閲覧
      - 検索
    - 作成
    - コメント
      - 閲覧/投稿 
    - ブックマーク機能

## なぜこのサービスを作りたいのか？
いざ親孝行しようとした際に、何をすればいいのかわからなかった経験がある。
調べてもランキングや広告のサイトが多く、具体的にどういうものが良いのわからなかった。
その時にさまざまな選択肢があればと感じ、孝行を投稿するSNSがあればいいと思ったから。

■スケジュール

企画〜技術調査：5/1〆切  
README〜ER図作成：5/1 〆切  
メイン機能実装：5/1 - 5/15  
β版をRUNTEQ内リリース（MVP）：5/20〆切  
本番リリース：6月  

■技術選定
- Rails7
- postgresql
- その他未定
