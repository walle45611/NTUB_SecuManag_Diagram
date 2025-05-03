sequenceDiagram
    actor User as 使用者
    participant Frontend
    participant Backend
    participant Database

    User->>Frontend: 點擊「版本歷史」
    Frontend->>Backend: GET /api/system/asset-settings/{origin_id}/history
    Backend->>Database: 查詢 version_group_id = origin_object.version_group_id 的所有版本
    Backend-->>Frontend: 回傳版本清單
    Frontend->>Frontend: 顯示版本列表與基本資訊
