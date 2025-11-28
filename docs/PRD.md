# Wiwynn 訪客登記系統 PRD（Python + HTML + Supabase + Power Automate）

## 1. 系統目的

建立可透過 QR Code
使用的外網訪客登記系統，訪客可填寫資料、拍照、簽名並立即通知被訪人。\
名單來源每日透過 Python 排程從 HR API/CSV 同步到 Supabase，前端 HTML
即時查詢。

## 2. 系統組成

-   Python 後端（每日同步 HR → Supabase）
-   HTML + JavaScript 前端（訪客操作頁面）
-   Supabase（DB + Hosting）
-   Power Automate（Adaptive Card 通知）

## 3. 系統架構

    HR DB
       ↓ (API / CSV，由 Python 每日讀取)
    Python Script（排程）
       ↓ upsert
    Supabase employees
       ↓
    HTML 前端訪客系統（外網，可掃 QR Code）
       ↓ POST
    Supabase visitor_log
       ↓
    Power Automate（Adaptive Card 通知）
       ↓
    Teams（被訪人）

## 4. 前端功能

-   QR Code 開啟頁面
-   填寫姓名、公司、電話
-   拍照上傳（Base64）
-   簽名（Canvas）
-   搜尋員工（模糊搜尋 name/email）
-   規章閱讀 + 勾選同意
-   寫入 Supabase visitor_log

## 5. 後端功能（Python）

-   每日排程讀取 HR API 或 CSV
-   Upsert 至 Supabase employees
-   僅包含非敏感資料：name, email, department
-   使用 Supabase Python Client

## 6. Supabase DB Schema

### employees

-   name\
-   email\
-   department\
-   updated_at

### visitor_log

-   name\
-   phone\
-   company\
-   host_emails\
-   photo_base64\
-   signature_base64\
-   rule_agreed\
-   arrive_time\
-   notified

## 7. Power Automate

-   每分鐘檢查 visitor_log.notified = false
-   發 Teams Adaptive Card 給 host_emails
-   更新 notified = true

## 8. 安全性

-   RLS：employees 允許 SELECT，visitor_log 允許 INSERT
-   前端使用 anon key，後端同步使用 service role key
-   不涉及敏感人事資料

## 9. 流量

每日同步一次。\
訪客查詢僅查 Supabase，負載極低。

## 10. QR Code

QR Code 指向 Supabase Hosting 的 index.html：\
`https://xxxx.supabase.co/visitor/index.html`

## 11. 適用情境

-   外網訪客登記\
-   Teams 自動通知\
-   拍照、簽名、規章存證
