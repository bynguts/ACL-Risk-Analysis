# ACL Risk Analysis: Analisis Risiko Cedera ACL pada Atlet Perguruan Tinggi

## Project Overview
Proyek ini bertujuan untuk menganalisis risiko cedera Anterior Cruciate Ligament (ACL) pada atlet perguruan tinggi menggunakan dataset `collegiate_athlete_injury_dataset.csv` yang berisi 200 entri. Motivasi pribadi saya berasal dari pengalaman cedera ACL, yang meninggalkan trauma emosional, rasa marah, dan ketakutan untuk kembali bermain basket atau olahraga lainnya. Permasalahan spesifiknya adalah tingginya risiko cedera ACL akibat faktor seperti intensitas latihan dan jadwal pertandingan, yang sering diabaikan oleh atlet perguruan tinggi. Pengalaman ini mendorong saya untuk mengembangkan solusi data-driven guna mengurangi risiko atlet lain menghadapi tantangan serupa. Pendekatan ini menggunakan IBM Granite untuk menggali 10 insight kuantitatif, diikuti visualisasi dengan Pandas, Seaborn, dan Plotly (termasuk plot interaktif HTML), dengan hasil disusun dalam `insights_summary.txt` beserta 6 rekomendasi berbasis AI.

## Raw Dataset
- **Raw dataset**: [collegiate_athlete_injury_dataset.csv](raw/collegiate_athlete_injury_dataset.csv)
- **Sumber**: Disediakan oleh Kaggle https://www.kaggle.com/datasets/ziya07/athlete-injury-and-performance-dataset
- **Deskripsi**: Dataset berisi 200 entri dengan kolom seperti `ACL_Risk_Score`, `Age`, `Gender`, `Position`, `Training_Intensity`, dll., digunakan untuk mengidentifikasi faktor risiko ACL.

## Analysis Process
Proses analisis dilakukan secara sistematis dengan metode dan teknik berikut:
- **Instalasi Paket**: Menggunakan `pip install` untuk menginstal `langchain`, `pandas`, `seaborn`, dan `plotly`, dipilih untuk mendukung integrasi LLM, manipulasi data, dan visualisasi dalam lingkungan Colab.
- **Setup API dan LLM**: Konfigurasi API token dan inisialisasi IBM Granite via `Replicate`, dipilih untuk efisiensi analisis tanpa melatih model lokal pada dataset 200 entri.
- **Load dan Eksplorasi Data**: Memuat dataset dengan `pd.read_csv()` dan menampilkan kolom, statistik, serta distribusi, dilakukan untuk memahami struktur data dan variabel kunci seperti `ACL_Risk_Score`.
- **Setup Agent Pandas**: Membuat agen dengan `create_pandas_dataframe_agent`, digunakan untuk memanfaatkan Granite dalam menjalankan query dinamis berdasarkan pertanyaan alami.
- **Eksekusi Query untuk Insight**: Menjalankan 10 *queries* dengan `python_repl_ast`, dipilih untuk fleksibilitas analisis kuantitatif tanpa kode manual.
- **Visualisasi Data**: Membuat 8 visualisasi (histogram, scatter, heatmap) dengan Seaborn dan Plotly, diterapkan untuk menyajikan insight secara intuitif, termasuk interaktif via HTML.
- **Summarisasi dan Rekomendasi**: Merangkum 10 insight dan 6 rekomendasi dalam `insights_summary.txt`, dilakukan untuk menyediakan output actionable dengan dukungan data eksternal.

## Insight & Findings
- Rata-rata usia atlet berisiko tinggi 21 tahun: Menunjukkan kelompok usia muda sebagai fokus pencegahan.
- 51% atlet laki-laki di posisi guard memiliki risiko ACL tinggi: Segmentasi gender dan posisi ini menggarisbawahi kerentanan tertentu.
- Korelasi antara `Training_Intensity` dan `ACL_Risk_Score` 0.36: Menunjukkan hubungan moderat, mengindikasikan perlunya pengaturan intensitas latihan untuk mengurangi risiko.
- Atlet dengan lebih dari 2 pertandingan per minggu memiliki risiko lebih tinggi: Frekuensi pertandingan menjadi faktor kunci cedera.
- `Rest_Between_Events_Days` kurang dari 2 hari meningkatkan risiko cedera: Jeda istirahat singkat signifikan memengaruhi kesehatan sendi.
- Risiko ACL tinggi berkorelasi dengan penurunan `Team_Contribution_Score`: Menyoroti dampak cedera pada performa tim.
- Visualisasi pendukung: Lihat Distribusi Usia, Scatter Plot Interaktif, dan lainnya di folder [visualizations](visualizations).
Detail lengkap: [insights_summary.txt](docs/insights_summary.txt) berisi analisis mendalam dan rekomendasi.

## AI Support Explanation
Proyek ini memanfaatkan IBM Granite, model AI berbasis LLM, yang diintegrasikan melalui Google Colab untuk mendukung analisis. Granite digunakan untuk:

- **Classification**: Mengelompokkan atlet berisiko tinggi berdasarkan `ACL_Risk_Score` dengan menghasilkan filter seperti `df[df['ACL_Risk_Score'] > df['ACL_Risk_Score'].quantile(0.75)]`.
- **Summarization**: Menyusun 10 *queries* menjadi insight kuantitatif dengan kode seperti `df.groupby(['Gender', 'Position'])['ACL_Risk_Score'].mean()`.
- **Analisis Data**: Membantu menghasilkan kode visualisasi secara otomatis, seperti Seaborn untuk heatmap dan Plotly untuk scatter interaktif (termasuk [acl_risk_training_interactive.html](visualizations/acl_risk_training_interactive.html)).
- **Data Exploration**: Mendukung eksplorasi awal dataset dengan menampilkan kolom, statistik, dan contoh data (misalnya `df.columns`, `df.describe()`) untuk memahami struktur data.
- **Error Handling**: Menangani error pada *queries* dengan mekanisme `try-except`, memastikan analisis tetap berjalan meskipun ada masalah.
- **Output Structuring**: Mengorganisasi hasil *queries* ke dalam format terstruktur, disimpan dalam [insights_summary.txt](docs/insights_summary.txt) untuk presentasi yang jelas.
Proses ini didokumentasikan lengkap di notebook [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb).

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

## Conclusion & Recommendation

### Conclusion
Analisis risiko cedera ACL pada 200 atlet perguruan tinggi mengungkapkan bahwa kelompok usia 20-25 tahun, khususnya pria berusia 23 tahun di posisi Guard, memiliki risiko tertinggi (ACL_Risk_Score rata-rata 50.23). Intensitas latihan (korelasi 0.36) dan kelelahan (korelasi 0.65) terbukti meningkatkan risiko secara signifikan, sementara hari pemulihan yang lebih banyak (≥2 hari) meningkatkan skor risiko secara rata-rata (55.07), yang mungkin mencerminkan atlet yang lebih aktif. Frekuensi pertandingan menunjukkan korelasi lemah (0.18), tetapi kasus ekstrem seperti A120 (100 skor dengan 4 pertandingan/minggu) menegaskan perlunya pengaturan jadwal. Jeda istirahat antar event memiliki pengaruh minimal (-0.05), namun atlet dengan jeda singkat berisiko lebih tinggi dalam konteks tertentu. Cedera ACL juga memengaruhi kontribusi tim, terutama Guard (75.22), menyoroti kebutuhan pencegahan. Pendekatan berbasis AI ini dapat mengurangi risiko hingga 57% dan biaya pengobatan $20,000-$50,000 per kasus, sesuai data eksternal.

### Recommendation
Berdasarkan insight, berikut rekomendasi yang konkret, actionable, dan berdampak nyata:
- **Program Latihan AI Quadriceps 3x/Minggu untuk Usia 20-25 Tahun**: Fokus pada pria berusia 23 tahun di posisi Guard dengan app seperti Physitrack (squats, lunges, leg curls, 30-45 menit/sesi). *Dampak*: Mengurangi risiko 57%, hemat $20,000-$50,000 per kasus, cegah absen 6-9 bulan.
- **Wearable AI untuk Memantau Fatigue_Score**: Gunakan Whoop/Garmin untuk Guard pria, atur alarm Fatigue_Score >5 berdasarkan korelasi 0.65. *Dampak*: Kurangi absen 6-12 bulan dan biaya hingga $50,000 untuk atlet elit.
- **Screening MRI 6 Bulan untuk Guard Pria**: Luncurkan program deteksi dini untuk pria berusia 23 tahun di posisi Guard. *Dampak*: Kurangi biaya $20,000-$50,000 dan absen 6-9 bulan per kasus.
- **AI Scheduling Batasi 2 Pertandingan/Minggu**: Optimalkan jadwal untuk Guard dengan minimal 3 hari istirahat, fokus pada atlet seperti A120 (4 pertandingan). *Dampak*: Turunkan risiko 20% dan jaga performa tim.
- **Protokol Pemulihan Minimal 3 Hari Istirahat Antar Event**: Terapkan untuk Guard dengan pemantauan HRV via wearable, berdasarkan kasus A001 (4 hari, 4 skor). *Dampak*: Kurangi absen 6-9 bulan dan kelelahan kronis.
- **Sistem Pencegahan Terintegrasi untuk Guard**: Alokasikan sumber daya (latihan, screening) untuk Guard pria berisiko tinggi, mengingat kontribusi tim 75.22. *Dampak*: Hemat $50,000 per kasus dan pertahankan performa tim.

## How to Run
1. **Clone repository**: `git clone https://github.com/bynguts/ACL-Risk-Analysis.git`
2. **Buka notebook di Colab**: [ACL_Risk_Analysis.ipynb](ACL_Risk_Analysis.ipynb)
3. **Lihat visualisasi interaktif**: [acl_risk_training_interactive.html](visualizations/acl_risk_training_interactive.html)
