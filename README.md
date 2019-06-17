<<<<<<< HEAD
# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
=======
## DB設計
## userテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|
|user_id|string|null: false, foreign_key: true|
|group_id|string|null: false, foreign_key: true|
|member_id||user_id|string|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :members
- has_many :groups through: :members


>>>>>>> 5cfa6e2280db2bd1fa66f400df0f8c469867ba43
## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|string|
|image|string|
|user_id|string|null: false, foreign_key: true|
|group_id|string|null: false, foreign_key: true|

### Association
- belong_to :user
- belong_to :group



## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, inique :true, index|

### Association
- has_many :members
- has_many :messages
- has_many :users, through: members


## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user