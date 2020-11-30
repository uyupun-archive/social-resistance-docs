FORMAT: 1A
HOST: http://mitsu.uyupun.tech/api/v1

# Mitsu API
ゲームの進行を主に担当するMitsuのWeb API仕様

## ルールの取得 [GET /rules]
ルールを取得する

+ Request (application/json)
    + Attributes

+ Response 200 (application/json)
    + Attributes (array[object], fixed-type)
        + (object)
            + text: `プレイヤーは相手プレイヤーを募集するか、ワールドへ参加するかを選択します。` (string) - テキスト
            + image: `/images/rules/rule_1.png` (string) - 画像
        + (object)
            + text: `相手プレイヤーを募集する場合は、『うさぎさん』または『ばいきんくん』のどちらかを募集します。` (string) - テキスト
            + image: `/images/rules/rule_2.png` (string) - 画像

## 募集 [GET /recruit]
ワールドID、トークンの生成

+ Request (application/json)
    + Attributes
        + recruit: `1` (number, required) - プレイヤーの種類（1: うさぎさん | 2: ばいきんくん）

+ Response 200 (application/json)
    + Attributes
        + worldId: `xxxx` (string) - ワールドID
        + token: `xxxx` (string) - アクセストークン
        + role: `1` (number) - プレイヤーの種類（1: うさぎさん | 2: ばいきんくん）

## 参加 [GET /join]
ワールドIDの正当性のチェック、トークンの生成

+ Request (application/json)
    + Attributes
        + worldId: `xxxx` (string, required) - ワールドID

+ Response 200 (application/json)
    + Attributes
        + validity: `true` (boolean) - ワールドIDが正当なものかどうか
        + token: `xxxx` (string) - アクセストークン
        + role: `2` (number) - プレイヤーの種類（1: うさぎさん | 2: ばいきんくん）

## ワールド情報の確認 [GET /states]
ワールドの情報（ワールドID、ステータス、作成日時）の確認  
現状、本番環境では使用できない

+ Request (application/json)
    + Attributes

+ Response 200 (application/json)
    + Attributes
        + id: `xxxx` (string) - ワールドID
        + status: `xxxx` (string) - ステータス（initialized | waiting | playing | judged | disconnected）
        + createdAt: `2020/12/01 01:17:00` (string) - 作成日時
