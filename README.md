# テーブル設計

## usersテーブル

| Column                 | Type   | Options     |
| ---------------------- | ------ | ----------- |
| nickname               | string | null: false |
| email                  | string | nill: false |
| password               | string | null: false |
| encrypted_password     | string | null: false |
| family_name            | string | null: false |
| first_name             | string | null: false |
| family_name_full_width | string | null: false |
| first_name_full_width  | string | null: false |
| birth_day              | string | null: false |

### Association

- has_many :items
- has_many :purchases

## itemsテーブル

| Column              | Type    | Options     |
| ------------------- | ------- | ----------- |
| name                | string  | null: false |
| description         | text    | null: false |
| details_category_id | integer | null: false |
| details_status_id   | integer | null: false |
| shipping_charges_id | integer | null: false |
| shipping_area_id    | integer | null: false |
| shipping_days_id    | integer | null: false |
| selling_price       | integer | null: false |

### Association

- belongs_to :user
- has_one :purchase

## purchasesテーブル

| Column | Type       | Options           |
| ------ | ---------- | ----------------- |
| user   | references | foreign_key: true |
| item   | references | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :sipping_address

## shipping_addressテーブル

| Column           | Type       | Options           |
| ---------------- | ---------- | ----------------- |
| postal_code      | integer    | null: false       |
| shipping_area_id | integer    | null: false       |
| municipality     | string     | null: false       |
| address          | string     | null: false       |
| building_name    | string     |                   |
| phone_number     | string     |                   |
| purchase         | references | foreign_key: true |

### Association

- belongs_to :purchase
