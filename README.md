# アプリケーション名
reito-36114-app

# アプリケーション概要
登録した商品を元に口コミが登録できる

# URL
https://reito-36114-app.herokuapp.com/

# テスト用アカウント
MAIL:akai@sherlock.jp Pass:shuichi4869

# 利用方法
1. 新規登録/ログインをする
2. 商品詳細ページから口コミ投稿する

# 目指した課題解決
ターゲット：主婦/主夫
課題：お弁当に入れる冷凍食品の種類が固定されて飽きが来てしまう
解決：冷凍食品の口コミサイトから新たな商品発掘ができる

# 洗い出した要件
1. ユーザー管理機能
2. 商品登録機能
3. 口コミ機能


# データベース設計
[![Image from Gyazo](https://i.gyazo.com/939742e27b0d4a07abe85c9e4791606a.png)](https://gyazo.com/939742e27b0d4a07abe85c9e4791606a)




# テーブル設計
## usersテーブル

| Column             | Type   | Options                  |
| ------------------ | ------ | ------------------------ |
| nickname           | string | null:false               |
| email              | string | null:false, unique: true |
| encrypted_password | string | null:false               |
| age                | string |                          |

### Association
has_many :reviews


## productsテーブル
| Column                    | Type    | Options    |
| ------------------------- | ------- | ---------- |
| product_name              | string  | null:false |
| description               | text    | null:false |
| genre_id                  | integer | null:false |
| category_id               | integer | null:false |
| cooking_method_id         | integer | null:false |
| cooking_method2_id        | integer |            |
| company_id                | integer | null:false |

### Association
has_many :reviews


## reviewsテーブル
| Column             | Type       | Options                      |
| ------------------ | ---------- | ---------------------------- |
| title              | string     | null:false                   |
| created_on         | date       | null:false                   |
| recommend_score_id | integer    | null:false                   |
| comment            | text       | null:false                   |
| category_id        | integer    | null:false                   |
| user_id            | references | null:false,foreign_key: true |
| product_id         | references | null:false,foreign_key: true |

### Association
belongs_to :user
belongs_to :product