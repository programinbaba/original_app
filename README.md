# テーブル設計

## tweets テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| title  | string     | null: false                    |
| text   | text       | null: false                    |
| user   | references | null: false, foreign_key: true |

### Association
- has_many :tweet_tags
- has_many :tags, through: :tweet_tags
- belongs_to :user
- has_many :comments

## tags テーブル
| Column | Type   | Options                       |
| ------ | ------ | ----------------------------- |
| name   | string | null: false, uniqueness: true |

### Association
- has_many :tweet_tags
- has_many :tweets, through: :tweet_tags

## tweet_tags テーブル
| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| tweet  | references | null: false, foreign_key: true |
| tag    | references | null: false, foreign_key: true |

### Association
- belongs_to :tweet
- belongs_to :tag

## users テーブル
| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association
- has_many :tweets
- has_many :comments

## comments テーブル
| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| text   | string     | null: false                    |
| tweet  | references | null: false, foreign_key: true |
| user   | references | null: false, foreign_key: true |

### Association
- belongs_to :tweet
- belongs_to :user