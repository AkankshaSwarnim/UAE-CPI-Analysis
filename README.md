# 🇦🇪 UAE Consumer Price Index — Deep Statistical Analysis

**MSc Data Science — University of Birmingham Dubai | March 2026**

A comprehensive analysis of UAE CPI data (2014–2025) covering 14 sectors, 5,500+ monthly records from the Federal Competitiveness & Statistics Centre (FCSA). Includes trend decomposition, unsupervised regime detection, Granger causality testing, and comparative analysis with Saudi Arabia and global economies.

---

## 📊 Key Findings

1. **Housing Dominates** — 35% of CPI basket, single-handedly drives both the 2019-20 deflation era AND current 2025 inflation
2. **VAT Shock was Transitory** — Jan 2018's +2.68% MoM spike (largest ever) fully reversed within 12 months
3. **24-Month Deflation Unique in GCC** — UAE deflated from Jan 2019–Dec 2020 due to property oversupply, not monetary failure
4. **Dollar Peg = Double-Edged Sword** — Imports disinflation on tradeables (Textiles −5%) but blocks independent monetary response
5. **Two-Speed Economy in 2025** — Housing/services at +3-4% while tradeable goods flat or deflating

## 📁 Project Structure

```
UAE-CPI-Analysis/
├── data/
│   ├── FCSA_DF_CPI_3_2_0_all.csv              # Monthly CPI (main dataset)
│   ├── FCSA_DF_CPI_ANN_3_2_0_all__2_.csv      # Annual CPI
│   ├── FCSA_DF_CPI_Q_3_2_0_all.csv            # Quarterly CPI
│   └── UAE_CPI_2022_Reconstructed.csv          # 2022 monthly data (reconstructed)
├── notebooks/
│   └── UAE_CPI_Statistical_Analysis.ipynb      # Main analysis notebook (17 code cells)
├── dashboards/
│   ├── uae_cpi_analysis.html                   # Overview dashboard (6 tabs)
│   └── uae_cpi_monthly_deep_analysis.html      # Monthly deep-dive dashboard (7 tabs)
├── presentation/
│   ├── UAE_CPI_FINAL_10min.pptx                # 10-minute presentation (8 slides)
│   └── FINAL_10min_Transcript.docx             # Speaker scripts for 4 presenters
├── outputs/                                     # Generated charts (created by notebook)
├── requirements.txt
├── LICENSE
└── README.md
```

## 🚀 Quick Start

### Option A: Run Locally

```bash
# 1. Clone the repository
git clone https://github.com/YOUR-USERNAME/UAE-CPI-Analysis.git
cd UAE-CPI-Analysis

# 2. Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # Mac/Linux
# venv\Scripts\activate         # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch Jupyter
jupyter notebook notebooks/UAE_CPI_Statistical_Analysis.ipynb
```

### Option B: Run on Google Colab

1. Go to [Google Colab](https://colab.research.google.com)
2. Click **File → Upload notebook** → select `UAE_CPI_Statistical_Analysis.ipynb`
3. Upload the 3 CSV files from the `data/` folder when prompted (or use the Colab code below)
4. Run all cells (**Runtime → Run all**)

```python
# If using Colab, upload files first:
from google.colab import files
uploaded = files.upload()  # Select the 3 CSV files
```

### Option C: View Dashboards Only (No Setup)

Just open the HTML files in any browser:
* [Overview Dashboard (6 interactive tabs)](https://akankshaswarnim.github.io/UAE-CPI-Analysis/dashboards/uae_cpi_analysis.html)
* [Monthly Deep Analysis (7 tabs)](https://akankshaswarnim.github.io/UAE-CPI-Analysis/dashboards/uae_cpi_monthly_deep_analysis.html)

No server, no installation needed. Works offline.

## 📓 Notebook Guide (Cell by Cell)

| Cell | Section | What It Does | Key Output |
|------|---------|-------------|------------|
| 1 | Setup | Imports libraries, sets dark plot theme | — |
| 2 | Data Loading | Loads 3 CSVs, filters to 2014+, creates division mapping | Data summary |
| 3 | 2022 Reconstruction | Fills the FCSA data gap by computing YoY from index levels | Validated: 4.82% matches FCSA |
| 4 | Data Preparation | Pivots data into analytical format (sector × time matrices) | Series objects for all analyses |
| 5 | CPI Overview Charts | Plots CPI Index + Annual Inflation with regime annotations | `01_cpi_overview.png` |
| 6 | Descriptive Statistics | Computes mean, std, skewness by era (boom, deflation, etc.) | Era comparison table |
| 7 | STL Decomposition | Separates trend, seasonal, residual components | `02_stl_decomposition.png` |
| 8 | Structural Breaks | Rolling mean ± 2σ with break annotations, volatility plot | `03_structural_breaks.png` |
| 9 | CUSUM | Cumulative sum test for regime identification | `04_cusum.png` |
| 10 | Sector Correlation | Cross-correlation heatmap across 14 sectors | `05_sector_correlation.png` |
| 11 | Granger Causality | Tests which sectors lead headline CPI (p<0.05) | Text output: Housing & Food lead |
| 12 | HDBSCAN Clustering | Groups months into inflation regimes unsupervised | Cluster profiles |
| 13 | UMAP Projection | 2D visualization of regime evolution over time | `06_umap_clusters.png` |
| 14 | Sector Volatility | Mean vs. std scatter, range ranking | `07_sector_volatility.png` |
| 15 | Cross-Correlation Lags | Identifies lead/lag relationships per sector | `08_cross_correlation_lags.png` |
| 16 | Sector Heatmap | Monthly × sector inflation heatmap (2021-2025) | `09_sector_heatmap.png` |
| 17 | Cumulative Index | Sector price trajectories since 2021 | `10_cumulative_sectors.png` |
| 18 | Critical Months | Identifies top 10 spikes/drops with sector decomposition | Text output |
| 19 | Seasonal Patterns | Average MoM by calendar month | `11_seasonal_pattern.png` |
| 20 | Housing 3-Era Comparison | Side-by-side: 2015 boom vs 2019 collapse vs 2025 recovery | `12_housing_three_eras.png` |
| 21 | 2025 V-Shape | Month-by-month headline + MoM for 2025 | `13_2025_v_shape.png` |

## 📊 Methods Used

| Method | Library | Purpose |
|--------|---------|---------|
| STL Decomposition | `statsmodels` | Separate trend/seasonal/residual |
| Granger Causality | `statsmodels` | Test if sector X predicts headline CPI |
| HDBSCAN | `hdbscan` | Unsupervised inflation regime detection |
| UMAP | `umap-learn` | Dimensionality reduction for regime visualization |
| Cross-Correlation | `scipy` | Identify lead/lag between sectors |
| CUSUM | `numpy` | Structural break detection |
| Z-score Profiling | `sklearn` | Standardized sector comparison |

## 📡 Data Sources

| Source | URL | Data |
|--------|-----|------|
| FCSA Open Data | [uaestat.fcsc.gov.ae](https://uaestat.fcsc.gov.ae) | Primary: UAE CPI monthly/annual/quarterly |
| CBUAE | [centralbank.ae](https://www.centralbank.ae) | Quarterly Economic Reviews, monetary policy |
| IMF WEO | [imf.org](https://www.imf.org/en/Publications/WEO) | Global inflation comparison |
| KAMCO Invest | [kamcoinvest.com](https://www.kamcoinvest.com) | GCC inflation reports |
| Saudi GASTAT | [stats.gov.sa](https://www.stats.gov.sa) | Saudi Arabia CPI for comparison |

## 📄 License

This project is for academic purposes. Data is from UAE government open data portals.

## 👥 Team

MSc Data Science, University of Birmingham Dubai — March 2026
