# 単語情報（MySQL）

- word2vecs

|カラム名|型|説明|
|:--|:--|:--|
|id|数値|連番のID|
|word|文字列|単語|
|move_x|実数|単語のベクトル値（x）|
|move_y|整数|単語のベクトル値（y）|

# ワールド情報（Expressに内包された独自のデータストア）

```json
[
  {
    "id": "xxxx",
    "players": {
      "1": "<user_id>",
      "2": "<user_id>"
    },
    "field": Field,
    "turn": Turn,
    "word": Word,
    "dealer": Dealer,
    "createdAt": "xxxx",
    "status": 1,
    "isPublic": true
  }
]
```

# ユーザー情報（MySQL）

- users

|カラム名|型|説明|
|:--|:--|:--|
|user_id|文字列|ユーザーID|
|password|文字列|ハッシュ化されたパスワード|
|created_at|日付|作成日|
|updated_at|日付|更新日|
