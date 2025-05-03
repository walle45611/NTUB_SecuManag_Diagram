sequenceDiagram
    actor User as 使用者
    participant Frontend
    participant Backend
    participant Database
    participant MinIO

    User->>Frontend: 選擇檔案並點「上傳」
    Frontend->>Backend: POST /api/files
    Backend->>Database: INSERT file_record(status='pending', metadata…)
    Backend->>MinIO: PUT 檔案到 MinIO Bucket
    alt 上傳成功
        Backend->>Database: UPDATE file_record(status='uploaded')
    else 上傳失敗
        Backend->>Database: UPDATE file_record(status='failed')
        Backend-->>Frontend: 回傳錯誤
    end
