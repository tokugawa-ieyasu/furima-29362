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

# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :items
- has_one :buy

## items テーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| name           | string     | null: false                    |
| introduction   | text       | null: false                    |
| category       | references | null: false, foreign_key: true |
| item_condition | references | null: false, foreign_key: true |
| postage_payer  | references | null: false, foreign_key: true |
| area           | string     | null: false                    |
| day            | references | null: false, foreign_key: true |
| price          | integer    | null: false                    |

### Association

- has_many :users

## buy テーブル

| Column  | Type   | Options     |
| ------- | ------ | ----------- |
| user_id | string | null: false |
| item    | string | null: false |

### Association

- has_one :user
- has_one :item

## delivery_address テーブル

| Column       | Type    | Options     |
| ------------ | ------- | ----------- |
| postal_code  | integer | null: false |
| prefecture   | string  | null: false |
| city         | string  | null: false |
| address      | string  | null: false |
| phone_number | integer | null: false |

### Association

- has_one :buy