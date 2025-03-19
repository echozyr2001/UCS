# UCS 协议规范

## 概述
UCS（Unified Content Schema）是一套面向内容平台聚合与标准化的开放协议，旨在为内容、用户、评论等核心对象提供统一的数据结构定义与 API 接口规范，以实现平台无关、可扩展、易集成的内容生态标准。

## 版本
当前版本：1.0.0

## 核心模块
### UCS-User 模块（用户信息结构）
该模块定义了用户的基本信息，支持跨平台用户数据的统一表示。

### UCS-Content 模块（内容结构）
该模块定义了内容的基本信息，支持多种内容类型和详细指标。

### UCS-Comment 模块（评论结构）
该模块定义了评论的基本信息，支持嵌套评论结构。

## 数据结构
详细的数据结构定义请参考 [UCS-Core-Models.md](./UCS-Core-Models.md)。

## API 接口
详细的 API 接口设计请参考 [UCS-API-Design.md](./UCS-API-Design.md)。

## 平台映射
平台字段的映射规则请参考 [UCS-Platform-Mapping.md](./UCS-Platform-Mapping.md)。

## 扩展指南
如何扩展 UCS 协议请参考 [UCS-Extension-Guide.md](./UCS-Extension-Guide.md)。
