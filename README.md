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

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル

｜Coluom|Type|Options|
｜------|----|-------|
|name|string|null:false, index:true, unique:true|
|email|string|null:false, unique:true|


### Association
- has_many :groups_users
- has_many :groups, through: groups_users
- has_many :messages

## groupsテーブル

｜Coluom|Type|Options|
｜------|----|-------|
|name|string|null:false, unique:true|

### Association
- has_many :groups_users
- has_many :users, through: groups_users
- has_many :messages

## messagesテーブル

｜Coluom|Type|Options|
｜------|----|-------|
|body|text|
|image|string|
|user_id|references|null:false, foreign_key:true|
|group_id|references|null:false, foreign_key:true|

### Association
- belongs_to :group
- belongs_to :user
