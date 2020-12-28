FORMAT: 1A
HOST: http://mitsu.uyupun.tech/api/v2

# Web APIドキュメント
SOCIAL RESISTANCEのバックエンドAPIサーバ・MitsuのWeb API仕様書

## 登録 [POST /register]
ユーザーを登録する  
登録/ログイン後、各APIでは生成されたトークンをAuthorizationヘッダーのBearerスキーム上に載せて送信する

+ Request (application/json)
    + Attributes
        + userId: `xxxx` (string, required) - ユーザーのID
        + password: `xxxx` (string, required) - パスワード

+ Response 200 (application/json)
    + Attributes
        + token: `xxxx` (string) - JWT

## ログイン [POST /login]
ログインする  
登録/ログイン後、各APIでは生成されたトークンをAuthorizationヘッダーのBearerスキーム上に載せて送信する  
ログアウトはクライアント側で行う

+ Request (application/json)
    + Attributes
        + userId: `xxxx` (string, required) - ユーザーのID
        + password: `xxxx` (string, required) - パスワード

+ Response 200 (application/json)
    + Attributes
        + token: `xxxx` (string) - JWT

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
        + role: `1` (number, required) - プレイヤーの種類（1: うさぎさん | 2: ばいきんくん）
        + isPublic: `true` (boolean, required) - ワールドを公開するかどうか

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

## ワールドの検索 [GET /search]
ワールドを検索する

+ Request (application/json)
    + Attributes
        + page: `1` (number, required) - ページ番号
        + limit: `10` (number, required) - ワールドの取得件数

+ Response 200 (application/json)
    + Attributes
        + page: `1` (number) - ページ番号
        + limit: `10` (number) - ワールドの取得件数
        + total: `20` (number) - ワールドの合計件数
        + worlds (array[object], fixed-type)
            + (object)
                + id: `xxxx` (string) - ワールドID
                + role: `1` (number) - プレイヤーの種類（1: うさぎさん | 2: ばいきんくん）
