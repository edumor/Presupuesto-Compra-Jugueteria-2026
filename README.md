# 🧸 Toy Import Budget — Argentina Children's Day 2026

**Business Intelligence · Import Costing · Competitive Analysis · MercadoLibre**

> A full-cycle BI analysis to support wholesale import purchasing decisions ahead of Argentina's Children's Day (August 16, 2026). Built for MICROBELL S.A., a wholesale importer operating on MercadoLibre Argentina.

---

## 🔴 Live Demo

👉 **[View Interactive Report](https://edumor.github.io/Presupuesto-Importacion-Jugueteria-2026/Presupuesto_Importacion_Jugueteria_2026.html)**

> The report is fully interactive: competitive traffic lights, Chart.js visualizations, and a complete 30-item cost breakdown table with live MercadoLibre price comparisons.

---

## 📌 Problem Statement

Argentina's Children's Day is one of the highest-demand retail events of the year. Wholesale importers must place orders with Chinese manufacturers **4–5 months in advance** due to production lead times (30–45 days) and maritime transit (28–35 days).

This analysis answers three critical business questions:

1. **Which products are worth importing?** → Competitive analysis vs. MercadoLibre current prices
2. **What is the real landed cost?** → Full cost model: FOB China → Wholesale Price Argentina
3. **When is the deadline to order?** → Logistics calendar with risk scenarios

---

## 📊 Key Results

| Metric | Value |
|---|---|
| Products Analyzed | 30 |
| 🟢 Competitive (publish now) | 9 |
| 🟡 Marginal (renegotiate FOB) | 20 |
| 🔴 Not viable | 1 |
| Exchange Rate Used | 1 USD = $1,475 ARS |
| Import Duty (Decree 781/2025) | 20% (NCM 9503) |
| FOB → MeLi Multiplier | ×7.65 |
| Wholesale Margin | 45% |
| **⚡ Optimal Order Deadline** | **April 15, 2026** |

---

## 🧠 Methodology & BI Approach

### Data Sources
- **MercadoLibre Argentina** — current market prices for each product category (scraped reference prices, Mar–Aug 2025 period)
- **Nubimetrics** — sales volume estimates and category growth trends (Mar–Aug 2025)
- **Alibaba.com** — FOB reference prices from Chinese suppliers
- **AFIP / Argentine Customs** — duty rates and fiscal recovery rules (IVA, Gcias, IIBB)
- **Decree 781/2025** — reduced import duty (DIE) from 35% to 20% for NCM Chapter 9503 (toys), effective November 1, 2025

### Cost Model: FOB → MercadoLibre Price

```
FOB (China)
  × 1.07    → FOB Adjusted (market variance)
  + 13%     → Maritime Freight
  + 0.5%    → Marine Insurance
  ──────────────────────────────
  = CIF (Cost + Insurance + Freight)

CIF
  + 20%     → Import Duty (DIE, Decree 781/2025)
  + 10.5%   → IVA Importación     ← RECOVERABLE
  + 3%      → IVA Percepción      ← RECOVERABLE
  + 3%      → Gcias Percepción    ← RECOVERABLE
  + 3%      → IIBB (avg)          ← RECOVERABLE
  ──────────────────────────────
  = Valor Depósito (Landed Cost)

Valor Depósito
  × 1.35    → Operating Cost Factor (+35% logistics, storage, admin)
  ──────────────────────────────
  = Costo Mercadería

Costo Mercadería
  × 1.45    → Wholesale Price (+45% margin)
  × 1.80    → MercadoLibre Price (MeLi fees + VAT)
  ──────────────────────────────
  = MeLi List Price → Total Multiplier: ×7.65 over FOB
```

### Competitive Traffic Light System

Each product is classified by comparing the calculated MeLi price against current market prices:

| Signal | Condition | Action |
|---|---|---|
| 🟢 GREEN | Own price ≤ Market price | Publish immediately |
| 🟡 YELLOW | Own price 0–25% above market | Renegotiate FOB or reduce margin |
| 🔴 RED | Own price >25% above market | Drop or redesign |

---

## 📦 Top Categories Analyzed

| Category | MeLi Growth (Mar–Aug 2025) | Est. Units Sold |
|---|---|---|
| Construction Blocks | +95% | ~7,200 |
| Plush Toys (Labubu, Baby Shark) | +79% | ~10,900 |
| Board Games | +63% | ~9,300 |
| Consoles / Gaming | +41% | ~5,800 |
| Kids' Bicycles | +38% | ~8,900 |
| Dolls & Action Figures | +35% | ~10,200 |
| RC / Electronic Toys | +29% | ~6,700 |
| Outdoor / Sports | +25% | ~12,400 |

*Sources: MercadoLibre best sellers · Nubimetrics · ElCronista · Perfil*

---

## 📅 Logistics Calendar

```
Mar 31 ─── Apr 7-14 ─── Apr 21-28 ─── May ─── Jun 1-10 ─── Jul 10-15 ─── Jul 16-31 ─── Aug 1-10 ─── Aug 16
  │              │              │         │          │              │              │              │           │
Analysis    Contact         Confirm    China     Shipment       Arrival       Customs      Distribute   CHILDREN'S
Decision    Suppliers       Orders    Prod 30d   Shanghai      Buenos Aires   Clearance    + MeLi        DAY 🎉
```

| Scenario | Production | Transit | Order Deadline | Risk |
|---|---|---|---|---|
| 🟢 Optimal | 30 days | 28 days | **April 15, 2026** | LOW |
| 🟡 Tight | 40 days | 32 days | April 30, 2026 | MEDIUM |
| 🔴 Critical | 45+ days | 35+ days | After May 1, 2026 | HIGH |

---

## 🛠 Tools & Technologies

- **Business Intelligence**: Manual BI methodology — cross-referencing MeLi, Nubimetrics & Alibaba data
- **Visualization**: [Chart.js](https://www.chartjs.org/) — bar charts, donut charts, grouped comparisons
- **Presentation**: Microsoft PowerPoint (executive deck, 9 slides)
- **Web Report**: Vanilla HTML5 + CSS3 + Chart.js (single self-contained file, no backend)
- **Regulatory Reference**: NCM Chapter 9503 · AFIP · Decree 781/2025

---

## 📁 Repository Structure

```
Presupuesto-Importacion-Jugueteria-2026/
│
├── Presupuesto_Importacion_Jugueteria_2026.html   # Interactive web report (live demo)
├── Presupuesto_Importacion_Jugueteria_2026.pptx   # Executive PowerPoint deck (9 slides)
└── README.md                                       # This file
```

---

## 🔑 Strategic Recommendations

1. **Publish the 9 GREEN products immediately** — Auto RC, Mini Drone, Labubu & Baby Shark plush, Dinosaur sets, Bicycles and Slide are price-competitive. Minimum 200 units stock to sustain MeLi GOLD level.

2. **Renegotiate FOB on YELLOW items >18%** — Robot (+14.8%), STEM Set (+18.1%), Water Slide (+11.7%), Skateboard (+22.9%) require a 10–15% FOB reduction or margin adjustment from 45% to 35%.

3. **Drop or replace the RED item** — Hopper Ball (+32%) is not viable unless FOB ≤ USD 2.50. Recommended replacement: Bubble Gun + Paint Set combo (better FOB/price ratio).

4. **Leverage recoverable taxes** — Excluding recoverable duties (IVA + Gcias + IIBB) from the cost base reduces the FOB→MeLi multiplier from ×7.65 to ×5.52, turning 12 YELLOW items into GREEN.

5. **Consolidate shipment** — LCL or 20ft FCL container prioritizing compact, high-value items (blocks, plush, figures) for optimal freight/value ratio.

---

## 👤 Author

**Eduardo Moreno**
Systems Engineer · Business Intelligence · Wholesale Import

📧 eduardomoreno2503@gmail.com
🔗 [LinkedIn](www.linkedin.com/in/eduardo-moreno-15813b19b) 
🏢 MICROBELL S.A. — Wholesale Importer, Argentina

---

## ⚠️ Disclaimer

FOB prices are reference estimates based on Alibaba listings and should be verified directly with suppliers before placing orders. MercadoLibre prices reflect the Mar–Aug 2025 period and may vary. Exchange rate: 1 USD = $1,475 ARS (March 31, 2026).

---

*Report date: March 31, 2026 · Children's Day: August 16, 2026*