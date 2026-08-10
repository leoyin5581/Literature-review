# Paper-reading

Mechanism, quantitative characterization, and inhibition of corrosion in lithium batteries
APL Energy，AIP Publishing。
論文題目：“Improved internal short circuit models for thermal runaway simulations in lithium-ion batteries”
作者：Bakhshish Preet Singh et al.
APL Energy, Vol. 3, 016102 (2025)
DOI：10.1063/5.0244329。

這篇就是我前面提到的模型來源。它把 ISC 分成幾種主要路徑，包括：

\text{Cathode–Anode}

\boxed{\text{Al–Anode}}

\text{Cu–Cathode}

另外也討論 Cu–Al current collector short。

其中非常值得你看的是 Figure 2。在其模型設定下：

R_{\text{Al-Anode}}\approx2.4\ \Omega

而：

R_{\text{Cu-Cathode}}\approx87\ \Omega

R_{\text{Cathode-Anode}}\approx95\ \Omega

因此 Al–Anode 路徑的 electrochemical heat-generation rate 約是其他兩類的 30–35 倍，模型中只有 Al–Anode ISC 觸發 thermal runaway。

這也是為什麼我前面一直強調：

\boxed{\text{Al current collector}\rightarrow\text{fully lithiated anode}}

對你們 100% Si 架構尤其值得單獨研究。

另外，這篇文章引用了一篇更早、直接針對 nail penetration 建模的經典文章，也很值得一起看：

Journal of The Electrochemical Society
W. Zhao, G. Luo, C.-Y. Wang,
“Modeling nail penetration process in large-format Li-ion cells”
J. Electrochem. Soc. 162, A207–A217 (2015)
DOI：10.1149/2.1071501jes。

還有一篇實驗＋模型直接研究 penetration-induced ISC：

Applied Thermal Engineering
J. Wang et al.,
“Experimental and numerical study on penetration-induced internal short-circuit of lithium-ion cell”
Applied Thermal Engineering 171, 115082 (2020)。

如果你現在的目的是研究你們的 Al foil / SUS / Ni–P-Al / dual ceramic separator 哪一種會改變穿刺 ISC，我會優先讀 APL Energy 2025 + JES 2015 這兩篇：前者回答「哪種接觸最危險」，後者回答「nail 穿進去時短路怎麼形成」。