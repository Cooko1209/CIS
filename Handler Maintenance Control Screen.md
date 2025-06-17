# 3. Handler Maintenance Control Screen（維護控制畫面）

![image](https://hackmd.io/_uploads/H1j-jZd7el.png)

圖來自 AMAT Centura 5200 系統，畫面標題為：

---

## 🔷 **Handler Maintenance Control Screen（維護控制畫面）**

這個畫面主要是用來監控及維護 **Load Lock A/B、Buffer Chamber、Purge 系統** 的真空與氣體狀態，是機台操作人員常用來確認設備狀況是否符合進片條件的介面。

---

### 🖥️ 畫面結構與狀態介紹：

---

### 【1】Load Lock A（左上）

* **狀態：OFFLINE FOR MAI**（維護中）
* **CHAM PUMPED DOWN**：已抽真空完成
* **R/R**：Robot Ready = `0 mT/m`（未執行抽氣）
* **LLA**：真空壓力為 `166 mTorr`（表示尚未達製程真空等級）
* **Slit：Closed**（閘門關閉）
* **DOOR：Closed**（外門也關閉）

🔴 結論：目前 Load Lock A 被設定為離線維護（MAI），不會參與製程流程。

---

### 【2】Load Lock B（右上）

* **狀態：ONLINE FOR PROC**（製程中）
* **CHAM PUMPED DOWN**：已抽真空完成
* **LLB**：真空壓力為 `23 mTorr`（抽氣完成，接近製程壓力）
* **Slit：Closed**、**DOOR：Closed**

🟢 結論：Load Lock B 處於製程待機狀態，可進行 wafer 傳送。

---

### 【3】Buffer Chamber（中間）

* **狀態：ONLINE FOR PROC**
* **Service：idle**（服務閒置，未執行 wafer 傳送）
* **Conv.（Conveyor 壓力）**：`26 mTorr`（維持穩定真空）

🟡 結論：Buffer Chamber 處於製程連線中但無動作。

---

### 【4】Purge MFC（中下）

* **目標流量（Sp）：0 sccm** → 未設定流量
* **實際流量（Is）：2 sccm** → 有微量流量進入
* **氣體來源：N2**

⚠️ 有微量 N2 流入，可能是作為 idle 時的保護氣體流通。

---

### 【5】BUF PUMP（右下）& SYS PUMP（左下）

* **BUF PUMP：ONLINE / ON**
* **SYS PUMP：ONLINE / ON**

✅ 表示抽氣系統正常工作，整體壓力控制穩定。

---

## 🔍 總結設備狀態：

| 模組          | 狀態說明                             |
| ----------- | -------------------------------- |
| Load Lock A | 離線維護（OFFLINE FOR MAI），已抽氣但壓力偏高   |
| Load Lock B | 在線備用（ONLINE FOR PROC），準備載入 wafer |
| Buffer      | 在線，維持抽氣穩定但無動作                    |
| N2 Purge    | 輕微流入氣體，做為環境保護                    |
| 抽氣系統        | 正常運作中，顯示為 ONLINE                 |

---

