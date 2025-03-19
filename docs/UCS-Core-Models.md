# UCS 核心模型

## UCS-User 模块
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

## UCS-Content 模块
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "content_id": { "type": "string" },
    "platform": { "type": "string" },
    "type": { "type": "string", "enum": ["video", "article", "note", "live"] },
    "title": { "type": "string" },
    "description": { "type": "string" },
    "cover_url": { "type": "string", "format": "uri" },
    "content_url": { "type": "string", "format": "uri" },
    "author": { "$ref": "ucs-user.schema.json" },
    "tags": { "type": "array", "items": { "type": "string" } },
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

## UCS-Comment 模块
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
    "replies": { "type": "array", "items": { "$ref": "ucs-comment.schema.json" } },
    "raw": { "type": "object" }
  },
  "required": ["comment_id", "content_id", "platform", "user", "text"]
}
```
