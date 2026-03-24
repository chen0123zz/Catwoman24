# 🐱 貓系傲嬌女子 — 團購網站

內衣團購專用網站，支援 Google Drive 圖片、兩層規格（顏色→尺寸）。

## 📦 檔案一覽

| 檔案 | 說明 |
|------|------|
| `index.html` | 前台（客人下單）|
| `admin.html` | 後台（貓女管理用）|
| `google-apps-script.js` | 後端，貼到 Google Apps Script |

---

## 🚀 部署步驟

### Step 1 — 建立後端（Google Apps Script）

1. 開啟 [Google Sheets](https://sheets.google.com)，新增一份試算表
2. 上方選單：**擴充功能 → Apps Script**
3. 將 `google-apps-script.js` 全部內容貼上（取代原本的 `myFunction`）
4. 點選「**部署 → 新增部署作業**」
5. 類型選「**網頁應用程式**」
   - 執行身分：**我**
   - 誰可以存取：**所有人**
6. 按「部署」，複製產生的 **URL**

### Step 2 — 填入 GAS_URL

在 `index.html` 與 `admin.html` 兩個檔案中，找到這行並替換：

```js
const GAS_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL_HERE';
```

改成你的 URL：

```js
const GAS_URL = 'https://script.google.com/macros/s/你的ID/exec';
```

### Step 3 — 部署到 GitHub Pages

1. 在 GitHub 建立 **Public** repository
2. 上傳 `index.html` 和 `admin.html`
3. **Settings → Pages → Branch: main → Save**
4. 約 1 分鐘後即可訪問

---

## 🖼️ 圖片上傳方式（Google Drive）

1. 將商品圖片上傳到 Google Drive
2. 對圖片按右鍵 → **共用**
3. 存取權限改為「**知道連結的人都可以查看**」
4. 複製連結（格式：`https://drive.google.com/file/d/檔案ID/view`）
5. 在後台商品編輯中，貼入連結欄位 → 按「新增」

**每個顏色可上傳多張圖片**，客人點色票時會自動切換該顏色的圖組。

---

## 🎨 規格設定方式（後台操作）

1. 後台 → 商品管理 → 新增/編輯商品
2. 拉到「顏色規格」區塊
3. 點「新增顏色」→ 填入顏色名稱（如：霧玫瑰）、選取色碼
4. 展開顏色 → 貼入 Google Drive 圖片連結
5. 設定各尺寸名稱（S/M/L/XL 等）與庫存數量
6. 可新增多個顏色，每個顏色有獨立的圖片組和尺寸庫存

---

## 🔐 後台登入

- 預設帳號：`admin`
- 預設密碼：`admin123`
- 後台網址：`https://你的網址/admin.html`
- **上線後請立即至「設定」頁面修改密碼！**

---

## 📲 客人訂購流程

1. 選擇商品 → 點色票切換顏色（同步切換圖片）
2. 選尺寸 → 選數量 → 加入購物袋
3. 結帳時填寫姓名、手機、取貨方式
4. 選擇「傳送至 LINE」（自動帶入訂單跳轉貓女 LINE）或「複製文字」
5. 完成匯款後截圖傳給貓女確認

---

## ✅ 功能清單

**前台**
- [x] 高質感黑白設計（Cormorant Garamond 字型）
- [x] 商品卡片含顏色點預覽
- [x] 商品詳情 Modal（圖片輪播 + 縮圖列）
- [x] 色票點擊 → 即時切換圖片
- [x] 兩層規格：顏色 → 尺寸
- [x] 庫存 0 自動顯示售完/無法選擇
- [x] 購物袋 Drawer + 自動計價
- [x] 結帳表單 + 訂單摘要 + 匯款資訊
- [x] LINE 跳轉 + 複製文字兩種方式

**後台**
- [x] 帳密登入保護
- [x] 商品 CRUD（含顏色、圖片、尺寸）
- [x] 每個顏色獨立圖片組（貼 Drive 連結）
- [x] 尺寸庫存管理
- [x] 訂單管理（查看、篩選、更新狀態）
- [x] 設定（店名、截單日、匯款、LINE ID）
- [x] 資料存於 Google Sheets（免費）
