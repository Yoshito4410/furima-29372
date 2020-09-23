# README

## users テーブル

| Column          | Type   | Options                      |
| --------------- | ------ | ---------------------------- |
| nickname        | string | null: false                  |
| email           | string | null: false, uniqueness:true |
| password        | string | null: false, uniqueness:true |
| last_name       | string | null: false                  |
| first_name      | string | null: false                  |
| last_name_kana  | string | null: false                  |
| first_name_kana | string | null: false                  |
| birth_date      | date   | null: false                  |

### Association

- has_many :items
- belong_to :addresses
- has_many :purchases

## items テーブル

| Column           | Type       | Options                       |
| ---------------- | ------     | ----------------------------- |
| user             | references | null: false, foreign_key:true |
| name             | string     | null: false                   |
| description      | text       | null: false                   |
| category_id      | integer    | null: false                   |
| condition_id     | integer    | null: false                   |
| postage_payer_id | integer    | null: false                   |
| prefecture_id    | integer    | null:false                    |
| handling_time_id | integer    | null: false                   |
| price            | integer    | null: false                   |


### Association

- belong_to :users
- belong_to :image
- has_one :purchases

## image テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| item   | references | null: false, foreign_key: true |
| image  | string     | null: false                    |

### Association

- belong_to :user

## addresses テーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| post_code        | string     | null: false                    |
| prefecture_id    | integer    | null: false, foreign_key: true |
| city             | string     | null: false                    |
| building_name    | string     |                                |
| phone_name       | string     | null: false, uniqueness:true   |
| purchase         | references | null: false, foreign_key:true  |

### Association

- belong_to :items
- belong_to :users
- belong_to :purchases

## purchases テーブル

| Column        | Type          | Options                       |
| ------------- | ------------- | ----------------------------- |
| item          | references    | null: false, foreign_key:true |
| user          | references    | null: false, foreign_key:true |

### Association

- has_one :addresses