## DB設計

## userテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index :usere, [:name, :email]|
|email|string|null: false|
|password|string|null: false|
|user_id|string|null: false, foreign_key: true|
|group_id|string|null: false, foreign_key: true|
|member_id||user_id|string|null: false, foreign_key: true|
|group_id|string|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :members
- has_many :groups
- has_many :groups through: :members


## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|string|null: false|
|image|string|
|user_id|string|null: false, foreign_key: true|
|group_id|string|null: false, foreign_key: true|

### Association
- belong_to :user
- belong_to :group


## groupテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|string|null: false, foreign_key: true|
|member_id||user_id|string|null: false, foreign_key: true|

### Association
- has_many :members
- has_many :users, through: members


## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user