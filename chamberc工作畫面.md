# Chamber C 工作畫面
![image](https://hackmd.io/_uploads/SkHUAVIVex.png)
這張截圖來自 **AMAT CENTURA 5200 系統的 Chamber C（製程腔體）監控畫面**，主要用於監控與控制該腔體的運作狀況，以下是各區塊的詳細說明：

---

## 🔷 顯示畫面基本資訊

* **左上角時間與系統名稱：**

  * 日期時間：`23-Jun-2025 10:25:34`
  * 機台型號：`AMAT CENTURA 5200`
  * 軟體版本：`E4.8.26`
  * 畫面編號：`030207`

* **上方區域：**

  * `System Wafer`：表示目前顯示為與wafer相關的系統畫面
  * `Ch B Ch C Ch E Ch F`：代表目前可監控的腔體通道，本畫面聚焦於 `Chamber C`
  * `Monitor Strip / Chamber C`：此為標題，表示目前是監控Chamber C的strip製程畫面

---

## 1. ⚙️ 左側流程區（VDS區與壓力控制）

* **VDS（Vacuum Distribution System）：**

  * `Status: Offline`：真空分配系統目前為離線狀態
  * `Heaters: OFF`：加熱器未啟動

* **壓力資訊：**

  * `Pressure: 0.107 Torr`：目前腔體壓力
  * `Offset: 0.00 Torr`：壓力偏差補償

* **泵浦與清洗：**

  * `PUMP ON`：代表真空幫浦開啟中
  * `Temp OK`：溫度正常
  * `PURGE OK`：清洗氣體狀態正常
  * `Over 10 Torr`：壓力超過10Torr的偵測標示

---

## 2. 🟡 中央區：Gas Box（氣體盒）與加熱燈控制

* **Process Gases**：製程氣體進入腔體（透過Gas Box控制）

* **Microwave Power**：Microwave 功率供應通道（目前連接至Gas Box）

* **Gas Box控制狀態：**

  * `Temp: 25.5°C`：氣體盒內部溫度
  * `Lamp: 2.0%`：燈源輸出百分比
  * `0% / 0A`：表示實際電流輸出為0（代表沒有燈管加熱）
  * `Temp OK`：溫度在正常範圍內

---

### ⚫ Throttle Valve（節流閥控制）

* `At Step 800`：節流閥當前位置
* `OPEN`：目前處於打開狀態

---



## 3. ⚫ 右上角：Microwave 功率與磁控控制（Mag Generator）

* `Mag Generator OFF`：磁控產生器未開啟

* `Mag Filament ON`：磁控燈絲已開

* `NOT READY`（黃色底）表示目前 **不具備開始製程的條件**

* **功率資訊：**

  * `Request: 0W`：要求輸出功率
  * `Forward: 0W`：實際輸出功率
  * `Reflected: 1023W`：反射功率極高，可能有匹配問題（反射表示未被有效吸收）

---
### 🔵 右下角：Wafer Lift（晶圓升降控制）

* `At Step: 0`：目前升降馬達在步驟0
* `At Home`：升降平台處於原點

---
## 📋 底部選單

* `Monitor Handler`：監控 wafer handler
* `Gas Panel`：氣體面板設定
* `Monitor Process`：製程監控畫面
* `Chamber Service`：腔體維護功能
* `Previous`：回上一頁

---

### ⚠️ 畫面整體狀態總結：

* 系統處於待機狀態，VDS offline，磁控未啟動，僅開啟燈絲（未READY），腔體加熱正常，壓力正常，晶圓升降平台未運動，尚未具備啟動製程條件。
