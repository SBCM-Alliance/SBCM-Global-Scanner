# 🗺️ JAPAN DISTORTION MAP
**3D Volumetric Efficiency Auditor.**

[![Status](https://img.shields.io/badge/System-Operational-success)]()
[![Data](https://img.shields.io/badge/Data-OpenFreeMap-blue)](https://openfreemap.org/)
[![Tech](https://img.shields.io/badge/Tech-MapLibre_GL_JS-yellow)](https://maplibre.org/)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

> **「平らな地図（2D）では、都市の『稼ぐ力』は見えない。」**
>
> 地方自治体の財政破綻は、インフラの「平面的な拡散（スプロール）」と、建物の「垂直的な密度（高さ）」の不均衡によって引き起こされます。
> このツールは、全世界のオープンデータ（Vector Tiles）をリアルタイムで3D化し、**都市の「体積（Volume）」と「維持コスト」のバランス**を可視化する行政鑑識システムです。

---

## 📱 Demo

**👉 [Launch Global Scanner](https://sbcm-alliance.github.io/distortion-map/)**
*(PC / Smartphone Browser)*

| デモ (柏市) | 
| :---: | 
| <img src="images/demo_kashiwa.jpg" width="300"> |

---

## 📐 The Logic (SBCM Field Theory)

本システムは、SBCM理論 Part 4 (Field Theory) に基づき、都市を「面積」ではなく**「体積と密度の場」**として解析します。

### 1. Revenue Visualization (建物の高さ)
土地単位面積あたりの「納税力（収益性）」を、建物の高さから推定し色分けします。

| Color | Height | Status | Meaning |
| :--- | :--- | :--- | :--- |
| <span style="color:#00ffff">■</span> **CYAN** | **> 30m** | **HIGH (Excellent)** | **高層・高密度。** インフラ単価あたりの住民・テナント数が多く、黒字を生む「富のポンプ」。 |
| <span style="color:#00ff41">■</span> **GREEN** | **> 10m** | **MID (Efficient)** | **中層・適正。** 3階建て以上のビルやマンション。都市として持続可能な密度。 |
| <span style="color:#ff0055">■</span> **RED** | **< 10m** | **LOW (Sprawl)** | **低層・拡散。** 2階建て以下の住宅。道路延長に対して納税者が少なく、インフラ維持が赤字になりやすい領域。 |

### 2. Cost Visualization (インフラの動脈)
<span style="color:#0088ff">**― BLUE LINE**</span>
国道・県道などの主要道路を「青く発光するライン」として描画します。これが行政が維持し続けなければならない**「固定費のネットワーク」**です。

**判定:** 「青い線（コスト）」に対して「青・緑の箱（収益）」が十分に張り付いているか？ それとも「赤い箱」しかないか？ その比率が都市の余命を決定します。

---

## 🛠️ Features

### 1. Global Scope (OpenFreeMap)
データソースを日本限定のPLATEAUから、全世界対応の **OpenFreeMap (OSM Vector Tiles)** に切り替えました。
これにより、東京の路地裏からニューヨークの摩天楼、アフリカの地方都市まで、**地球上すべての都市を同一基準で監査可能**になりました。

### 2. Layer Injection Technology
地図のデザインデータ（Style JSON）に依存せず、プログラムが強制的に**「監査用3Dレイヤー」**を地図システムに注入（Inject）します。
これにより、データさえ存在すれば、どのような場所でも確実に3D化して表示させます。

### 3. Serverless & High Performance
**MapLibre GL JS** を採用し、スマホのGPUを使ってブラウザ内で高速レンダリングします。
重厚な3Dモデル（gltf）を使わず、ベクトルデータをその場で「引き伸ばす（Extrude）」処理を行うため、驚異的な軽さを実現しています。

---

## 🚀 Usage

### For Users
アクセスするだけで使用可能です。インストール不要。
検索ボックスに都市名（例: `Kashiwa`, `Manhattan`, `Paris`）を入力して GO を押してください。

### For Developers (Local Run)
```bash
# Clone repository
git clone https://github.com/SBCM-Alliance/distortion-map.git

# Run via Python simple server (CORS回避のため)
cd distortion-map
python3 -m http.server

# Open http://localhost:8000
```

---

## ⚠️ Data Attribution

- Map Data: © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright)
- Vector Tiles: [OpenFreeMap](https://openfreemap.org/)
- Rendering: MapLibre GL JS

---
<p align="center">
  <small>© 2025 SBCM Alliance. Powered by <b>Administrative Hydraulics</b>.</small>
</p>
```
