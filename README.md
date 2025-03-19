# UCS - Unified Content Schema

**版本**: 1.0.0

**UCS（Unified Content Schema）** 是一套面向内容平台聚合与标准化的开放协议，旨在为内容、用户、评论等核心对象提供统一的数据结构定义与 API 接口规范，以实现平台无关、可扩展、易集成的内容生态标准。

## UCS-User 模块（用户信息结构）

该模块定义了用户的基本信息，支持跨平台用户数据的统一表示。

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
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

### 示例

```json
{
  "user_id": "12345",
  "platform": "weibo",
  "nickname": "JohnDoe",
  "avatar_url": "https://example.com/avatar.jpg",
  "bio": "A passionate developer",
  "followers": 1000,
  "followings": 200,
  "verified": true
}
```

## UCS-Comment 模块（评论结构）

该模块定义了评论的基本信息，支持嵌套评论结构。

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "comment_id": { "type": "string" },
    "content_id": { "type": "string" },
    "platform": { "type": "string" },
    "user": { "$ref": "ucs-user.schema.json" },
    "text": { "type": "string" },
    "created_at": { "type": "string", "format": "date-time" },
    "like_count": { "type": "integer" },
    "replies": {
      "type": "array",
      "items": { "$ref": "ucs-comment.schema.json" }
    },
    "raw": { "type": "object" }
  },
  "required": ["comment_id", "content_id", "platform", "user", "text"]
}
```

### 示例

```json
{
  "comment_id": "67890",
  "content_id": "12345",
  "platform": "weibo",
  "user": {
    "user_id": "12345",
    "platform": "weibo",
    "nickname": "JohnDoe"
  },
  "text": "Great post!",
  "created_at": "2023-10-01T12:34:56Z",
  "like_count": 10
}
```

## UCS-Content 模块（内容结构）

该模块定义了内容的基本信息，支持多种内容类型和详细指标。

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
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
    "author": { "$ref": "ucs-user.schema.json" },
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

### 示例

```json
{
  "content_id": "54321",
  "platform": "youtube",
  "type": "video",
  "title": "Introduction to UCS",
  "description": "A brief introduction to the Unified Content Schema.",
  "cover_url": "https://example.com/cover.jpg",
  "content_url": "https://example.com/video.mp4",
  "author": {
    "user_id": "12345",
    "platform": "youtube",
    "nickname": "JohnDoe"
  },
  "tags": ["UCS", "tutorial"],
  "metrics": {
    "views": 10000,
    "likes": 500,
    "comments": 50,
    "shares": 200
  },
  "created_at": "2023-09-01T12:34:56Z",
  "updated_at": "2023-09-02T12:34:56Z"
}
```