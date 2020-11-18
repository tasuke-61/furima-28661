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

## usersテーブル


| Column            |Type  |Options     |
|-------------------|------|------------|
|nickname           |string|null: false |
|email              |string|null: false |
|encrypted_password |string|null: false |
|family_name        |string|null: false |
|first_name         |string|null: false |
|kana_family_name   |string|null: false |
|kana_first_name    |string|null: false | 
|birthday           |date  |null: false | 

| Column         |Type  |Options     |
|----------------|------|------------|
|nickname        |string|null: false |
|mail            |string|null: false |
|password        |string|null: false |
|family_name     |string|null: false |
|first_name      |string|null: false |
|kana_family_name|string|null: false |
|kana_first_name |string|null: false | 



### Association
has_many :items
has_many :purchase_records


## itemsテーブル

| Column          |Type      |Options                        |
|-----------------|----------|-------------------------------|
|name             |string    |null: false                    |
|explain          |text      |null: false                    |
|item_id          |integer   |null: false                    |
|category_id      |integer   |null: false                    |
|status_id        |integer   |null: false                    |
|delivery_fee_id  |integer   |null: false                    |
|shipping_place_id|integer   |null: false                    |
|shipping_day_id  |integer   |null: false                    |
|price            |integer   |null: false                    |
|user             |references|null: false, foreign_key: true |



### Association
belongs_to :user
has_one :purchase_record
belongs_to :item

| Column         |Type      |Options                        |
|----------------|----------|-------------------------------|
|image           |string    |null: false                    |
|item_name       |string    |null: false                    |
|item_explain    |string    |null: false                    |
|item_category   |string    |null: false                    |
|item_status     |string    |null: false                    |
|delivery_fee    |string    |null: false                    |
|shipping_place  |string    |null: false                    |
|shipping_days   |integer   |null: false                    |
|price           |integer   |null: false                    |
|user_id         |references|null: false, foreign_key: true |


### Association
belongs_to :users
has_one :purchase_records



## purchase_recordsテーブル


| Column |Type      |Options                        |
|--------|----------|-------------------------------|
|user    |references|null: false, foreign_key: true |
|item    |references|null: false, foreign_key: true |


### Association
belongs_to :user
belongs_to :item

| Column   |Type      |Options                        |
|----------|----------|-------------------------------|
|users_id  |references|null: false, foreign_key: true |
|items_id  |references|null: false, foreign_key: true |


### Association
belongs_to :users
belongs_to :items



## addressesテーブル


| Column        |Type      |Options                        |
|---------------|----------|-------------------------------|
|post_number    |string    |null: false                    |
|address_id     |integer   |null: false                    |
|prefecture_id  |integer   |null: false                    |
|city           |string    |null: false                    |
|house_number   |string    |null: false                    |
|building_name  |string    |                               |
|phone_number   |string    |null: false                    |
|purchase_record|references|null: false, foreign_key: true |


### Association
belongs_to :purchase_record
belongs_to :address

| Column            |Type      |Options                        |
|-------------------|----------|-------------------------------|
|post_number        |integer   |null: false                    |
|prefecture         |string    |null: false                    |
|city               |string    |null: false                    |
|house_number       |integer   |null: false                    |
|building_name       |string    |null: false                    |
|phone_number       |integer   |null: false                    |
|purchase_records_id|references|null: false, foreign_key: true |


### Association
belongs_to :purchase_records

