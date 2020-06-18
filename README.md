# README

# ChatSpaceデータベースh1

## usersテーブルh2
|Column|Type|Validation|
|------|----|----------|
|id|integer|null: false, unique: true|
|user_name|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false, length: { minimum: 8 }|
### Association
- has_many :groups, through: :users_groups
- has_many :chat_comments


## groupsテーブルh2
|Column|Type|Validation|
|------|----|----------|
|id|integer|null: false, unique: true|
|group_name|string|null: false|
### Association
- has_many :users, through: :users_groups
- has_many :chat_comments

## users_groupsの中間テーブルh2
|Column|Type|Validation|
|------|----|----------|
|id|integer|null: false, unique: true|
|user_id|integer|foreign_key|
|group_id|integer|foreign_key|
### Association
- belongs_to :users
- belongs_to :groups

## chat_commentsテーブルh2
|Column|Type|Validation|
|------|----|----------|
|id|integer|null: false, unique: true|
|comment|text|length: { minimum: 100 }|
|image|text|url, format: URI::regexp(%w(http https))|
|user_id|integer|foreign_key: true, dependent: delete|
|group_id|integer|foreign_key: true, dependent: delete|
### Association
- belongs_to :users
- belongs_to :groups


