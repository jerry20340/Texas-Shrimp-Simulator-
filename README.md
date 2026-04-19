# Texas Shrimp Simulator v2 (Advanced Model Consolidation)

**德州養蝦模擬器 v2 · 七檔數據合併模型版**

![Version](https://img.shields.io/badge/version-2.0.0-3ddc6e?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-Web_Application-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Production_Ready-gold?style=for-the-badge)

## 📌 項目概述
**Texas Shrimp Simulator v2** 是一款基於真實地緣氣候數據與生物物理參數開發的高精度養殖經濟模型。本工具專為德州 Port Mansfield 地區的野生白蝦（*Litopenaeus vannamei*）養殖規劃設計，旨在透過整合多維度 JSON 數據集，提供比第一代更具精確度的動態決策支持。

## 🚀 從 v1 到 v2：核心演進與專業差異

相較於第一代 v1 偏向「概算」的邏輯，v2 進行了底層架構的技術升級，實現了**數據參數化**與**物理量化**：

### 1. 數據架構：從「固定成本」轉向「動態連動」
* **v1 (Simplified)**：採用固定成本上限模型（例如單池固定 $40,500），電力與飼料僅能以固定比例概算。
* **v2 (Data-Driven)**：完全捨棄固定值，改由七檔核心 JSON 驅動所有變量：
    * **`O2CUS40.json`**: 模擬不同生長期的生物氧氣需求（Biomass O2 Demand）。
    * **`Waterwheel.json`**: 嚴格計算 3HP 水車在物理環境下的補氧效能（48.07 kg/day/台）。
    * **`Eat_FCR40.json`**: 採用三階段飼料配比，並以 **FCR 1.85** 進行非線性成本推算。
    * **`Shrimp_life40.json`**: 引進動態存活與重量模型。

### 2. 生物物理模型：精準計算補氧與能源
* **動態溶解氧 (DO) 分析**：v2 會實時計算「自然曝氣補充（29.14 kg/day）」與「蝦隻呼吸需求」的差額。當用戶調整產量目標時，系統會自動算出需增加的水車台數及其產生的**邊際電費增加量**，而非 v1 的固定比例分配。
* **差異化分析 (Delta Analysis)**：新增實時增量面板，對比當前產量與基準（20,000 lbs）在氧氣峰值、水車台數、飼料費及每磅成本（Cost per Pound）的位移變化。

### 3. 人力成本模型：邊界政策動態模擬
* **地緣政治情境模擬**：v2 首創「邊界關閉（Border Closed）」切換機制：
    * **開放模式**：使用墨西哥籍勞動組合，確保成本最優。
    * **關閉模式**：模擬墨西哥工人短缺，系統自動將勞力切換為本地高薪人力（White Local Labor），並計算單季單池 **+$1,820** 的成本增益與收蝦費變動。

---

## 🛠 技術規格與物理常數

| 參數分類 | 核心數據 / 公式基準 | 備註 |
| :--- | :--- | :--- |
| **養殖規模** | 13 Ponds / 10 Acres per Pond | 均一化物理體積模型 |
| **水體容積** | 60,702,846 Liters | 基於 1.5m 平均水深計算 |
| **氧氣轉移** | 0.033 mg/L/hr per 3HP Unit | 基於水車效能實驗數據 |
| **電力費率** | 0.0458 USD/kWh | 基於 2026 預測費率 |
| **FCR 模型** | 1.85 (Economic Level) | 三階段動態成本攤提 |
| **地圖系統** | MapLibre GL JS + Esri Satellite | 整合 Port Mansfield 實測經緯度 |

---

## 📊 功能模組

### 🗺 蝦池空間分析 (Pond Spatial Tab)
整合 GIS 技術，可視化 13 個蝦池的精確邊界，並提供每池均一化後的生產潛力預估。

### 📊 季度獲利模型 (Analysis Tab)
整合德州季節性氣候風險，將「黃金季」、「風險季」、「寒流季」的損失率量化，並支持多生產週期（Cycles）的年度利潤累加計算。

### 💧 溶氧物理分析 (O2 Analysis Tab) - **v2 核心進化**
實時監控 Day 1–90 的生物量增長與氧氣需求曲線，提供水車供需平衡分析與「安全餘裕」警告，防止因密度過高導致的毀滅性風險。

---

## 📝 開發者說明
本模擬器前端採用純原生 JavaScript/CSS 撰寫，確保最高運算效率。數據交互邏輯嚴格遵循底層 JSON 物理參數庫，排除隨機經驗誤差。

> *此模擬器僅供學術研究與養殖規劃參考，實際產出受環境變量（如極端天氣、病害）影響可能有所變動。*

---
**Texas Shrimp Simulator v2** - *Engineering the Future of Aquaculture Management.*
