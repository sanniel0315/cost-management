# cost-management
# 專案成本查詢系統設計解釋

## 1. 整體結構
專案遵循 Vue 框架的標準設計模式，代碼分為多個模組化目錄，便於維護和擴展。

---

## 2. 目錄詳解

### (1) `assets`
- **用途**：存放靜態資源（如圖片）。
- **內容**：
  - `background-image.jpg`：背景圖片。
  - `office.jpg`, `spot.jpg`：用於網頁展示或圖表輔助資源。

### (2) `components`
- **用途**：存放可重複使用的 Vue 元件。
- **內容**：
  - **`charts`**：專門用於數據圖表顯示的元件：
    - `LineChart.vue`：折線圖。
    - `PieChart.vue`：圓餅圖。
  - **`Comparison.vue`**：比較數據集的元件。
  - **`CostReport.vue`**：成本報告元件。
  - **`ItemForm.vue`**：用於新增或編輯項目資料的表單。
  - **`ItemTable.vue`**：展示數據的表格元件。

### (3) `router`
- **用途**：管理應用的路由設定。
- **檔案**：
  - `index.js`：定義各路徑（如 `/home`, `/login`）及其對應視圖。

### (4) `services`
- **用途**：與後端 API 互動的邏輯。
- **檔案**：
  - `api.js`：包含 API 請求，例如獲取數據、提交表單。

### (5) `stores`
- **用途**：狀態管理（Vuex 或 Pinia）。
- **檔案**：
  - `searchStore.js`：管理搜尋相關的狀態，例如查詢條件和結果。

### (6) `types`
- **用途**：定義 TypeScript 型別。
- **狀態**：目前目錄尚未使用，但可擴展。

### (7) `utils`
- **用途**：通用工具函式。
- **檔案**：
  - `helpers.js`：包含日期格式化、數據處理等通用函式。

### (8) `views`
- **用途**：主要頁面視圖。
- **內容**：
  - `Dashboard.vue`：儀表板頁面，展示核心數據摘要。
  - `Home.vue`：主頁，包含搜尋功能和結果顯示。
  - `Login.vue`：登錄頁面，用於身份驗證。
  - `NavBar.vue`：導航欄，包含頁面切換與用戶功能。
  - `ReportTable.vue`：報表數據顯示。
  - `Toast.vue`：彈出式提示通知元件。
  - `upload.vue`：檔案上傳功能頁面。

### (9) 根目錄
- **配置檔案**：
  - `.env` 系列檔案：不同環境的設定檔案。
  - `tailwind.config.js`：Tailwind CSS 配置。
  - `vite.config.js`：Vite 開發工具設定。

---

## 3. 設計特點

1. **模組化設計**
   - 各功能分成獨立元件，便於測試與重用。

2. **清晰的目錄結構**
   - 視圖 (`views`) 和元件 (`components`) 分離，增強可讀性。
   - 靜態資源統一放置在 `assets`。

3. **響應式設計**
   - 使用 Tailwind CSS，確保樣式的一致性與響應性。

4. **高可維護性**
   - `services` 和 `utils` 目錄分離了邏輯層與工具層。

5. **多功能支援**
   - 圖表、表單、表格共同構成數據操作的核心功能。
   - 提示通知 (`Toast.vue`) 提升用戶體驗。

---

## 4. 優化建議

1. **目錄細分**
   - 將視圖與功能性元件進一步細分，例如：
     - 為資料處理功能新增專用目錄。

2. **擴展功能**
   - 添加錯誤處理元件（如 ErrorBoundary）。
   - 在 `api.js` 中實現 API 請求的錯誤重試機制。

3. **完善文件**
   - 補充 `README.md`，詳細說明專案功能與安裝步驟。

4. **強化代碼註解**
   - 在 `utils` 與 `api.js` 增加詳細註解，提升後續維護效率。

## 流程說明

* 進入頁面**
    → 檢查認證 
    → 載入專案列表 
    → 顯示歡迎訊息
* 輸入搜索條件** 
    → 驗證輸入 
    → 執行搜索 
    → 顯示結果/錯誤
* 開啟專案選擇
    → 載入專案列表 
    → 選擇專案 
    → 確認選擇 
    → 執行相關搜索
* 錯誤處理:
    →統一的錯誤處理邏輯
    →Toast 通知系統
    →載入狀態管理

## 專案結構說明
project/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   └── views/
├── backend/
│   ├── api/
│   └── models/
└── database/
## 功能模塊
*  總覽分析
   ├── 總案件數
   ├── 總金額統計
   ├── 廠商分析
   
* 趨勢分析
   ├── 月度費用趨勢
   ├── 採購/契約比較
   └── 項目數量變化
* 廠商分析
   ├── 廠商分布
   ├── 金額佔比
   └── 子系統覆蓋
* 項目追蹤
   ├── 最近更新
   ├── 狀態分布
   └── 重要指標
   
## 響應式設計
--即時數據更新
--交互式圖表

## 數據安全：

--權限控制
--數據驗證
--錯誤處理

## 性能優化：

--使用索引優化查詢
--資料緩存機制
# 資料庫
![image](https://hackmd.io/_uploads/Sy04MJiMJl.png)
---
id	project_name	category	sub_category	description	unit	quantity	unit_price	total_price	type	code	created_at	updated_at	created_by	updated_by	sheet_name	vendor	vendor2	order_quantity	purchase_unit_price	purchase_total_price	item_number	auxiliary_item	unique_id	project_date
---

111	(v2301)	工程建置	纜線材料	纜線材料	NULL	NULL	NULL	NULL	NULL	NULL	2024-11-02 11:19:17.523	2024-11-02 11:19:17.523	NULL	NULL	國5112	NULL	NULL	NULL	NULL	NULL	壹.一.3	67	A6A317FB-DDF5-8D24-2F3F-1A632DD1A816	NULL
---
### 完整的數據流程是：

**/點擊專案列表按鈕/** 
→ showProjectList
  呼叫 fetchProjectNames 獲取數據
  數據獲取成功後顯示在模態框中
  用戶選擇專案後觸發 selectProject
  發出選擇事件並關閉模態框
  
1.  // 專案列表相關的狀態
const projectList = ref([])  // 存儲專案列表數據
const loadingProjects = ref(false)  // 載入狀態
const lastProjectUpdate = ref(null)  // 最後更新時間


2. // 獲取專案列表數據
const fetchProjectNames = async () => {
  loadingProjects.value = true
  try {
    const response = await getProjectNamesWithRetry()
    if (response.projects === 'success') { 
      projectList.value = response.projects || []
      lastProjectUpdate.value = new Date()
    } else {
      throw new Error('獲取專案列表失敗')
    }
  } catch (error) {
    console.error('Failed to fetch projects:', error)
    showToast('獲取專案列表失敗', 'error')
  } finally {
    loadingProjects.value = false
  }
}

3.專案選擇流程：
javascriptCopy// 選擇專案
const selectProject = (project) => {
  emit('select-project', project)
  closeProjectModal()
  showToast("已選擇專案:${project},'successfully'}")  
}

// 關閉專案模態框
const closeProjectModal = () => {
  emit('update:showProjectModal', false)
}

4.API 調用：
javascriptCopyimport { getProjectNamesWithRetry } from '@/services/api'

----搜尋專案流程
Navbar.vue (觸發)
   ↓
1. 點擊專案列表
2. 打開 Modal
3. 獲取專案列表
4. 選擇專案
   ↓
App.vue (中轉)
   ↓
1. 接收選中的專案
2. 更新 selectedProject
3. 導航到首頁
   ↓
Home.vue (處理)
   ↓
1. 接收 selectedProject
2. 更新搜索參數
3. 執行搜索
4. 顯示結果
## 報表項次
項次 類別 案件 子系統 項目及說明 單位 契約數量 契約單價 契約複價 廠商 下單數量 採購單價 採購複價 型號或料號

## 所有驗證 token 的邏輯
統一使用 services/api.js 中的 validateToken 函數。
