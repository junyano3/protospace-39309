# README

## usersテーブル----------------------------------------------------------------
* 「データとして、保存できるものは以下のもの」
 + ### string型
  - email　※emailは同じものは保存できない（ユニーク制約：１つのemailで１つのuser）
  - name
   - encrypted_password

 + ### text型
  - profile
  - occupation
  - position

※上記全ての項目に関してカラムが空のレコードだと保存できない。（NOT_NULL制約）

### アソシエーション
* 1つのユーザーは、多くの写真投稿を持つことができる（phototypesテーブルと1対多の関係にある）
* 1つのユーザーは、多くのコメントを持つことができる（commentsテーブルと1対多の関係にある）
------------------------------------------------------------------------------


## phototypesテーブル ----------------------------------------------------------
* 「データとして、保存できるものは以下のもの」
 + ### string型
  - title

 + ### text型
  - catch_copy
  - concept

  + ### references型
   - user   ※（外部キー制約：user_idカラムのデータと、それに対応するusersテーブルの情報が必須になる
   ）

  ※上記全ての項目に関してカラムが空のレコードだと保存できない。（NOT_NULL制約）

### アソシエーション
user_idを保存するのは、1つの写真投稿には必ず1つのユーザーが紐付くため
1つの写真投稿は、多くのコメントを持つことができる（commentsテーブルと1対多の関係にある）
------------------------------------------------------------------------------


## commentsテーブル-------------------------------------------------------------
* 「データとして、保存できるものは以下のもの」
 + ### text型
  - content 

+ ### references型
 - prototype  ※（外部キー制約:prototype_idｶラムのデータと、それに対応するprototypesテーブルの情報が必須になる）
 - user       ※（外部キー制約:user_idカラムのデータと、それに対応するusersテーブルの情報が必須になる）

※上記全ての項目に関してカラムが空のレコードだと保存できない。（NOT_NULL制約）

### アソシエーション
prototype_idを保存するのは、1つのコメントには必ず1つのツイートが紐付くため
user_idを保存するのは、1つのコメントには必ず1つのユーザーが紐付くため
------------------------------------------------------------------------------