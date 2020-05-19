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

## users table
|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|name|string|null: false, unique: true|
|email|string|null: false|
### Association
- has_many :groups, through: :groups_users
- has_many :groups_users
- has_many :messages

## groups table
|Column|Type|Options|
|------|----|-------|
|id|integer|null: false|
|name|string|null: false|
|users_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :users
- has_many :users, through: :groups_users
- has_many :messages

## groups_users table
|Column|Type|Options|
|------|----|-------|
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|
### Association
- has_many :users
- has_many :groups

## messages table
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|groups_id|integer|null: false, foreign_key: true|
|users_id|integer|null: false, foreign_key: true|
### Association
- blongs_to :users
- belongs_to :groups