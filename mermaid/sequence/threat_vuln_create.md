sequenceDiagram
    actor User as 一般使用者
    participant Frontend
    participant Backend
    participant AI Module
    participant Database

    User->>Frontend: 新增弱點 / 威脅
    Frontend->>Backend: POST /api/isms/threat/ or /api/isms/vulnerability
    note over Backend, Frontend: 發送通知並等待核准允許流程完畢
    Backend->> AI Module: 評估弱點 / 威脅數值
    AI Module->>Database: 新增弱點 / 威脅資料
    Backend->>Frontend: 回傳並顯示至畫面
