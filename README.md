# 🗺️ JAPAN DISTORTION MAP
**Infrastructure Efficiency Auditor.**

[![Status](https://img.shields.io/badge/System-Operational-success)]()
[![Data](https://img.shields.io/badge/Data-OpenStreetMap-green)](https://www.openstreetmap.org)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

> **「行政の帳簿（決算書）は嘘をつけるが、物理（地図）は嘘をつかない。」**
>
> 日本の地方自治体は「隠れ肥満（スプロール）」により破綻の危機に瀕しています。
> このツールは、OpenStreetMap (OSM) の衛星・GPSデータをリアルタイムで解析し、その街が抱える**「インフラ維持の重さ」**を可視化する監査システムです。

---

## 📱 Demo

**👉 [Launch Distortion Map](https://sbcm-alliance.github.io/distortion-map/)**
*(PC / Smartphone Browser)*

|デモ(柏市)|
|:---:|
|![](images/demo_kashiwa.jpg)|
---

## 📐 The Logic (SBCM Audit v3.0)

このシステムは、SBCM理論に基づき**「都市の密度効率」**を以下の式で算出します。

$$ \text{Burden Score} = \frac{\text{Total Road Length (m)}}{\text{Real Intersections (Nodes)}} $$

*   **分子 (Cost):** 維持管理が必要な道路の総延長。
*   **分母 (Value):** 人間の経済活動の結節点（交差点）。
*   **意味:** 「1つの交差点を維持するために、何メートルの道路を背負わされているか？」

### 🚦 Verdict Criteria (判定基準)

半径3km圏内のスキャン結果に基づき、以下の3段階で判定します。

| Score (m/node) | Status | Meaning |
| :--- | :--- | :--- |
| **< 130m** | 🟢 **SUSTAINABLE** | **高効率。** 豊島区や大阪市など。車なしで生活できるコンパクトシティ。 |
| **130m - 200m** | 🟡 **WARNING** | **注意。** 郊外型スプロール現象の兆候。維持費が税収を圧迫し始めている。 |
| **> 200m** | 🔴 **CRITICAL** | **維持困難。** 夕張市や限界集落。インフラの更新ができず、物理的崩壊が確定している。 |

---

## 🛠️ Features

### 1. Serverless & Real-time
バックエンドサーバーを持たず、ブラウザから直接 **Overpass API (OSM Database)** を叩きます。
これにより、行政によるデータの隠蔽や改ざんが不可能な「生の物理データ」を取得します。

### 2. 3x3 Keypad Interface
文字入力の手間を省くため、日本の都市構造の「松竹梅（成功と失敗）」を代表する9都市をプリセット。
ワンタップで監査を実行できます。

### 3. Strict Intersection Logic
単なるノード数ではなく、「2本以上の道路が接続する点」のみを交差点としてカウント。
田舎の「曲がりくねった一本道」を正しく「非効率」として検出する厳格なロジックを実装しています。

---

## 🚀 Usage

### For Users
アクセスするだけで使用可能です。インストール不要。
[https://sbcm-alliance.github.io/distortion-map/](https://sbcm-alliance.github.io/distortion-map/)

### For Developers (Local Run)
```bash
# Clone repository
git clone https://github.com/SBCM-Alliance/distortion-map.git

# Run via Python simple server (to avoid CORS issues)
cd distortion-map
python3 -m http.server

# Open http://localhost:8000
```

---

## ⚠️ Data Attribution

This tool uses data provided by **OpenStreetMap contributors**.
- Data © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright)
- Data is available under the Open Database License.

---
<p align="center">
  <small>© 2025 SBCM Alliance. Powered by Algorithmic Public Interestism.</small>
</p>
