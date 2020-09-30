# README


# テーブル設計

## users テーブル

| Column    | Type    | Options     |
| --------- | ------- | ----------- |
| name      | string  | null: false |
| email     | string  | null: false |
| password  | string  | null: false |

### Association

- has_many :user_plans
- has_many :plans, through: user_plans

## plans テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| title   | string     | null: false                    |

### Association

- has_many :user_plans
- has_many :users, through: user_plans
- has_one :detail

## user_plans テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| plan   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :plan

## details テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| start_time    | string     |                                |
| ending_time   | string     |                                |
| deadline_time | string     |                                |
| all_day       | string     |                                |
| comment       | text       |                                |
| plan          | references | null: false, foreign_key: true |

### Association

- belongs_to :plan
