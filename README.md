🧪 A/B Testing Conversion Rate
==============================

📌 Project Overview
--------------------

Project ini bertujuan untuk mengevaluasi efektivitas dua varian desain atau strategi digital (**Variant A** dan **Variant B**) melalui metode **A/B Testing**. Analisis dilakukan terhadap berbagai metrik utama seperti **Conversion Rate**, **Click-Through Rate (CTR)**, **Add-to-Cart Rate**, **Checkout Rate**, dan **Average Revenue Per User (ARPU)** untuk mengidentifikasi varian yang memberikan performa terbaik.

Dataset bersumber dari Kaggel dalam bentuk CSV, terdiri dari 100.000 baris data yang mencakup informasi pengguna, variant, perangkat, negara, sumber traffic, dan perilaku funnel (page view, click, add to cart, hingga purchase).

Hasil analisis menunjukkan bahwa secara keseluruhan **Variant A unggul** dengan conversion rate 7,14% dibandingkan Variant B sebesar 6,98%. Namun, ditemukan juga bahwa pada segmen tertentu (Malaysia, Desktop, Google Ads), **Variant B justru menunjukkan performa lebih baik**, sehingga pendekatan segmentasi lebih disarankan dibandingkan penerapan satu variant secara global.

🎯 Problem Statement
---------------------

Perusahaan ingin mengetahui apakah perubahan desain/strategi digital (Variant B) memberikan peningkatan conversion rate dibandingkan versi sebelumnya (Variant A), serta segmen pengguna mana yang menunjukkan performa terbaik dan terburuk.

❓ Business Question
---------------------

- Apakah Variant B memberikan peningkatan conversion rate dibandingkan Variant A?
- Segmen pengguna mana (country, device, traffic source) yang menunjukkan performa terbaik dan terburuk?
- Bagaimana tren conversion rate kedua varian selama periode eksperimen?
- Apakah performa kedua variant berbeda pada setiap jenis perangkat?


🛠️ Tools & Tech Stack
------------------------

| Kategori | Tools |
|---|---|
| Bahasa Pemrograman | Python |
| Library Data Processing | Pandas, NumPy |
| Analisis Statistik | IQR Method (Outlier Detection) |
| Visualisasi | Matplotlib, Power BI |
| Sumber Data | Kaggle (CSV) |
| Environment | Jupyter Notebook |


⚙️ Method
-----------

1. **Data Understanding** — Memeriksa struktur dan tipe data. Dataset terdiri dari 100.000 baris dengan 16 kolom (`user_id`, `variant`, `date`, `device`, `browser`, `country`, `page_view`, `click`, `add_to_cart`, `purchase`, `revenue`, `session_duration`, `impressions`, `traffic_source`, `gender`, `age`). Ditemukan satu tipe data yang tidak konsisten pada kolom `date`.
2. **Data Cleaning** — Tidak ditemukan *missing value* maupun *duplicate*. Dilakukan penyeragaman huruf (lowercase) dan penghapusan spasi berlebih pada kolom kategorikal seperti `variant`.
3. **Data Preparation** — Mengubah tipe data `date` menjadi format datetime (`pd.to_datetime`) agar sesuai untuk analisis tren waktu.
4. **Outlier Handling** — Mendeteksi outlier menggunakan metode **IQR** pada kolom `revenue`, `session_duration`, dan `purchase`. Tidak ditemukan outlier pada `revenue` dan `session_duration`, namun ditemukan outlier sebesar 7,06% pada `purchase` yang tetap dipertahankan karena dianggap valid.
5. **Exploratory Data Analysis** — Menganalisis conversion rate berdasarkan traffic source, country, device, dan variant, serta melakukan analisis univariate pada session duration dan impressions untuk memastikan tidak ada ketimpangan data yang signifikan.
6. **Dashboard & Decomposition Analysis** — Menyajikan hasil analisis dalam dashboard Power BI interaktif, dilengkapi heatmap device & variant serta decomposition tree untuk menelusuri performa variant pada level segmen yang lebih detail (country → device → traffic source → variant).

💡 Business Recommendations
-----------------------------

- **Implementasikan Variant A sebagai default version**, karena terbukti menghasilkan conversion rate tertinggi secara keseluruhan dan performa yang lebih stabil selama periode pengujian.
- **Lakukan segment-based deployment** dengan mempertimbangkan penggunaan Variant B pada segmen Malaysia, Desktop, dan Google Ads, karena pada segmen tersebut Variant B menunjukkan performa yang lebih unggul dibandingkan Variant A.
- **Optimalkan channel Google Ads** karena memiliki conversion rate tertinggi dibandingkan sumber traffic lainnya, sehingga berpotensi memberikan return yang lebih baik terhadap investasi pemasaran.
- **Tingkatkan performa pengguna mobile** melalui optimasi tampilan dan pengalaman pengguna, mengingat conversion rate mobile masih lebih rendah dibandingkan desktop.
- **Fokus meningkatkan CTR** melalui perbaikan desain, copywriting, call-to-action (CTA), dan strategi targeting, karena CTR yang masih rendah menunjukkan banyak pengguna belum tertarik untuk melanjutkan ke tahap berikutnya dalam funnel.

✅ Conclusion
--------------

Berdasarkan hasil analisis A/B Testing, **Variant A** secara keseluruhan menunjukkan performa yang lebih baik dibandingkan Variant B dengan conversion rate sebesar **7,14%**, sedangkan Variant B memperoleh **6,98%**. Hal ini menunjukkan bahwa perubahan yang diterapkan pada Variant A lebih efektif dalam mendorong pengguna melakukan konversi. Dari sisi segmentasi, **Malaysia** menjadi negara dengan conversion rate tertinggi, **Desktop** merupakan perangkat dengan performa terbaik, dan **Google Ads** menjadi sumber traffic yang menghasilkan konversi paling tinggi.

Analisis lebih lanjut menggunakan **Decomposition Tree** menunjukkan bahwa performa variant tidak selalu konsisten pada seluruh segmen pengguna. Meskipun Variant A unggul secara agregat, kombinasi **Malaysia–Desktop–Google Ads** pada **Variant B** justru menghasilkan purchase rate tertinggi sebesar **8,79%**, jauh di atas rata-rata keseluruhan sebesar 7,06%. Temuan ini mengindikasikan bahwa karakteristik pengguna memiliki pengaruh terhadap efektivitas suatu variant, sehingga pendekatan yang lebih tersegmentasi dapat memberikan hasil yang lebih optimal dibandingkan penerapan satu variant untuk seluruh pengguna.
