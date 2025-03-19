# UCS API 设计

## 概述
UCS API 提供统一的内容、用户、评论接口，支持跨平台数据聚合与查询。

## 接口列表
### 查询内容列表
- **路径**: `/contents`
- **方法**: `GET`
- **参数**:
  - `platform`: 内容所属平台（必填）
  - `type`: 内容类型（可选）
  - `keyword`: 内容关键词搜索（可选）
- **响应**: 返回内容列表，数据结构为 `UCS-Content` 数组。

### 获取内容详情
- **路径**: `/contents/{platform}/{content_id}`
- **方法**: `GET`
- **参数**:
  - `platform`: 内容所属平台（必填）
  - `content_id`: 内容唯一标识（必填）
- **响应**: 返回内容详情，数据结构为 `UCS-Content`。

### 获取评论列表
- **路径**: `/comments/{platform}/{content_id}`
- **方法**: `GET`
- **参数**:
  - `platform`: 评论所属平台（必填）
  - `content_id`: 内容唯一标识（必填）
- **响应**: 返回评论列表，数据结构为 `UCS-Comment` 数组。

### 获取用户信息
- **路径**: `/users/{platform}/{user_id}`
- **方法**: `GET`
- **参数**:
  - `platform`: 用户所属平台（必填）
  - `user_id`: 用户唯一标识（必填）
- **响应**: 返回用户信息，数据结构为 `UCS-User`。
