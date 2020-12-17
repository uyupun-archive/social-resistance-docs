# SOCIAL RESISTANCE Documents

[SOCIAL RESISTANCE](https://github.com/uyupun/social-resistance)'s documents repository.

### Index

- [アブストラクト](abstract.md)
- [ターゲット層について](target.md)
- [システム構成図](system_architecture.md)
- [システム化の範囲と目的](project_scope.md)
- [スケジュール](schedule.md)
- [画面遷移図](screen_transition.md)
- カンプ
  - [v1](https://www.figma.com/file/SYnE52gQISHkQLZV9NPJG1/Social-Resistance?node-id=0%3A1)
  - [v2](https://www.figma.com/file/SYnE52gQISHkQLZV9NPJG1/Social-Resistance?node-id=192%3A574)
  - [v3](https://www.figma.com/file/SYnE52gQISHkQLZV9NPJG1/Social-Resistance?node-id=428%3A2)
- [Web APIドキュメント](web_api.md) （[HTML版](web_api.html)）
- [クラス図](class.md)
- [DB設計](db.md)
- [WebSocketフロー](web_socket_flow.md)
- 状態遷移図
- [ワールドのステータスについて](world_status.md)
- [レートとランク一覧](rate_and_rank.md)

### 環境構築（PlantUML）

開発環境はmacOSを想定。

```bash
# Javaがインストールされている前提です
$ brew install graphviz
$ brew install plantuml
# png形式で出力される
$ plantuml foo.pu
```

[VSCodeの拡張](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)を使用するのも良い。

### 環境構築（API Blueprint + aglio）

```bash
$ npm install -g aglio
# HTML形式で出力される
$ aglio -i foo.md -o foo.html
# API仕様書を開く
$ open foo.html
```
