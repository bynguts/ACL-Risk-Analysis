# ACL-Risk-Analysis

# Capstone Project: Analisis Risiko Cedera ACL pada Atlet Perguruan Tinggi

## Project Overview
Proyek ini bertujuan untuk menganalisis risiko cedera Anterior Cruciate Ligament (ACL) pada atlet perguruan tinggi menggunakan dataset `collegiate_athlete_injury_dataset.csv` yang berisi 200 entri. Motivasi pribadi saya berasal dari pengalaman pribadi mengalami cedera ACL, yang meninggalkan trauma emosional, rasa marah, dan ketakutan untuk kembali bermain basket bahkan olahraga secara keseluruhan. Pengalaman ini mendorong saya untuk mengembangkan solusi data-driven guna mengurangi resiko atlet lain menghadapi tantangan serupa. Pendekatan yang digunakan melibatkan IBM Granite untuk menggali insight dari 10 *queries* kuantitatif, diikuti oleh visualisasi data dengan Pandas, Seaborn, dan Plotly (termasuk 1 plot interaktif HTML). Hasilnya disusun dalam `insights_summary.txt` dengan 6 rekomendasi berbasis AI.

## Raw Dataset
- Raw dataset: [collegiate_athlete_injury_dataset.csv](raw/collegiate_athlete_injury_dataset.csv)
- Sumber: Disediakan oleh Kaggle https://www.kaggle.com/datasets/ziya07/athlete-injury-and-performance-dataset
- Deskripsi: Dataset berisi 200 entri dengan kolom seperti `ACL_Risk_Score`, `Age`, `Gender`, `Position`, `Training_Intensity`, dll., digunakan untuk mengidentifikasi faktor risiko ACL.

## Insight & Findings
- Rata-rata usia atlet berisiko tinggi: 21 tahun.
- 51% atlet perempuan di posisi guard memiliki risiko ACL tinggi.
- Korelasi antara `Training_Intensity` dan `ACL_Risk_Score`: 0.36, menunjukkan intensitas latihan signifikan.
- Atlet dengan lebih dari 2 pertandingan per minggu memiliki risiko lebih tinggi.
- `Rest_Between_Events_Days` kurang dari 2 hari meningkatkan risiko cedera.
- Risiko ACL tinggi berkorelasi dengan penurunan `Team_Contribution_Score`.
- Visualisasi pendukung: [Distribusi Usia](visualizations/acl_age_distribution_enhanced.png), [Scatter Plot Interaktif](visualizations/acl_risk_training_interactive.html), dll. (lihat [visualizations](visualizations)).
- Detail lengkap: [insights_summary.txt](docs/insights_summary.txt)

## AI Support Explanation
Proyek ini memanfaatkan IBM Granite, model AI berbasis LLM, yang diintegrasikan melalui Google Colab untuk mendukung analisis. Granite digunakan untuk:
- **Classification**: Mengelompokkan atlet berisiko tinggi berdasarkan `ACL_Risk_Score` (misalnya, filter `df[df['ACL_Risk_Score'] > df['ACL_Risk_Score'].quantile(0.75)]`).
- **Summarization**: Menyusun 10 *queries* menjadi insight kuantitatif (misalnya, `df.groupby(['Gender', 'Position'])['ACL_Risk_Score'].mean()`).
- **Analisis Data**: Membantu menghasilkan kode untuk visualisasi (Seaborn untuk heatmap, Plotly untuk scatter interaktif). Proses ini dijalankan di notebook [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb), yang mencakup langkah-langkah analisis lengkap.

## Struktur Repository
- **Root**: [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb): Notebook utama dengan kode analisis.
- **/docs/**: [insights_summary.txt](docs/insights_summary.txt): Ringkasan insight dan rekomendasi.
- **/visualizations/**:
  - [Distribusi Usia](visualizations/acl_age_distribution_enhanced.png)
  - [Proporsi Risiko](visualizations/acl_risk_proportion.png)
  - [Intensitas Latihan](visualizations/acl_risk_training.png)
  - [Korelasi Faktor](visualizations/acl_correlation_heatmap.png)
  - [Posisi Atlet](visualizations/acl_risk_position_boxplot.png)
  - [Frekuensi Pertandingan](visualizations/acl_risk_match_count.png)
  - [Kontribusi Tim](visualizations/acl_team_contribution.png)
  - [Scatter Plot Interaktif](visualizations/acl_risk_training_interactive.html)
- **/raw/**: [collegiate_athlete_injury_dataset.csv](raw/collegiate_athlete_injury_dataset.csv): Dataset mentah.

## Recommendations
- Program latihan AI quadriceps 3x/minggu untuk usia 20-25 tahun (kurangi risiko 57%, hemat $50,000 per kasus).
- Wearable AI untuk memantau `Training_Intensity` pada penyerang.
- Screening MRI setiap 6 bulan untuk perempuan penyerang (60% berisiko).
- AI scheduling: Batasi 2 pertandingan/minggu dengan 3 hari istirahat.
- Protokol pemulihan dengan 3 hari istirahat antar event.
- Sistem pencegahan terintegrasi berbasis AI untuk penyerang.

## How to Run
1. Clone repository: `git clone https://github.com/bynguts/ACL-Risk-Analysis.git`
2. Buka notebook di Colab: [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb)
3. Lihat visualisasi interaktif: [acl_risk_training_interactive.html](visualizations/acl_risk_training_interactive.html)
