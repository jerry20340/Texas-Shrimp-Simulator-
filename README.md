# 🦐 Texas Shrimp Simulator (2014 Edition) | 德州養蝦模擬器

![Category](https://img.shields.io/badge/Category-Simulation-emerald)
![Tech](https://img.shields.io/badge/Tech-HTML5%20%2F%20JS%20%2F%20MapLibre-blue)
![Data](https://img.shields.io/badge/Data%20Source-Port%20Mansfield%2C%20TX-orange)

這是一個基於真實地理數據與經濟模型開發的互動式模擬系統。本專案模擬了 2014 年美國德州 **Port Mansfield** 養蝦場的運作，整合了極端氣候風險模型、邊境勞動力政策影響以及精確的財務盈虧分析。

## 🌟 核心功能

### 1. 氣候風險評估模型 (Climate Risk Assessment)
* **寒流衝擊 (Winter Kill)**：系統模擬了德州灣岸的氣候特性，精確反映 12 月至 3 月期間北方寒流導致的 100% 產量損耗風險。
* **季節性生產曲線**：模擬 6 月至 9 月最佳水溫下的高效能生產模型。

### 2. 動態經濟與政策參數
* **勞動力動態模擬**：設有「邊境政策」開關，模擬邊境管制對墨西哥技術勞工（Foreman）供應的影響，並自動調整人工成本與產能分配。
* **即時財務分析**：包含 ROI 計算、淨利預估（USD/TWD 雙幣制顯示），並針對 13 個獨立蝦池（總計約 131.5 英畝）進行細節計算。

### 3. GIS 地理資訊整合
* 使用 **MapLibre GL** 渲染即時衛星地圖。
* 透過波多邊形（Polygons）標記 13 座真實存在的蝦池，實現空間數據與生產數據的視覺化連動。

## 🛠 技術架構
* **Frontend**: 原生 JavaScript (ES6+), HTML5, CSS3。
* **Mapping**: MapLibre GL JS / Esri World Imagery (衛星影像)。
* **Typography**: 採用 `Bebas Neue` 與 `IBM Plex Mono` 營造專業儀表板質感。

## 🚀 快速開始
1. 將此專案 Clone 到本地環境：
   ```bash
   git clone [https://github.com/](https://github.com/)[YOUR_USERNAME]/texas-shrimp-simulator.git
