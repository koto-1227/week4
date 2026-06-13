# Week3 APIインタフェース定義書 作成プロンプト

## 使用方法
TaskAPI_Template.mdと課題説明書をもとに、以下の内容を参考にしてAPIインタフェース定義書を作成しました。

## 課題条件
- GET /health
- GET /tasks
- GET /tasks/{task_id}
- POST /tasks
- PUT /tasks/{task_id}
- DELETE /tasks/{task_id}

## 共通ルール
- Base URL: http://localhost:8080
- Content-Type: application/json
- 日時形式: ISO 8601
- statusは todo / doing / done