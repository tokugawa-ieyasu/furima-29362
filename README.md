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

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| nickname        | string | null: false |
| email           | string | null: false |
| password        | string | null: false |
| last_name       | string | null: false |
| first_name      | string | null: false |
| last_name_kana  | string | null: false |
| first_name_kana | string | null: false |
| birth_date      | date   | null: false |

### Association

- has_many :items
- has_many :buy

## items テーブル

| Column         | Type       | Options     |
| -------------- | ---------- | ----------- |
| user           | references | null: false |
| name           | string     | null: false |
| introduction   | text       | null: false |
| category       | integer    | null: false |
| item_condition | integer    | null: false |
| postage_payer  | integer    | null: false |
| area           | integer    | null: false |
| day            | integer    | null: false |
| price          | integer    | null: false |

### Association

- belongs_to :user
- has_one :buy

## buys テーブル

| Column  | Type    | Options                        |
| ------- | ------- | ------------------------------ |
| user_id | integer | null: false, foreign_key: true |
| item_id | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :delivery_address

## delivery_address テーブル

| Column        | Type    | Options                        |
| ------------  | ------- | ------------------------------ |
| postal_code   | string  | null: false                    |
| prefecture    | integer | null: false                    |
| city          | string  | null: false                    |
| address       | string  | null: false                    |
| phone_number  | string  | null: false                    |
| building_name | string  |                                |
| buy_id        | integer | null: false, foreign_key: true |

### Association

- belongs_to :buy