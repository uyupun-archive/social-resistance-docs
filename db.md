# 単語情報（SQLite）

- word2vecs

|カラム名|型|説明|
|:--|:--|:--|
|id|数値|連番のID|
|word|文字列|単語|
|move_x|実数|単語のベクトル値（x）|
|move_y|整数|単語のベクトル値（y）|

# ワールド情報（Redis）

- Key
  - worldId

- Value
  - worldId
    - ワールドID
  - tokens.1
    - うさぎさんのトークン
  - tokens.2
    - ばいきんくんのトークン

```json
{
  "worldId": "xxxx",
  "tokens": {
    "1": "xxxx",
    "2": "xxxx"
  }
}
```

# ユーザー情報（MySQL）

- users

|カラム名|型|説明|
|:--|:--|:--|
|user_id|文字列|ユーザーID|
|password|文字列|ハッシュ化されたパスワード|
|token|文字列|アクセストークン|
|created_at|日付|作成日|
|updated_at|日付|更新日|
