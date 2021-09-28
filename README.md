# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| phone_number       | string | null: false |
| last_name          | string | null: false |
| first_name         | string | null: false |
| age                | string | null: false |
| job                | string | null: false |
| profile            | string | null: false |
| prefecture         | string | null: false |


### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages
- has_many :animals

## animals テーブル

| Column             | Type           | Options     |
| ------------------ | -------------- | ----------- |
| name               | string         | null: false |
| image              | ActiveStorage  | null: false |
| genre              | string         | null: false |
| gender             | string         | null: false |
| birthday           | string         | null: false |
| anm_age            | string         | null: false |
| user               | string         | null: false |
| prefecture         | string         | null: false |
| catch_copy         | string         | null: false |


### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages
- has_many :animals



## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user