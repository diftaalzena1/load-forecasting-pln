# ⚡ Short-Term Electric Load Forecasting for Grid Demand Planning (Dummy Project for PLN Use Case)

Halo! Ini adalah proyek portofolio saya sebagai seorang data scientist, yang berfokus pada bagaimana data time series dapat dimanfaatkan untuk perencanaan distribusi daya listrik jangka pendek — terutama di sektor energi dan kelistrikan.

Dalam proyek ini, saya membangun model prakiraan beban listrik harian menggunakan data simulasi realistis. Pendekatan ini meniru kebutuhan PLN dalam memprediksi beban listrik harian untuk menjaga kestabilan pasokan dan efisiensi jaringan distribusi.

---

## 🧠 Latar Belakang

Sistem kelistrikan nasional membutuhkan perencanaan beban yang akurat untuk menghindari over-supply (pemborosan daya) maupun under-supply (pemadaman). Prakiraan beban listrik yang buruk dapat memengaruhi:

- Efisiensi distribusi daya  
- Keandalan sistem jaringan  
- Stabilitas operasional pembangkit

Proyek ini mensimulasikan pendekatan _data-driven forecasting_ yang dapat membantu PLN atau penyedia listrik lainnya dalam merencanakan pasokan harian berdasarkan data historis konsumsi.

---

## 🎯 Tujuan Proyek

- Mensimulasikan sistem prakiraan beban listrik harian berbasis model statistik.
- Membandingkan beberapa pendekatan (ARIMA, Regresi Linear, Polynomial).
- Membangun pipeline prakiraan yang siap diintegrasikan ke sistem monitoring PLN.
- Menunjukkan kemampuan ARIMA dalam validasi operasional (rolling forecast).

---

## 🛠️ Pendekatan & Tools

### Data & Simulasi

- Data dummy selama 365 hari (tahun 2024)
- Beban dasar: 800 MW
- Pola musiman: fungsi sinus (summer/winter effect)
- Efek mingguan: weekday vs weekend
- Noise acak: simulasi dinamika konsumsi harian

### Modeling & Evaluasi

- **Model**: ARIMA(5,1,0), Regresi Linear, Polynomial Regression (degree=2)
- **Evaluasi**: MAPE (Mean Absolute Percentage Error)
- **Validasi operasional**: Rolling Forecast (one-step prediction)
- **Tools**: Python, Pandas, Scikit-learn, Statsmodels, Seaborn

---

## 📊 Komponen Utama

### Exploratory Data Analysis (EDA)
- Visualisasi tren musiman dan fluktuasi harian
- Uji stasioneritas (ADF Test)
- ACF & PACF untuk identifikasi parameter ARIMA

### Train-Test Split
- Data 14 hari terakhir disisihkan sebagai test set
- Pendekatan out-of-sample realistis sesuai kebutuhan PLN

### Modeling & Forecast
- **ARIMA** memberikan hasil paling akurat (MAPE 4.85%)
- **Rolling Forecast ARIMA** (MAPE 2.48%) → simulasi prediksi harian PLN
- Regresi Linear dan Polynomial digunakan sebagai baseline sederhana

### Forecasting Pipeline
Fungsi `forecast_beban_listrik()` dibangun modular agar siap digunakan:

```
def forecast_beban_listrik(data, steps=7, order=(5,1,0)):
```

✅ Siap integrasi ke:

* Dashboard PLN (real-time forecasting)
* Cron job harian / API internal
* Skala regional atau nasional

---

## 🔎 Insight & Hasil

| Model                 | MAPE   | Keterangan                                 |
| --------------------- | ------ | ------------------------------------------ |
| ARIMA (static)        | 4.85%  | Akurat dan stabil untuk prediksi musiman   |
| Linear Regression     | 11.68% | Cepat tapi lemah pada pola musiman         |
| Polynomial Regression | 14.46% | Menangkap tren non-linear tapi sensitif    |
| Rolling ARIMA         | 2.48%  | Simulasi harian paling realistis untuk PLN |

📌 Ringkasan:

* ARIMA cocok sebagai *main model* untuk forecasting beban listrik jangka pendek
* Pipeline dapat otomatis dijalankan setiap hari (rolling)
* Sistem siap diadaptasi ke sistem peringatan dini PLN atau dashboard harian

---

## 📌 Catatan Tambahan

> Proyek ini merupakan dummy project untuk pembelajaran dan portofolio. Semua data bersifat simulasi dan tidak merepresentasikan data asli PLN.

Namun pendekatan dan pipeline yang dibangun telah dirancang sedekat mungkin dengan kebutuhan operasional dunia nyata, sehingga bisa menjadi referensi awal sistem prakiraan PLN berbasis data science.

---

## 👤 Tentang Penulis

**Difta Alzena Sakhi**
Mahasiswa S1 Sains Data – UPN "Veteran" Jawa Timur
🔗 GitHub: [@diftaalzena1](https://github.com/diftaalzena1)

---

## 🙏 Terima Kasih

Terima kasih telah mengunjungi proyek ini!
Kalau kamu punya pertanyaan, saran, atau ingin diskusi seputar topik ini — jangan ragu untuk kontak saya lewat GitHub 😄

