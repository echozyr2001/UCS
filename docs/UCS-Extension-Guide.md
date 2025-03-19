# UCS 扩展指南

## 概述
UCS 协议设计为可扩展的，支持自定义字段和新的平台集成。

## 扩展字段
### 在 `raw` 字段中添加自定义数据
`raw` 字段用于保留原始平台数据，可以在其中添加自定义字段。例如：
```json
{
  "raw": {
    "custom_field": "custom_value"
  }
}
```

### 扩展新的平台
1. 在 `platform` 字段中使用唯一的平台标识。
2. 在 `raw` 字段中保留原始平台数据。
3. 更新 [UCS-Platform-Mapping.md](./UCS-Platform-Mapping.md) 中的平台映射表。

## 扩展新的模块
1. 创建新的 JSON Schema 文件，定义模块的数据结构。
2. 在 `ucs-api-v1.yaml` 中添加新的 API 接口。
3. 更新 [UCS-Core-Models.md](./UCS-Core-Models.md) 中的核心模型定义。
