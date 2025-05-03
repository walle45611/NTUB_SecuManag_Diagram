sequenceDiagram
    actor ReviewerA as 核准者A
    participant Frontend
    participant Backend
    participant Database
    actor ReviewerB as 核准者B
    actor User as 發起者

    ReviewerA->>Frontend: 點選「通過」
    Frontend->>Backend: POST /api/system/approval/{approval_id}/user/{user_id}/approved
    Backend->>Database: UPDATE approval_record SET status='approved', approver='A'

    alt 還有下一位審核者
        Backend->>ReviewerB: 發送通知給 ReviewerB
    else 全部審核完成
        Backend->>Database: UPDATE approval_request SET status='approved'
        Backend->>Database: 核准過後將核准的相關文件歸檔並且向量化儲存到資料庫
        Backend->>Backend: 執行後續業務邏輯 (重新計算風險數值、調整使用者權限)
        Backend->>Database: 結束後續業務邏輯儲存到資料庫
    end
