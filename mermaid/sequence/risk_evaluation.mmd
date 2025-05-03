sequenceDiagram
    actor User as 使用者
    participant Frontend
    participant Backend
    participant Database
    participant Approval as 核准流程模組

    %% 1. 前端初始化
    User->>Frontend: 開啟新增風險頁面
    Frontend->>Backend: GET /api/isms/asset-categories
    Backend-->>Frontend: 回傳分類列表
    Frontend->>Backend: GET /api/isms/assets?category={category_id}
    Backend-->>Frontend: 回傳資產列表
    Frontend->>Backend: GET /api/isms/threats?asset={asset_id}
    Backend-->>Frontend: 回傳威脅列表
    Frontend->>Backend: GET /api/isms/vulnerabilities?asset={asset_id}
    Backend-->>Frontend: 回傳弱點列表

    %% 2. 發起風險新增請求
    User->>Frontend: 選擇資產並點「新增風險」
    Frontend->>Backend: POST /api/isms/risk/{asset_id}

    %% 3. 觸發核准流程（黑盒引用）
    Backend->>Approval: POST /api/system/approval  （建立風險核准請求）

    %% 4. 核准流程執行，完成後呼回
    Approval-->>Backend: approval_completed  （收到核准結果）

    %% 5. 核准完成後才計算並存回資料庫
    Backend->>Database: 取得 Asset Setting（公式與變數）
    Backend->>Database: 讀取 Asset/Threat/Vulnerability 資料
    Backend->>Backend: 套用公式計算風險值
    Backend->>Database: 儲存 Risk Result

    %% 6. 前端重新讀取結果
    Backend-->>Frontend: approval 回應（或空）
    Frontend->>Backend: GET /api/isms/risk/{asset_id}
    Backend-->>Frontend: 回傳最新 Risk Result
