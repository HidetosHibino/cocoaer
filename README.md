# cocoaer

## サービス概要

孝行をもっと身近に、手軽に。  
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

- 非ログイン時

   - 投稿された孝行について、一覧/詳細を見ることができる。
     - コメントを見ることができる。
     
   - フォーラムについて、一覧を見ることができる。
   - プロジェクトについて、一覧を見ることができる。
   - パスワードリセット機能
   
- ログインユーザー  

  - <孝行>
    - 投稿された孝行について、一覧/詳細を見ることができる。
      - コメントについて閲覧/投稿できる
      - ブックマークすることができる
      
    - 投稿された孝行について、検索することができる。
        
    - 孝行を新規投稿/編集することができる  
  - <フォーラム>  
    - フォーラムについて、 一覧/詳細を見ることができる。
      - コメントについて閲覧/投稿できる
      - ブックマークすることができる
      
    - フォーラムについて、検索できる 

    - フォーラムを作成することができる
  
  - <プロジェクト機能> :孝行をプロジェクトライクで進めるための機能。- カテゴリ、期間や予算を設定して使う日記的なもの。
    - カテゴリ、期間や予算を設定する。
    - 行動を記録できる。  
    - カテゴリ（旅行・贈り物・etc...）や期間、予算で検索できる。

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

■　画面遷移図
https://www.figma.com/file/fsUtM0ocbfR2CHklVjkkZC/Untitled?node-id=0%3A1&t=rIkv44a6duu7mhQc-1

■　ER図
![ER図](/er.drawio.png)
[User]ユーザ情報マスタ
  - name: ユーザの名前
  - email: ユーザーのメールアドレス
  - avatar: アバター画像
  - crypted_password: ハッシュ化されたパスワード
  - salt: ハッシュ時のsalt
  - reset_password_token: パスワードリセット時のトークン
  - reset_password_token_expires_at: パスワードリセット時のトークン作成日時
  - reset_password_email_sent_at: パスワードリセットのメール送信日時
  - access_count_to_reset_password_page: パスワードリセット画面にアクセスした回数

[Target]ターゲット情報マスタ(例: 父・母・兄弟,etc...)
  - value: ターゲット情報

[Category]カテゴリマスタ(例： 食事・贈り物・旅行, etc...)
  - value: カテゴリ情報

[Article]孝行の記録情報
  - user_id: 投稿者のユーザーID
  - target_id: ターゲット情報のID
  - category_id: カテゴリ情報のID
  - days: 孝行の実施日数
  - cost: 費用
  - title: タイトル
  - body: 詳細
  - picture: 画像用

[Forum]フォーラム機能
  - user_id: 投稿者のユーザID
  - target_id: ターゲット情報のID
  - category_id: カテゴリ情報のID
  - days: 孝行の実施日数
  - cost: 予算
  - title: タイトル
  - body: 詳細

[Project]プロジェクト機能
  - user_id: 投稿者のユーザID
  - target_id: ターゲット情報のID
  - category_id: カテゴリ情報のID
  - limit_date: 締切日
  - cost: 予算
  - title: タイトル
  - body: 詳細

[Comment]Article/Forumに対するコメント
  - commentable_type: Article or Forum
  - commentable_id: Article or ForumのID
  - user_id: コメントをしたユーザのID
  - body: コメント内容


[Favorite]Article/Forum/Projectに対するお気に入り
  - favoritable_type: Article or Forum or Project
  - favoritable_id: Article or Forum or ProjectのID
  - user_id: お気に入りをしたユーザのID

[Task]プロジェクトのタスク
  - user_id: タスクを作成したユーザのID
  - project_id: タスク対象のプロジェクトID
  - sort_number: 画面での表示順
  - value: タスク内容

[Action]プロジェクトでの行動記録
  - user_id: アクションを作成したユーザのID
  - project_id: アクション対象のプロジェクトID
  - sort_number: 画面での表示順
  - value: アクション内容

[Apikey]トークン認証用のトークンテーブル
  - user_id: 認証対象のユーザ
  - access_token: トークン
  - expires_at: トークン有効期限

■技術選定　:調査中

- Rails7
- postgresql
- React（仮） 
  - <調査中>:認証まわりを調べる。トークンをクッキーor外部認証サービス（Auth0?）
- tailwind or Bootstrap 
  - <調査中>:tailwind でスピーディに開発できそうか？　
