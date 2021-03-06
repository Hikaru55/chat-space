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

# DB設計

## usersテーブル

|colum|type|options|
|-----|----|-------|
|name|string|null: false, unique :true, add_index|
|email|string|null: false, unique :true|

### Association
- has_many :messages
- has_many :groups, through: :group_users
- has_many :group_users

## messagesテーブル

|colum|type|options|
|-----|----|-------|
|body|text|null: false|
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル

|colum|type|options|
|-----|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many :users, through: :group_users
- has_many :messages
- has_many :messages

## group_usersテーブル

|colum|type|options|
|-----|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
