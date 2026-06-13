# Tasks API 仕様書

## 概要
学習用のタスク管理APIです。
タスクの作成・取得・更新・削除を行います。

## 共通仕様
- Base URL: `http://localhost:8080`
- Content-Type: `application/json`
- 日時形式: ISO 8601
- `status`: `todo` / `doing` / `done`

## 1. ヘルスチェック
- Method: `GET`
- Path: `/health`

### Response 200
```json
{
  "status": "ok"
}
```

## 2. タスク一覧取得
- Method: `GET`
- Path: `/tasks`

### Response 200
```json
{
  "items": [
    {
      "id": 1,
      "title": "Pythonを復習する",
      "description": "Week1の内容を見直す",
      "status": "todo",
      "due_date": "2026-04-10T18:00:00+09:00",
      "created_at": "2026-04-01T19:00:00+09:00",
      "updated_at": "2026-04-01T19:00:00+09:00"
    }
  ],
  "total": 1
}
```

## 3. タスク取得
- Method: `GET`
- Path: `/tasks/{task_id}`

### Response 200
```json
{
  "id": 1,
  "title": "Pythonを復習する",
  "description": "Week1の内容を見直す",
  "status": "todo",
  "due_date": "2026-04-10T18:00:00+09:00",
  "created_at": "2026-04-01T19:00:00+09:00",
  "updated_at": "2026-04-01T19:00:00+09:00"
}
```

### Response 404
```json
{
  "error": {
    "code": "NOT_FOUND",
    "message": "task not found"
  }
}
```

## 4. タスク作成
- Method: `POST`
- Path: `/tasks`

### Request
```json
{
  "title": "FastAPIを試す",
  "description": "POST /tasks を実装する",
  "status": "doing",
  "due_date": "2026-04-15T20:00:00+09:00"
}
```

### Response 201
```json
{
  "id": 2,
  "title": "FastAPIを試す",
  "description": "POST /tasks を実装する",
  "status": "doing",
  "due_date": "2026-04-15T20:00:00+09:00",
  "created_at": "2026-04-01T20:00:00+09:00",
  "updated_at": "2026-04-01T20:00:00+09:00"
}
```

### Response 400
```json
{
  "error": {
    "code": "BAD_REQUEST",
    "message": "title is required"
  }
}
```

## 5. タスク更新
- Method: `PUT`
- Path: `/tasks/{task_id}`

### Request
```json
{
  "title": "FastAPIを試す",
  "description": "PUT /tasks/{task_id} も実装する",
  "status": "done",
  "due_date": "2026-04-16T20:00:00+09:00"
}
```

### Response 200
```json
{
  "id": 2,
  "title": "FastAPIを試す",
  "description": "PUT /tasks/{task_id} も実装する",
  "status": "done",
  "due_date": "2026-04-16T20:00:00+09:00",
  "created_at": "2026-04-01T20:00:00+09:00",
  "updated_at": "2026-04-01T20:30:00+09:00"
}
```

## 6. タスク削除
- Method: `DELETE`
- Path: `/tasks/{task_id}`

### Response 204
本文は返しません。
