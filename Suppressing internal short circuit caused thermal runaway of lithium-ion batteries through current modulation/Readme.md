# 鋰電池內短路（ISC）模型與穿刺研究文獻整理

## 1. ISC 主要路徑分類
根據前述模型來源，內部短路（ISC）可分為以下幾種主要路徑：

- **Cathode–Anode**（正極–負極）
- **Al–Anode**（鋁集流體–負極）
- **Cu–Cathode**（銅集流體–正極）

> ⚠️ 文中另討論了 **Cu–Al current collector short**（銅鋁集流體短路）之情形。

---

## 2. 關鍵數據與熱失控分析（Figure 2）

在該模型的設定條件下，各路徑電阻值如下：

| ISC 路徑 | 電阻值 ($R$) |
| :--- | :--- |
| $\text{Al-Anode}$ | $\approx 2.4\ \Omega$ |
| $\text{Cu-Cathode}$ | $\approx 87\ \Omega$ |
| $\text{Cathode-Anode}$ | $\approx 95\ \Omega$ |

### 🔥 熱生成與觸發風險
- **Al–Anode** 路徑的電化學熱生成速率（electrochemical heat-generation rate）約為其他兩類路徑的 **30–35 倍**。
- 在模型中，**僅有 Al–Anode ISC 會觸發熱失控（Thermal Runaway）**。

### 💡 針對 100% Si 架構的研究建議
基於上述結果，以下接觸組合對 100% Si 負極架構尤其值得單獨深入研究：

$$
\boxed{\text{Al current collector} \rightarrow \text{fully lithiated anode}}
$$

---

## 3. 重要參考文獻

### 經典釘刺建模文獻
> W. Zhao, G. Luo, C.-Y. Wang, "Modeling nail penetration process in large-format Li-ion cells," *Journal of The Electrochemical Society*, vol. 162, pp. A207–A217, 2015.
> - **DOI:** [10.1149/2.1071501jes](https://doi.org/10.1149/2.1071501jes)
> - **重點：** 直接針對 nail penetration 進行建模的經典文章。

### 穿刺誘發 ISC 實驗與數值研究
> J. Wang et al., "Experimental and numerical study on penetration-induced internal short-circuit of lithium-ion cell," *Applied Thermal Engineering*, vol. 171, 115082, 2020.
> - **重點：** 結合實驗與模型，直接研究 penetration-induced ISC。

---

## 4. 閱讀優先級建議

若研究目標為探討 **Al foil / SUS / Ni–P-Al / dual ceramic separator** 何者會改變穿刺 ISC 行為，建議優先閱讀以下兩篇：

| 優先級 | 文獻 | 核心問題 |
| :--- | :--- | :--- |
| ⭐⭐⭐ | APL Energy (2025) | 回答「哪種接觸最危險」 |
| ⭐⭐⭐ | JES (Zhao et al., 2015) | 回答「nail 穿入時短路如何形成」 |
| ⭐⭐ | Applied Thermal Eng. (Wang et al., 2020) | 實驗＋模型驗證穿刺 ISC |
