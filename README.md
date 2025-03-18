# UCS - Unified Content Schema

**UCS（Unified Content Schema）** 是一套面向内容平台聚合与标准化的开放协议，旨在为内容、用户、评论等核心对象提供统一的数据结构定义与 API 接口规范，以实现平台无关、可扩展、易集成的内容生态标准。

## UCS-User 模块（用户信息结构）

```json
{
  "$schema": "",
  "type": "object",
  "properties": {
    "user_id": { "type": "string" },
    "platform": { "type": "string" },
    "nickname": { "type": "string" },
    "avatar_url": { "type": "string", "format": "uri" },
    "bio": { "type": "string" },
    "followers": { "type": "integer" },
    "followings": { "type": "integer" },
    "verified": { "type": "boolean" },
    "raw": { "type": "object" }
  },
  "required": ["user_id", "platform", "nickname"]
}
```

## UCS-Comment 模块（评论结构）

```json
{
  "$schema": "",
  "type": "object",
  "properties": {
    "comment_id": { "type": "string" },
    "content_id": { "type": "string" },
    "platform": { "type": "string" },
    "user": { "$ref": "usc-user.schema.json" },
    "text": { "type": "string" },
    "created_at": { "type": "string", "format": "date-time" },
    "like_count": { "type": "integer" },
    "replies": {
      "type": "array",
      "items": { "$ref": "usc-comment.schema.json" }
    },
    "raw": { "type": "object" }
  },
  "required": ["comment_id", "content_id", "platform", "user", "text"]
}
```

## UCS-Content 模块（内容结构）

```json
{
  "$schema": "",
  "type": "object",
  "properties": {
    "content_id": { "type": "string" },
    "platform": { "type": "string" },
    "type": {
      "type": "string",
      "enum": ["video", "article", "note", "live"]
    },
    "title": { "type": "string" },
    "description": { "type": "string" },
    "cover_url": { "type": "string", "format": "uri" },
    "content_url": { "type": "string", "format": "uri" },
    "author": { "$ref": "usc-user.schema.json" },
    "tags": {
      "type": "array",
      "items": { "type": "string" }
    },
    "metrics": {
      "type": "object",
      "properties": {
        "views": { "type": "integer" },
        "likes": { "type": "integer" },
        "comments": { "type": "integer" },
        "shares": { "type": "integer" }
      }
    },
    "created_at": { "type": "string", "format": "date-time" },
    "updated_at": { "type": "string", "format": "date-time" },
    "raw": { "type": "object" }
  },
  "required": ["content_id", "platform", "type", "title"]
}
```