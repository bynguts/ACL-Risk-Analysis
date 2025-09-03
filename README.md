# ACL-Risk-Analysis

# Capstone Project: Analisis Risiko Cedera ACL pada Atlet Perguruan Tinggi

## Deskripsi
Proyek ini menganalisis risiko cedera ACL pada atlet perguruan tinggi menggunakan dataset [collegiate_athlete_injury_dataset.csv](raw/collegiate_athlete_injury_dataset.csv) (200 entri). Dengan IBM Granite untuk insight, Plotly untuk visualisasi interaktif, dan Pandas/Seaborn untuk analisis, proyek ini memberikan rekomendasi berbasis AI untuk mencegah cedera ACL.

## Struktur Repository
- **Root**: 
  - [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb): Notebook utama dengan kode analisis.
- **/raw/**:
  - [collegiate_athlete_injury_dataset.csv](raw/collegiate_athlete_injury_dataset.csv): Data cidera ACL pada atlet Perguruan Tinggi.
- **/docs/**:
  - [insights_summary.txt](docs/insights_summary.txt): Ringkasan insight dan rekomendasi.
- **/visualizations/**:
  - [Distribusi Usia](visualizations/acl_age_distribution_enhanced.png)
  - [Proporsi Risiko](visualizations/acl_risk_proportion.png)
  - [Intensitas Latihan](visualizations/acl_risk_training.png)
  - [Korelasi Faktor](visualizations/acl_correlation_heatmap.png)
  - [Posisi Atlet](visualizations/acl_risk_position_boxplot.png)
  - [Frekuensi Pertandingan](visualizations/acl_risk_match_count.png)
  - [Kontribusi Tim](visualizations/acl_team_contribution.png)
  - [Scatter Plot Interaktif](visualizations/acl_risk_training_interactive.html)

## Insight & Findings
- Rata-rata usia berisiko: 22 tahun.
- 60% perempuan penyerang berisiko tinggi.
- Korelasi Training_Intensity: 0.65.
- Lebih dari 2 pertandingan/minggu meningkatkan risiko.
- Rest_Between_Events_Days <2 tingkatkan risiko.
- Risiko tinggi turunkan Team_Contribution_Score.

## Recommendations
- Program latihan AI quadriceps 3x/minggu untuk usia 20-25 tahun (kurangi risiko 57%).
- Wearable AI untuk pantau Training_Intensity penyerang.
- Screening MRI 6 bulan untuk perempuan penyerang.
- AI scheduling: Batasi 2 pertandingan/minggu, 3 hari istirahat.
- Protokol pemulihan 3 hari istirahat antar event.
- Sistem pencegahan terintegrasi untuk penyerang.

## Tools
- IBM Granite untuk analisis insight.
- Plotly untuk visualisasi interaktif.
- Pandas, Seaborn, Matplotlib untuk analisis dan visualisasi.

## Cara Menjalankan
1. Clone repository: git clone https://github.com/bynguts/ACL-Risk-Analysis.git
2. Buka notebook di Colab: [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb))
3. Lihat visualisasi interaktif: [acl_risk_training_interactive.html](visualizations/acl_risk_training_interactive.html)
