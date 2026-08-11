# 📄 APL Energy (2025) 論文研讀筆記

## 🏷️ 一、標題與摘要

- **標題**：Quantifying Layer-to-Layer Internal Short Circuit Risks in Lithium-Ion Batteries Using a Current Modulation Method
- **作者**：Xinjian Liu, Yashuang Zhang, Xiang Feng, Yubo Zhang, Minggao Ouyang, Andrew F. Bower
- **期刊**：APL Energy, 2025

### 📌 摘要重點

- **背景**：內部短路（ISC）是鋰離子電池熱失控（TR）的主要誘因之一，但精確量化不同層間 ISC 的風險仍具挑戰性。
- **方法**：開發一種電流調變（current modulation）方法，利用 ISC pad 技術在 pouch cell 中製造可控 ISC，並透過即時電流與電壓監測量化 ISC 風險。
- **結果**：針對四種 ISC 類型（Al-Anode、Al-Cu、Cathode-Anode、Cathode-Cu）進行系統性測試，Al-Anode ISC 最為嚴重，peak ISC 電流達 ~120 A；CA 相關組別因正極材料導電性差，電流顯著降低。
- **結論**：電流調變方法可有效量化層間 ISC 風險，並驗證了發熱的高度侷限性，為電池安全設計提供定量依據。

---

## 📚 二、研究背景

### 2.1 引言

- 🔋 鋰離子電池廣泛應用於電動車、儲能系統與消費性電子產品，但熱失控（thermal runaway, TR）仍是其最嚴重安全隱患。
- ⚡ 內部短路（internal short circuit, ISC）是觸發 TR 的最常見機制之一，可由製造缺陷、機械濫用（針刺、擠壓）、枝晶生長或隔膜老化引起。
- ❗ 實際 ISC 具有隨機性與不可控性，使得實驗研究困難重重。

### 2.2 文獻回顧

| 研究方向 | 代表工作 | 關鍵發現 |
| :--- | :--- | :--- |
| 🔩 機械觸發 ISC | Feng et al., Ren et al. | 針刺與擠壓測試中 ISC 電流與短路電阻的統計分佈 |
| 🎯 可控 ISC 方法 | Compressor-triggered ISC, Fuse wire ISC | 利用外部觸發機制模擬 ISC，但再現性有限 |
| 🧩 ISC Pad 技術 | Liu et al. (本文前作) | 在 pouch cell 中嵌入 Cu/Al pad，可精確控制 ISC 位置與類型 |
| 💻 數值模擬 | P2D model, EC model | 模擬 ISC 後電流分佈與溫升，但缺乏實驗驗證 |
| 🔄 電流調變概念 | 本文首次提出 | 透過即時監測 ISC 電流與電壓，量化各層間 ISC 風險 |

### 2.3 Knowledge Gap

- 🔍 缺乏系統性方法區分不同層間（正極-負極、正極-Cu、Al-負極、Al-Cu）ISC 的相對風險。
- 📉 現有 ISC 測試方法再現性不足，難以進行統計性風險評估。
- ⚙️ ISC 電阻難以直接量測，導致產熱量計算不精確。
- 🔗 缺乏將 ISC 電流調變與實際 TR 觸發條件連結的定量框架。

### 2.4 研究目的

- 🎯 開發電流調變（current modulation）方法，系統性量化四種層間 ISC 的風險。
- 🧪 利用 ISC pad 技術實現高再現性的可控 ISC 實驗。
- 📐 透過能量積分法 $E_{ec} = \int I_{ISC} \times U_0 \, dt$ 迴避 ISC 電阻量測困難。
- ✅ 驗證 ISC 發熱的高度侷限性，為電池安全設計提供實驗依據。

---

## 🔬 三、實驗方法

### 3.1 ISC Pad Method

- **原理**：將一對 Cu pad 與 Al pad 嵌入電芯內部，透過外部開關與電流感測器連接。閉合開關後，電子從負極經 Cu pad → 開關 → 電流感測器 → Al pad 流向正極，同時鋰離子穿過隔膜，模擬真實 ISC 行為。
- **四種 ISC 類型**：可透過移除正極塗層、負極塗層或兩者皆移除，創建 Al-Anode、Al-Cu、Cathode-Anode、Cathode-Cu 四種 ISC。
- **參數量測**：
    - 🌡️ **ISC 溫度 ($T_{ISC}$)**：K-type 微型熱電偶（40 AWG, Omega Engineering）嵌入 Cu/Al pad 之間
    - ⚡ **ISC 電流 ($I_{ISC}$)**：直接由電流感測器量測
    - 📏 **ISC 電阻 ($R_{NE}, R_{PE}$)**：量測 cell tab 與 pad 之間的電壓降除以 $I_{ISC}$
    - 🔥 **ISC 產熱率**：$I^2_{ISC} \times (R_{NE} + R_{PE})$

#### 銅鋁箔規格

| 項目 | 規格 |
| :--- | :--- |
| 🟤 Al pad | 8 mm 寬 × 0.09 mm 厚（PLiB-ATC8, MTI Corporation） |
| 🟠 Cu pad | 8 mm 寬 × 0.15 mm 厚（Amazon） |
| ⚙️ Shunt resistor | 0.75 mΩ（SHD1-100C075DE, Ohmite） |
| 🔌 Relay switch | LEV200A4ANA, Tyco |
| 🎗️ Kapton tape | 0.5 mm 厚，貼於 ISC 區域確保穩定接觸 |
| ✂️ Pad 邊角處理 | 圓角處理，避免刺穿隔膜或電極 |

### 3.2 電芯準備方法

| 參數 | 規格 |
| :--- | :--- |
| 📦 電芯格式 | Pouch format, 4 Ah（Li-FUN Technologies, model 7651A0） |
| ➕ 正極材料 | NMC811（14.7 mg/cm², 95.5% 活性材料） |
| ➖ 負極材料 | Artificial graphite（9.5 mg/cm², 95.7% 活性材料） |
| 📏 正極塗層厚度 | 44 μm / 面（雙面塗佈） |
| 📏 負極塗層厚度 | 66 μm / 面（雙面塗佈） |
| 🔢 正極層數 | 22 層（雙面塗佈） |
| 🔢 負極層數 | 23 層（雙面塗佈） |
| 🟠 銅箔厚度 | 8 μm |
| 🟤 鋁箔厚度 | 12 μm |
| 🧱 隔膜 | PE 基材 9 μm + 陶瓷塗層 3 μm = 總厚 12 μm |
| 📐 負極尺寸 | 88 mm × 47 mm |
| 📐 正極尺寸 | 85 mm × 44 mm |
| 🏷️ Tab 規格 | 12 mm 寬 × 0.25 mm 厚 |
| 💧 電解液 | 1 M LiPF₆ in EC:EMC = 3:7 (v/v)（MTI Corporation） |
| ⚖️ 注液量 | 12 g |
| 🏋️ 電芯總質量 | ~76 g |
| 🔧 壓縮條件 | 兩片陶瓷纖維絕緣片（1.6 mm）+ 6061 鋁合金板（6.4 mm），4 顆螺栓各鎖 2 Nm，壓縮力 ~1200 N |

### 3.3 化成與 ISC 測試程序

- 🔋 **化成**：1.5 V 靜置 12 h → C/20 充放電 1 圈（4.2 V max / 2.8 V min）→ C/10 充放電 2 圈 → C/3、1C、2C 性能驗證（1C = 4 A）。
- ⚡ **ISC 測試前充電**：CCCV 協議，4 A 恆流至 4.2 V，再 4.2 V 恆壓至電流降至 0.02 A，室溫 23±2°C。
- 🔄 **Current modulation**：當電壓降至 <4.0 V 時啟動外部放電（由 Arbin LBT21084 電池測試儀執行）。
- ⚡ **External short circuit（ESC）**：由 relay switch 觸發，外部短路總電阻 ~6 mΩ（HIOKI 3561 量測）。
- 📊 **數據擷取**：Keysight 34980A，5 Hz 採樣頻率；所有測試在安全箱（MSK-TE905, MTI）內進行。

### 3.4 電芯拆解與 SEM 觀察

- 🔍 對經歷 120 A current modulation 的 Al-Anode ISC 電芯進行事後分析。
- 🧤 電芯完全放電後於氬氣手套箱中拆解，取出隔膜樣品。
- 🧴 隔膜以 DMC（99%, Thermo Scientific）清洗三次並乾燥。
- 🆕 新鮮乾電池隔膜作為對照組。
- 🔬 **SEM 設備**：Thermo Scientific™ Apreo（University of Alabama Core Analytical Facility）。
- 📸 樣品鍍金處理後進行成像（200×, 2,000×, 20,000×）。
- 💡 **關鍵發現**：ISC 側隔膜孔隙消失（PE 熔融 shutdown），正極側因陶瓷塗層保護無明顯收縮，支持「均勻加熱 + 隔膜安全 shutdown」機制假說。

---

## 📊 四、實驗結果與討論

### 4.1 Al-Anode ISC 再現性驗證

- 🎯 **選擇依據**：根據先前文獻，Al-Anode ISC 為最嚴重的內部短路類型，因此優先針對此組進行重複測試。
- 🔁 **重複次數**：3 次，驗證方法的高度一致性與可再現性。
- 📏 **量測方式**：
    - ⚡ ISC 電流 ($I_{ISC}$) 與電壓 ($U$)：實驗過程中直接量測
    - 📐 ISC 電阻 ($R_{ISC}$)：由 $V / I$ 計算獲得
- 📈 **能量計算**：
    - 公式：$E_{ec} = \int_{0}^{t_{TR}} I_{ISC} \times U_0 \, dt$
    - 此方法避免了焦耳熱 $I^2R$ 中 ISC 電阻難以直接量測的問題
- 🌡️ **溫升估算**：
    - 根據釋放能量換算，整顆電芯溫升僅約 48°C
    - 遠低於電芯熱失控觸發溫度
- ✅ **關鍵結論**：發熱具有高度的侷限性（highly localized），未擴散至整個電芯

### 4.2 其餘 ISC 組別測試結果

| ISC 類型 | Peak $I_{ISC}$ (A) | $R_{NE}$ (mΩ) | $R_{PE}$ (mΩ) | 特徵說明 |
| :--- | :--- | :--- | :--- | :--- |
| 🔴 Al-Anode | ~120 | ~0.7 | ~0.5 | 最嚴重；3次重複驗證高度再現 |
| 🟠 Al-Cu | ~95 | ~0.8 | ~0.6 | 無活性材料參與，純金屬接觸 |
| 🟡 Cathode-Anode | ~45 | ~3.5 | ~2.8 | CA 為不良導體，電流顯著降低 |
| 🟢 Cathode-Cu | ~30 | ~5.2 | ~4.1 | 雙側皆含非良導體，電阻最高、電流最低 |

#### 🔑 CA 相關組別（Cathode-Anode、Cathode-Cu）的關鍵差異

- 正極活性材料（NMC811）本身電子導電性差，構成額外的串聯電阻。
- 導致 ISC 電流大幅低於純金屬接觸組別（Al-Anode、Al-Cu）。
- $R_{NE}$ 與 $R_{PE}$ 均明顯偏高，反映電流路徑中包含了活性材料層的體電阻與界面接觸電阻。
- 產熱率 ($I^2R$) 雖因電阻升高而單點溫度可能較高，但總能量釋放遠低於 Al-Anode 組別。

> 📊 **四種 ISC 風險排序**：Al-Anode > Al-Cu > Cathode-Anode > Cathode-Cu

🔗 **與 current modulation 的關聯**：不同 ISC 類型的初始電流與電阻差異，直接決定了所需調變電流的門檻值與響應時間，這也是後續量化各層間 ISC 風險的基礎。

---

## 📝 五、待補充章節

- [ ] ⚙️ Current modulation 詳細機制與參數設定
- [ ] 📈 各組別電流調變響應曲線比較
- [ ] 🧮 能量積分與溫升模型驗證
- [ ] 🔬 SEM 微觀分析結果詳述
- [ ] 💡 結論與工程應用建議

---

🕒 **文件生成時間**：2026-08-11  
📎 **來源**：APL Energy (2025), APL Energy (2025).pdf
