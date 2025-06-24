# Chamber B Service Screen
![image](https://hackmd.io/_uploads/B1ZIQ9DEge.png)
這張畫面是 AMAT Centura 5200 系統中 **Chamber B（製程腔體B）** 的 **Service Screen（維護畫面）**，用來進行設備維護、設定及測試操作。畫面上功能主要區分為數個區塊，以下是詳細說明：

---

## 🔷 畫面上方資訊欄

* **日期與時間**：`24-Jun-2025`，時間為 `9:47:58`
* **系統名稱**：`AMAT CENTURA 5200`
* **軟體版本**：`E4.3.26`
* **系統模式**：`System: Wafer`（系統目前處於晶圓製程模式）
* **程式模式**：`Program: Misc`（表示目前載入的是非標準製程程式）
* **目前顯示頁面**：`Etch Chamber B Service Screen`（蝕刻腔體B的維護畫面）

---

## 🔷 畫面中央藍色功能框：維護操作功能列表

此處是主要的操作區，提供了許多維護或手動控制功能，可大致分為以下幾類：

### ⚙️ 狀態切換

* `Put offline for maintenance`：將腔體設定為維護模式（無法進行製程）
* `Put online for process`：將腔體設定為可進行製程的狀態

### 🧪 腔體與真空控制

* `Start chamber pump down`：開始腔體抽真空
* `Start chamber vent`：開始腔體洩壓（通氣）
* `AFC Cal.`：自動壓力控制系統校正
* `Start rough pump down`：使用 rough pump 進行初步抽真空
* `Leak Up`：進行洩漏測試

### 🔄 製程相關功能

* `Abort Service Program`：中止目前的維護程序
* `Cycle purge`：執行氣體清洗循環
* `Hi-Pur Gas Cycle purge`：高純度氣體循環清洗

### ✅ 驗證與歸零

* `AFC flow verify`：壓力流量驗證
* `Dechuck wafer`：晶圓解除吸附
* `Process Manometer zero`：歸零製程壓力感測器
* `TGV learn to Servo`：將閥門學習後的設定送入伺服控制器
* `Service Program Sequence`：啟動特定維護程序流程
* `Service Manometer zero`：歸零維護壓力感測器

---

## 🔷 畫面下方功能鍵（灰色按鈕區）

* `Monitor Handler`：監控晶圓搬送機構
* `Monitor Gas Panel`：監控氣體面板參數
* `Monitor Chamber`：監控腔體狀態
* `Previous`：返回上一頁

---

## 🔷 左側真空閥資訊（Throttle Control）

* `Throttle Control` 狀態：目前為 **Home Throttle**
* `Step` 控制資訊表示正在執行的指令：

  * Stepper 位置、速度、分解度、目標 Step 值、Servo轉速等

---

## ✅ 總結

此畫面是用來在 AMAT Centura 5200 蝕刻系統的 Chamber B 上執行各種維護與檢查工作的控制介面。技術人員可藉此進行：

* 真空腔體操作（抽氣/洩壓）
* 系統校正（AFC, 壓力感測器）
* 洩漏測試、氣體清洗
* 控制設備是否可供製程（Online/Offline 切換）

