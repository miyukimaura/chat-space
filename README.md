# README

## usersテーブル
||Column|Type|Options|
|------|----|-------|
|id|integer|null: false, unique: true|
|name|string|null: false|
|email|string|null: false, unique: true|
|passwword|string|null: false|
|message_id|integer|null: false, foreign_key: true|
|member_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :users, through: :members
- has_many :users, through: :groupss

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|body|text|null: false|
|image|string|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|


### Association
- belong_to :user
- has_many :users, through: :groups

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- bolengs_to :group
- belongs_to :user

## groupテーブル

|Column|Type|Options|
|------|----|-------|

|user_id|integer|null: false, foreign_key: true|
|member_id|integer|null: false, foreign_key: true|
|message_id|integer|null: false, foreign_key: true|

### Association
- has_many :users, through: groups  
- has_many :mumbers, through: groups
- haz_many :mssages
