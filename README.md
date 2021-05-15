# README

# AppName
schd-share

## Descriptions
- スケジュール投稿(編集/削除も可能)
- スケジュール作成
- コメント機能
- 新規登録/ログイン

## AppURL（※実装後記述）


## Production
家族や恋人、友人とスケジュールを共有できるアプリケーション。
子供がバイトを始めシフトを把握しておきたい、恋人とデートの予定を立てるのにお互いのスケジュールを確認したいといった悩みから、簡単にスケジュールの登録や家族や友人の確認ができるアプリケーションを制作。

## Account（※実装後記述）
### Basic
id:
pass:

### LoginPass（※実装後記述）
mail:
pass:

## テーブル設計

### users テーブル
| Column      | Type   | Options                   |
| ----------- | ------ | ------------------------- |
| accountname | string | null: false               |
| email       | string | null: false, unique: true |
| password    | string | null: false               |

#### Association
- has-many :rooms, through: :room_users
- has-many :room-users
- has_many :schedules

## rooms テーブル
| Column     | Type   | Options     |
| ---------- | ------ | ----------- |
| name       | string | null: false |
| password   | string | null: false |

#### Association
- has-many :users, through: :room_users
- has-many :room-users
- has_many :schedules

## room-users テーブル
| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

#### Association
- belongs_to :user
- belongs_to :room

### schedules テーブル
| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| text        | text       | null: false                    |
| user        | references | null: false, foreign_key: true |
| room        | references | null: false, foreign_key: true |

#### Association
- belongs_to :user
- belongs_to :room
