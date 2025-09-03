# ACL-Risk-Analysis

# Capstone Project: Analisis Risiko Cedera ACL pada Atlet Perguruan Tinggi

## Project Overview
Proyek ini bertujuan untuk menganalisis risiko cedera Anterior Cruciate Ligament (ACL) pada atlet perguruan tinggi menggunakan dataset `collegiate_athlete_injury_dataset.csv` yang berisi 200 entri. Motivasi pribadi saya berasal dari pengalaman cedera ACL, yang meninggalkan trauma emosional, rasa marah, dan ketakutan untuk kembali bermain basket atau olahraga lainnya. Permasalahan spesifiknya adalah tingginya risiko cedera ACL akibat faktor seperti intensitas latihan dan jadwal pertandingan, yang sering diabaikan oleh atlet perguruan tinggi. Pengalaman ini mendorong saya untuk mengembangkan solusi data-driven guna mengurangi risiko atlet lain menghadapi tantangan serupa. Pendekatan ini menggunakan IBM Granite untuk menggali 10 insight kuantitatif, diikuti visualisasi dengan Pandas, Seaborn, dan Plotly (termasuk plot interaktif HTML), dengan hasil disusun dalam `insights_summary.txt` beserta 6 rekomendasi berbasis AI.

## Raw Dataset
- Raw dataset: [collegiate_athlete_injury_dataset.csv](raw/collegiate_athlete_injury_dataset.csv)
- Sumber: Disediakan oleh Kaggle https://www.kaggle.com/datasets/ziya07/athlete-injury-and-performance-dataset
- Deskripsi: Dataset berisi 200 entri dengan kolom seperti `ACL_Risk_Score`, `Age`, `Gender`, `Position`, `Training_Intensity`, dll., digunakan untuk mengidentifikasi faktor risiko ACL.

## Insight & Findings
- Rata-rata usia atlet berisiko tinggi: 21 tahun, menunjukkan kelompok usia muda sebagai fokus pencegahan.
- 51% atlet laki-laki di posisi guard memiliki risiko ACL tinggi: Segmentasi gender dan posisi ini menggarisbawahi kerentanan tertentu.
- Korelasi antara `Training_Intensity` dan `ACL_Risk_Score`: 0.36: Menunjukkan hubungan moderat, mengindikasikan perlunya pengaturan intensitas latihan untuk mengurangi risiko.
- Atlet dengan lebih dari 2 pertandingan per minggu memiliki risiko lebih tinggi: Frekuensi pertandingan menjadi faktor kunci cedera.
- `Rest_Between_Events_Days` kurang dari 2 hari meningkatkan risiko cedera: Jeda istirahat singkat signifikan memengaruhi kesehatan sendi.
- Risiko ACL tinggi berkorelasi dengan penurunan `Team_Contribution_Score`: Menyoroti dampak cedera pada performa tim.
- Visualisasi pendukung: Lihat Distribusi Usia, Scatter Plot Interaktif, dan lainnya di folder [visualizations](visualizations).
Detail lengkap: [insights_summary.txt](docs/insights_summary.txt) berisi analisis mendalam dan rekomendasi.

## AI Support Explanation
Proyek ini memanfaatkan IBM Granite, model AI berbasis LLM, yang diintegrasikan melalui Google Colab untuk mendukung analisis. Granite digunakan untuk:

- Classification: Mengelompokkan atlet berisiko tinggi berdasarkan `ACL_Risk_Score` dengan menghasilkan filter seperti df[df['ACL_Risk_Score'] > df['ACL_Risk_Score'].quantile(0.75)].
- Summarization: Menyusun 10 queries menjadi insight kuantitatif dengan kode seperti df.groupby(['Gender', 'Position'])['ACL_Risk_Score'].mean().
- Analisis Data: Membantu menghasilkan kode visualisasi secara otomatis, seperti Seaborn untuk heatmap dan Plotly untuk scatter interaktif (termasuk `acl_risk_training_interactive.html`).
- Data Exploration: Mendukung eksplorasi awal dataset dengan menampilkan kolom, statistik, dan contoh data (misalnya df.columns, df.describe()) untuk memahami struktur data.
- Error Handling: Menangani error pada queries dengan mekanisme `try-except`, memastikan analisis tetap berjalan meskipun ada masalah.
- Output Structuring: Mengorganisasi hasil queries ke dalam format terstruktur, disimpan dalam insights_summary.txt untuk presentasi yang jelas. Proses ini didokumentasikan lengkap di notebook [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb).

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
