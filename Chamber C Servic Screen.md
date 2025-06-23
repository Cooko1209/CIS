# Chamber C Servic Screen
![image](https://hackmd.io/_uploads/S1_kESUNex.png)

這是 **AMAT CENTURA 5200 – Chamber C 的維護畫面（Service Screen）**，主要提供技術人員進行節流閥（Throttle Valve）與晶圓升降平台（Stripper Lift）的手動校準與狀態監控。以下是各區塊的詳細介紹：

---

## 1. 🔧 Throttle Control（節流閥控制）

### 📌 當前狀態

* **At Step 800 / Request Step 800**：目前節流閥位置為 800，且請求值也是 800（表示位置達成）
* **Closed at step 0 / Hysteresis 8.0**：節流閥關閉位置為 0，開關遲滯值為 8 step
* **Sense：NOT CLOSED / OPEN**：感測狀態為未關閉/開啟，可能表示節流閥處於中間位置或未正確校準

### 📌 指令區

* `Request：Home Throttle`：歸零節流閥
* `Calibrate Throttle`：進行校準動作
* `Close Throttle / Open Throttle`：手動開關節流閥
* `Go to step`、`Close by`、`Open by`：以步進方式控制節流閥微調

### 📌 其他參數

* **Servo：0.000T**：伺服控制參數，通常用於微調壓力
* **Pressure：0.102 Torr**：目前腔體內部壓力

---

## 2. 💡 Lamps（燈源控制）

* **Servo to 0°C**（控制關閉） / **目前 25.5°C**
* **Set to 0%** / **目前為 2%**：燈源輸出為 2%

---

## 3. ➕ Stepper : Throttle / Flags 狀態（左下角）

### **Stepper : Throttle 控制參數：**

  * First Rate：3（初始速率）
  * Run Rate：7（運轉速率）
  * Slope：1（斜率）
  * Divisor：1（除數）
  *
    ---
    以下是針對 AMAT 系統中 **Stepper 區塊的四個參數（First Rate、Run Rate、Slope、Divisor）** 的詳細說明，這些參數控制的是「節流閥（Throttle Valve）步進馬達」的移動特性，特別是速度與加速行為。

    ---

    🔧 Stepper 控制參數說明：

    | 參數名稱               | 說明 |
    | ------------------ | -- |
    | **1️⃣ First Rate** |   初始速度（Initial Speed）
    * 指的是節流閥剛啟動移動時的**起始速率**（step/sec）
    * 數值越大，啟動越快，但若設太高可能導致啟動失步（miss step）
    * **畫面數值：3 → 代表啟動較緩和** 



    ---

    | 參數名稱         | 說明                      |
    | ---------------- | ------------------------- |
    | **2️⃣ Run Rate** | 運行速度（Running Speed） |


    * 當節流閥加速到穩定後，會以此速度持續移動（step/sec）
    * 越大表示移動越快，適合較大範圍移動，但穩定性要好
    * **畫面數值：7 → 表示中等偏快的穩定速度**

    ---

    | 參數名稱          | 說明 |
    | ------------- | -- |
    | **3️⃣ Slope** |  加速/減速斜率（Acceleration Slope）  |
    * 表示從 First Rate 過渡到 Run Rate 所需的速率變化階段，數值越大表示加速越慢（更平順）
    * 常用於防止劇烈啟動或過快停止造成精度錯誤
    * **畫面數值：1 → 表示加速/減速變化比較快（斜率低 = 快速達速）**

    ---

    | 參數名稱            | 說明 |
    | --------------- | -- |
    | **4️⃣ Divisor** | 控制細分步距（Step Divider）   |

    * 用來細分步進馬達的步距，數值越大，代表越細緻控制，但速度會變慢
    * 例如：Divisor = 2 時，每個實際步距會分成兩個邏輯步驟執行
    * **畫面數值：1 → 表示沒有細分（等於原始步距），即一般速度與精度設定**


    ---
    🔁 總結舉例：

    假設系統要從位置 A 移動到位置 B，控制流程大致如下：

    1. 以 First Rate（速度 = 3）啟動
    2. 根據 Slope（1）加速至 Run Rate（速度 = 7）
    3. 過程中每步為原始大小（Divisor = 1），不做細分
    4. 停止時根據相同斜率逐步減速回到靜止

    ---


###  **Flags：**
 Home / Upper / Lower flags：
 **Flags:** 的數值：

| 項目        | 數值  | 含義說明                                |
| --------- | --- | ----------------------------------- |
   | **Home**  | `1` | 節流閥目前位於「Home 歸零位置」，此標誌已觸發（1 = True） |
| **Upper** | `0` | 尚未達到節流閥的「上限位置」                      |
| **Lower** | `0` | 尚未達到「下限位置」                          |

📌 總結：

**Flags 中的 Home 對應的數值為 `1`**，代表目前節流閥已經處於其「歸零參考位置（Home Position）」。



---

## 4. 🔵 Chamber Control（腔體控制）

### 📌 系統狀態

* **OFFLINE FOR MAINTENANCE**：腔體目前處於維護離線狀態
* **Time Elapsed：0:00:00**：維護時間尚未啟動
* **Rate of Rise：0.00 mT/min**：壓力上升速率為 0
* **Backing：48 mTorr**：背壓值
* **Chamber：0.102 Torr**：腔體內壓

---

## 5. 🔧 Stripper Lift（晶圓升降平台）說明

### 📌 當前位置與請求位置

* **Currently：RELEASE**：目前處於 Wafer Release 狀態
* **Lift：-2.499 mm** / **Request：-2.5 mm**：升降位置幾乎達成
### 📌 動作指令

以下是針對 **Stripper Lift（晶圓升降平台）** 的重新整理與重點說明，結合畫面資訊與實際設備功能，幫助你清楚掌握其運作原理與使用方式。


#### 一、功能簡介

Stripper Lift 是晶圓於製程腔體中垂直移動的機構，負責在以下幾個階段將晶圓抬升或下降至指定位置：

* **接收晶圓（Release Position）**
* **抬升暫存（Lift Position）**
* **執行製程（Process Position）**
* **釋放晶圓（回到 Release）**

#### 二、操作指令（共 4 個）

畫面中提供了 4 個藍色控制按鈕，對應的功能如下：

| 動作指令                     | 功能說明                                                     |
| ------------------------ | -------------------------------------------------------- |
| **1️⃣ Home Lift**        | 將升降平台歸零，回到機械原點位置，常用於開機初始化與校準。                            |
| **2️⃣ Wafer to Lift**    | 將晶圓升至「Lift Position」，即中間高度，用於暫存、對位或等待。                   |
| **3️⃣ Wafer to Process** | 將晶圓升至「Process Position」，這是製程執行位置，靠近反應區（如 RF 或 Plasma 區）。 |
| **4️⃣ Wafer to Release** | 將晶圓降至「Release Position」，方便機械手臂放入或取出晶圓。                   |

---

#### 三、對應位置設定值（畫面右下角）

| 位置項目                       | 對應值（mm）  | 說明                          |
| -------------------------- | -------- | --------------------------- |
| **Lift wafer position**    | `-2.5`   | 中間位置，供對位或暫存之用               |
| **Process Position 1**     | `-8.5`   | 第一組製程高度                     |
| **Process Position 2**     | `-8.5`   | 第二組製程高度（目前與1相同，可調整）         |
| **Release Position**       | `-4.582` | 放入/取出晶圓的高度                  |
| **Wafer to Release 1 / 2** | `8.5`    | 可調整的備用釋放高度（實際位置視 recipe 使用） |

---

#### 四、移動參數設定

這些參數控制升降時的速度與平順度：

| 參數名稱                | 值   | 說明             |
| ------------------- | --- | -------------- |
| **Hi Acceleration** | `8` | 快速移動時的加速度      |
| **Lo Acceleration** | `8` | 慢速時的加速度（較穩定）   |
| **Hi Velocity**     | `5` | 正常快速運行速度       |
| **Lo Velocity**     | `5` | 慢速移動速度，常用於精準位置 |

---

#### 五、典型升降流程

```
1. Home Lift （初始化）
2. Wafer to Release（接收 wafer）
3. Wafer to Lift（升到中間位置）
4. Wafer to Process（進行製程）
5. Wafer to Release（下降等待取出）
```

---

#### 六、使用建議

| 使用時機     | 建議指令             |
| -------- | ---------------- |
| 開機校正     | Home Lift        |
| 製程開始前預定位 | Wafer to Lift    |
| 製程執行     | Wafer to Process |
| 製程完成準備卸片 | Wafer to Release |

---

### 📍 位置與動作參數（右下角）

* **Wafer to release 1 / 2：8.5 mm**

* **Wafer to process 1 / 2：-5.5 mm**

* **Lift wafer position：-2.5 mm**

* **Process Position 1 / 2：-8.5 mm**

* **Release Position：-4.582 mm**

* **Lift Acceleration / Deceleration：8 / 5**

* **Hi Velocity / Lo Velocity：5 / 3**

這些數值主要是定義晶圓在製程中的各個上下運動位置與速度參數。

---

## 6. 📌 底部功能鍵

* `Monitor Handler`：檢視晶圓搬運模組
* `Monitor Gas Panel`：查看氣體面板
* `Monitor Chamber`：腔體狀態
* `Previous`：返回上一畫面

---

## ✅ 總結：

此畫面提供維護工程師進行 **Chamber C 的手動維修與校正操作**，可調整：

* Throttle Valve 位置與校準
* Wafer 升降位置、速度與控制參數
* 觀察溫度與壓力是否在正常範圍內
