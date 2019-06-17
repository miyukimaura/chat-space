## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false|
|password|string|null: false|
|user|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
|member_id|references|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :members
- has_many :groups through: :members


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|string|
|image|string|
|user|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

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
|user|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user