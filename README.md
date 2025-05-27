# Laporan Project Machine Learning - Mochammad Syahrul Abidin

## Project Overview

Airbnb merupakan salah satu platform penyewaan properti jangka pendek terbesar di dunia yang telah merevolusi industri perhotelan dan akomodasi. Di tengah persaingan yang semakin ketat, pemilik properti dituntut untuk mengoptimalkan strategi penyewaan mereka agar dapat menarik lebih banyak pelanggan dan meningkatkan pendapatan. Salah satu tantangan utama adalah memahami faktor-faktor apa saja yang memengaruhi harga sewa dan rating sebuah properti, agar tuan rumah dapat membuat keputusan berbasis data untuk meningkatkan performa listing mereka.

Mengapa Proyek Ini Penting?
1. Bagi pemilik properti: hasil dari analisis ini dapat digunakan untuk meningkatkan strategi penawaran, memilih fasilitas yang tepat, serta memahami bagaimana rating mempengaruhi revenue.
2. Bagi konsumen: insight yang dihasilkan bisa membantu dalam pengambilan keputusan berdasarkan value for money.
3. Bagi platform Airbnb: model ini dapat digunakan untuk meningkatkan sistem rekomendasi dan penentuan harga otomatis (dynamic pricing).

## Business Understanding

Proyek ini bertujuan untuk menganalisis dan memprediksi harga sewa properti di Seattle melalui pendekatan CRISP-DM (Cross Industry Standard Process for Data Mining), menggunakan data dari platform Airbnb. Dengan memanfaatkan data meliputi harga, fasilitas, lokasi, rating ulasan, dan ketersediaan properti, proyek ini mencoba mengungkap hubungan antar fitur dan menemukan variabel-variabel penting yang memengaruhi rating dan revenue sebuah listing.

### Problem Statements

Dalam upaya membantu pemilik properti dan platform Airbnb untuk meningkatkan performa listing dan revenue, beberapa permasalahan yang perlu diselesaikan dalam proyek ini adalah:
1. Apa saja area dengan peringkat tertinggi untuk memesan akomodasi di Seattle?
2. Apa saja lingkungan dengan revenue tertinggi di Seattle?
3. Apa saja fasilitas yang paling banyak disediakan oleh tuan rumah di Seattle?
4. Skor mana yang paling penting untuk ratings keseluruhan?
5. Apakah tuan rumah dengan ratings lebih tinggi secara keseluruhan menghasilkan revenue lebih tinggi?
6. Fasilitas, karakteristik perumahan, dan faktor apa yang berkontribusi positif terhadap revenue?
7. Fasilitas, karakteristik perumahan, dan faktor apa yang berkontribusi positif terhadap ratings?

### Goals

Berdasarkan masalah yang telah dijelaskan sebelumnya, tujuan dari project ini ialah:
1. Mengidentifikasi area di Seattle dengan rating akomodasi tertinggi.
2. Mengidentifikasi lingkungan di Seattle dengan revenue tertinggi untuk listing Airbnb.
3. Menentukan fasilitas-fasilitas yang paling populer dan paling sering disediakan di Seattle.
4. Menentukan faktor-faktor (review scores) yang paling berkontribusi terhadap rating keseluruhan.
5. Mengevaluasi hubungan antara rating listing dan revenue listing.
6. Menemukan fasilitas dan karakteristik properti yang meningkatkan revenue secara signifikan.
7. Menemukan fasilitas dan karakteristik properti yang meningkatkan rating secara signifikan.

### Solution statements
- Exploratory Data Analysis (EDA)
  Melakukan eksplorasi awal untuk memahami korelasi antara lokasi, fasilitas, harga, rating, dan revenue. Visualisasi data menggunakan heatmap, scatter plot, dan bar chart untuk melihat pola dan hubungan antar variabel.
- Feature Engineering
  Membuat fitur baru seperti revenue dengan rumus revenue = price * minimum_nights. Melakukan one-hot encoding pada fitur kategorikal seperti fasilitas properti.
- Model Building
  Prediksi Rating: Membuat model Linear Regression untuk memprediksi rating berdasarkan skor-skor seperti cleanliness, communication, location, dll.
  Prediksi Revenue: Membangun model Linear Regression untuk memprediksi revenue berdasarkan fasilitas properti, karakteristik listing, dan skor review.
- Evaluasi Model
  Menilai performa model menggunakan metrik R² Score, MAE, MSE, dan RMSE.

## Data Understanding
Dataset yang digunakan dalam proyek ini adalah data Airbnb untuk kota Seattle, Washington selama periode 2016-2017. Terdapat tiga file utama yang digunakan:
- listings.csv: berisi informasi detail mengenai properti yang disewakan, termasuk harga, lokasi, fasilitas, dan skor ulasan (memiliki 92 fitur).
- reviews.csv: memuat ulasan tamu terhadap properti, termasuk tanggal ulasan dan ID listing terkait (memiliki 6 fitur).
- calendar.csv: mencatat harga harian dan ketersediaan untuk setiap properti (memiliki 4 fitur).

Jumlah Total Baris Data:
- listings.csv: 3818 baris data.
- reviews.csv: 84849 baris data.
- calendar.csv: 1393570 baris data.

Variabel-variabel pada dataset ini antara lain:
1. Listings.csv:
   - id: ID unik untuk masing-masing listing di Airbnb.
   - listing_url: URL halaman listing di situs Airbnb.
   - scrape_id: ID unik sesi pengambilan data (scraping).
   - last_scraped: Tanggal terakhir data listing di-scrape.
   - name: Nama judul dari listing properti.
   - summary: Ringkasan singkat mengenai properti.
   - space: Deskripsi ruang properti yang tersedia untuk tamu.
   - description: Deskripsi lengkap tentang listing.
   - experiences_offered: Menyatakan apakah listing menawarkan pengalaman tambahan (experiences).
   - neighborhood_overview: Gambaran tentang lingkungan sekitar properti.
   - notes: Catatan tambahan yang diberikan oleh host.
   - transit: Informasi mengenai transportasi umum di sekitar properti.
   - thumbnail_url: URL untuk gambar thumbnail properti.
   - medium_url: URL untuk gambar ukuran sedang dari properti.
   - picture_url: URL utama gambar properti.
   - xl_picture_url: URL untuk gambar ukuran ekstra besar.
   - host_id: ID unik dari host (pemilik listing).
   - host_url: URL ke profil host di Airbnb.
   - host_name: Nama host.
   - host_since: Tanggal sejak host mulai menggunakan Airbnb.
   - host_location: Lokasi host.
   - host_about: Deskripsi tentang host.
   - host_response_time: Waktu rata-rata host membalas pesan.
   - host_response_rate: Persentase seberapa sering host membalas pesan.
   - host_acceptance_rate: Persentase permintaan yang diterima oleh host.
   - host_is_superhost: Menunjukkan apakah host adalah superhost (ya/tidak).
   - host_thumbnail_url: URL foto profil kecil dari host.
   - host_picture_url: URL foto profil host.
   - host_neighbourhood: Nama lingkungan tempat tinggal host.
   - host_listings_count: Jumlah listing yang dimiliki host saat itu.
   - host_total_listings_count: Total listing host secara keseluruhan.
   - host_verifications: Metode verifikasi identitas host.
   - host_has_profile_pic: Apakah host memiliki foto profil (ya/tidak).
   - host_identity_verified: Apakah identitas host terverifikasi (ya/tidak).
   - treet: Alamat jalan listing.
   - neighbourhood: Nama lingkungan listing.
   - neighbourhood_cleansed: Nama lingkungan yang sudah dibersihkan/standar dari Airbnb.
   - neighbourhood_group_cleansed: Kelompok wilayah berdasarkan Airbnb.
   - city: Kota tempat listing berada.
   - state: Negara bagian tempat listing berada.
   - zipcode: Kode pos lokasi listing.
   - market: Nama pasar lokal (kota).
   - smart_location: Gabungan lokasi cerdas yang digunakan Airbnb.
   - country_code: Kode negara (misal: US).
   - country: Nama negara.
   - latitude: Koordinat lintang properti.
   - longitude: Koordinat bujur properti.
   - is_location_exact: Menunjukkan apakah lokasi yang diberikan akurat atau dibulatkan.
   - property_type: Jenis properti (apartment, house, dll).
   - room_type: Jenis ruangan yang ditawarkan (entire home/apt, private room, shared room).
   - accommodates: Jumlah tamu maksimal yang dapat ditampung.
   - bathrooms: Jumlah kamar mandi.
   - bedrooms: Jumlah kamar tidur.
   - beds: Jumlah tempat tidur.
   - bed_type: Jenis tempat tidur (real bed, airbed, dll).
   - amenities: Fasilitas yang tersedia di properti (dalam format list).
   - square_feet: Luas properti dalam satuan kaki persegi.
   - price: Harga per malam (dalam format string, perlu konversi ke numerik).
   - weekly_price: Harga per minggu (jika tersedia).
   - monthly_price: Harga per bulan (jika tersedia).
   - security_deposit: Besaran deposit keamanan (jika ada).
   - cleaning_fee: Biaya kebersihan (jika ada).
   - guests_included: Jumlah tamu yang termasuk dalam harga dasar.
   - extra_people: Biaya tambahan untuk tamu ekstra.
   - minimum_nights: Jumlah minimum malam yang dapat dipesan.
   - maximum_nights: Jumlah maksimum malam yang dapat dipesan.
   - calendar_updated: Frekuensi update kalender listing.
   - has_availability: Menunjukkan ketersediaan properti (ya/tidak).
   - availability_30: Jumlah hari tersedia dalam 30 hari ke depan.
   - vailability_60: Jumlah hari tersedia dalam 60 hari ke depan.
   - availability_90: Jumlah hari tersedia dalam 90 hari ke depan.
   - availability_365: Jumlah hari tersedia dalam 365 hari ke depan.
   - calendar_last_scraped: Tanggal terakhir kalender listing di-scrape.
   - number_of_reviews: Jumlah total ulasan yang diterima.
   - first_review: Tanggal ulasan pertama.
   - last_review: Tanggal ulasan terakhir.
   - review_scores_rating: Skor rating keseluruhan listing.
   - review_scores_accuracy: Skor akurasi deskripsi listing.
   - review_scores_cleanliness: Skor kebersihan properti.
   - review_scores_checkin: Skor pengalaman check-in tamu.
   - review_scores_communication: Skor komunikasi dengan host.
   - review_scores_location: Skor lokasi properti.
   - review_scores_value: Skor nilai untuk uang (value for money).
   - requires_license: Apakah properti membutuhkan lisensi (ya/tidak).
   - license: Nomor lisensi (di dataset ini seluruhnya kosong).
   - jurisdiction_names: Nama yurisdiksi properti (aturan/ketentuan hukum lokal).
   - instant_bookable: Menyatakan apakah properti dapat langsung dipesan tanpa persetujuan host.
   - cancellation_policy: Jenis kebijakan pembatalan (flexible, moderate, strict, dll).
   - require_guest_profile_picture: Apakah tamu wajib memasang foto profil.
   - require_guest_phone_verification: Apakah tamu wajib verifikasi nomor telepon.
   - calculated_host_listings_count: Jumlah listing yang terhubung ke host saat data diambil.
   - reviews_per_month: Rata-rata ulasan per bulan.
2. reviews.csv:
   - listing_id: ID unik dari properti yang diulas.
   - id: ID unik untuk setiap ulasan.
   - date: Tanggal ulasan dibuat.
   - reviewer_id: ID unik dari tamu yang menulis ulasan.
   - reviewer_name: Nama tamu yang memberikan ulasan.
   - comments: Isi komentar/ulasan dari tamu.
3. calendar.csv:
   - listing_id: ID unik dari properti terkait kalender.
   - date: Tanggal spesifik untuk ketersediaan listing.
   - available: Status apakah properti tersedia untuk tanggal tersebut (ya/tidak).
   - price: Harga sewa per malam untuk tanggal tertentu (format string, perlu konversi ke numerik).

Kondisi Data:
- Tidak ada duplikat yang signifikan ditemukan di dataset utama. Namun, beberapa kolom yang memiliki informasi yang lebih terperinci, seperti host_name dan neighbourhood, memiliki variasi pengkodean yang harus dibersihkan.
- Terdapat beberapa outlier dalam dataset, terutama pada fitur price dan availability. Beberapa properti memiliki harga yang sangat tinggi atau sangat rendah yang perlu dianalisis lebih lanjut untuk memastikan apakah itu kesalahan atau bagian dari strategi bisnis yang sah.

Distribusi Data:
- Price: Terdapat distribusi harga yang sangat bervariasi, dengan sebagian besar harga berkisar antara $50 hingga $200 per malam, namun ada beberapa properti dengan harga lebih dari $1000 per malam yang merupakan outlier.
- Reviews: Sebagian besar properti memiliki jumlah ulasan yang relatif sedikit, dengan beberapa properti memiliki jumlah ulasan lebih dari 500 yang merupakan anomali.
- Fasilitas: Fasilitas seperti WiFi, kitchen, dan washer & dryer merupakan fasilitas yang paling umum disediakan, sementara fasilitas mewah seperti hot tub dan doorman lebih jarang ditemukan.

Masalah Umum pada Data:
   - Banyak missing values terutama pada kolom skor ulasan dan informasi host.
   - Beberapa kolom numerik disimpan sebagai string dengan simbol $, ,, dan %.
   - Kategori boolean disimpan dalam format string ("t" atau "f") dan perlu diubah menjadi numerik (0/1).
   - Fitur amenities disimpan dalam format string JSON-like yang memerlukan parsing.

Sumber data yang digunakan berasal dari dataset Airbnb yang dapat diakses melalui tautan berikut:
https://drive.google.com/drive/folders/1HfWY6uvPdMCKvWzdC1vYjahvdvzvZcOr?usp=sharing

## Data Preparation
Pada tahap ini, dilakukan serangkaian proses pembersihan dan transformasi data untuk memastikan dataset siap digunakan dalam pemodelan Machine Learning. Berikut tahapan yang dilakukan:
1. Penanganan Missing Values
   - Mengisi nilai kosong dengan median berdasarkan neighbourhood_cleansed untuk fitur numerik seperti skor review.
   - Untuk fitur boolean dan jumlah integer, nilai kosong diisi dengan 0.
   - Untuk bathrooms, bedrooms, dan beds, nilai kosong diisi dengan median berdasarkan grup yang relevan.
2. Konversi Tipe Data
   - Kolom price yang awalnya berupa string (dengan simbol "$" dan koma) dikonversi menjadi tipe numerik.
   - Kolom available yang awalnya berisi nilai "t" atau "f" dikonversi menjadi tipe boolean (True/False).
   - Beberapa kolom yang memiliki format tidak standar, seperti amenities, dikonversi menjadi format yang lebih mudah diproses.
3. Feature Engineering
   - Membuat fitur baru revenue sebagai hasil perkalian price dengan minimum_nights.
   - Mengekstrak daftar fasilitas dari kolom amenities dan mengubahnya menjadi fitur biner (dummy features).
4. Feature Encoding
   - Melakukan one-hot encoding pada fitur kategorikal seperti neighbourhood_group_cleansed, property_type, room_type, dan cancellation_policy.
5. Feature Scaling
   - Melakukan standardisasi dan normalisasi (StandardScaler dan MinMaxScaler) untuk fitur numerik seperti beds, bathrooms, host_total_listings_count, dan skor review agar berada dalam skala yang seragam.
6. Feature Selection
   - Fitur yang dipilih berdasarkan analisis korelasi dan relevansi dengan target variabel, yaitu:
      - Rating: Fitur yang paling berpengaruh terhadap rating adalah value, cleanliness, dan accuracy.
      - Revenue: Fitur yang berkontribusi positif terhadap revenue adalah tipe properti seperti Entire Home/Apt, fasilitas mewah seperti Hot Tub, dan status Super Host.
7. Data Splitting
   - Dataset dibagi menjadi dua bagian yaitu:
      - Training Set: Data yang digunakan untuk melatih model, yang terdiri dari 80% dari total data.
      - Testing Set: Data yang digunakan untuk menguji dan mengevaluasi performa model, yang terdiri dari 20% dari total data.

## Modeling
Pada tahap ini, model Linear Regression digunakan untuk menyelesaikan permasalahan terkait prediksi rating dan revenue listing Airbnb di Seattle. Model dibangun untuk memahami faktor-faktor penting yang mempengaruhi performa listing.
A. Model Linear Regression untuk Prediksi Rating
   Linear Regression adalah metode statistik yang digunakan untuk memodelkan hubungan linier antara variabel independen (fitur) dan variabel dependen (target). Dalam konteks ini, kita menggunakan Linear Regression untuk memprediksi rating keseluruhan dari sebuah listing Airbnb berdasarkan skor review yang berbeda, seperti cleanliness, communication, location, dan value for money. Cara kerja dari Linear Regression adalah dengan mencari garis terbaik yang meminimalkan selisih antara prediksi dan nilai aktual. Ini dilakukan dengan cara mengoptimalkan koefisien pada fitur yang ada. Model ini mengasumsikan hubungan linier antara variabel input dan output. Parameter yang Digunakan adalah Model menggunakan parameter default Linear Regression dari scikit-learn.
   Kelebihan:
   - Sederhana dan cepat dalam implementasi.
   - Mudah untuk menginterpretasi hasilnya, karena model memberikan koefisien yang menggambarkan pengaruh setiap fitur terhadap target.
   - Efisien untuk dataset dengan hubungan linier.
   Kekurangan:
   - Tidak efektif untuk menangani data dengan hubungan non-linier.
   - Sensitif terhadap outliers yang dapat memengaruhi hasil prediksi.

B. Model Linear Regression untuk Prediksi Revenue
   Linear Regression juga digunakan untuk memprediksi revenue listing Airbnb, yang dihitung berdasarkan harga per malam, jumlah kamar tidur, jumlah kamar mandi, dan fasilitas properti. Model ini mengasumsikan bahwa ada hubungan linier antara fitur-fitur properti dengan revenue yang dihasilkan. Linear Regression bekerja dengan mengestimasi koefisien untuk setiap fitur yang ada, sehingga dapat digunakan untuk memprediksi revenue. Setiap fitur akan memberikan kontribusi tertentu terhadap hasil prediksi, yang dihitung berdasarkan bobot koefisiennya. Parameter yang Digunakan adalah Sama dengan model rating, algoritma menggunakan parameter default.
   Kelebihan:
   - Memberikan hasil yang cepat dan mudah dipahami.
   - Cukup kuat untuk memodelkan hubungan sederhana antara fitur dan target.
   - Dapat memberikan wawasan langsung tentang pengaruh masing-masing fitur terhadap revenue.
   Kekurangan:
   - Model ini mungkin kurang cocok untuk hubungan non-linier atau kompleks yang ada dalam data.
   - Rentan terhadap multikolinearitas, dimana beberapa fitur yang sangat berkorelasi dapat memengaruhi keakuratan model.

## Evaluation
Dalam project ini, evaluasi performa model regresi dilakukan menggunakan empat metrik yaitu sebagai berikut:
1. Nilai Prediksi Revenue

Tabel 1. Evaluasi Kinerja Model Prediksi Revenue

| Model | MAE |	MSE | RMSE | R² |
|:-----:|:-----:|:-----:|:-----:|:-----:|
|Prediksi Revenue | 2.30 | 13.77 | 3.71 | 0.56 |

![Evaluasi Prediksi Revenue](https://github.com/user-attachments/assets/e0a4bbbd-c865-445e-8b45-6ff55112fa26)

Gambar 8. Actual vs Predicted (Revenue)

Interpretasi: Model dapat menjelaskan sekitar 56% variasi revenue dalam data uji. Nilai RMSE yang cukup besar menunjukkan bahwa ada banyak variabel lain yang tidak dimodelkan secara optimal atau ketidakteraturan dalam data revenue.


2. Nilai Prediksi Rating

Tabel 2. Evaluasi Kinerja Model Prediksi Rating
  
| Model | MAE |	MSE | RMSE | R² |
|:-----:|:-----:|:-----:|:-----:|:-----:|
|Prediksi Rating | 2.29 | 13.76 | 3.71 | 0.56 |

![Evaluasi Prediksi Rating](https://github.com/user-attachments/assets/b2e5b584-ecee-459f-bf86-ad90276bfa05)

Gambar 9. Actual vs Predicted (Rating) 

Interpretasi: Model mampu menjelaskan sekitar 56% variasi skor rating dengan tingkat kesalahan prediksi yang cukup kecil. Ini mengindikasikan model cukup baik dalam mengestimasi rating berdasarkan fitur yang dipilih.

Berikut jawaban dan analisis dari 7 pertanyaan yang telah dijelaskan sebelumnya:
1. Apa saja area dengan peringkat tertinggi untuk memesan akomodasi di Seattle?

![Jawaban pertanyaan 1](https://github.com/user-attachments/assets/26a45e4d-bc71-4072-93ae-61393dfad8ab)

Gambar 1. Top 10 Area dengan Peringkat Tertinggi

Top 10 area Terbaik dengan Peringkat Tertinggi terdaftar di atas dalam urutan menurun.

2. Apa saja lingkungan dengan revenue tertinggi di Seattle?

![Jawaban pertanyaan 2](https://github.com/user-attachments/assets/33287145-f391-46c5-8aca-3727f04bb7d1)

Gambar 2. Top 10 Area dengan Pendapatan Tertinggi

Top 10 area dengan Pendapatan Tertinggi terdaftar di atas dalam urutan menurun.

3. Apa saja fasilitas yang paling banyak disediakan oleh tuan rumah di Seattle?

![Jawaban pertanyaan 3](https://github.com/user-attachments/assets/017f4c08-3854-413d-ba1d-b72264f5880f)

Gambar 3. Grafik Top 15 Fasilitas

Top 15 Fasilitas Teratas yang Paling Banyak Disediakan tercantum di atas dalam urutan menurun.

4. Skor mana yang paling penting untuk ratings keseluruhan?

![Jawaban pertanyaan 4](https://github.com/user-attachments/assets/5eab1d3c-9eb7-4124-b3da-1e8de247fcb6)

Gambar 4. Grafik Top 6 Riview Scores

Tiga faktor riview teratas yang mempengaruhi penilaian keseluruhan untuk seorang tuan rumah adalah Value, Cleanliness dan Accuracy.

5. Apakah tuan rumah dengan ratings lebih tinggi secara keseluruhan menghasilkan revenue lebih tinggi?

![Jawaban pertanyaan 5](https://github.com/user-attachments/assets/bd73183a-944b-4ec2-8e3f-5ba90c61eff1)

Gambar 5. Grafik Top Riview Scores

Rating yang lebih tinggi tidak secara signifikan meningkatkan revenue. Hubungan antara rating dan revenue sangat lemah (R² hanya 0,11%), sehingga faktor lain di luar rating lebih berpengaruh terhadap potensi revenue sebuah listing.

6. Fasilitas, karakteristik perumahan, dan faktor apa yang berkontribusi positif terhadap revenue?

![Jawaban pertanyaan 6](https://github.com/user-attachments/assets/bb7f79c3-8b80-4491-b3f7-e324fd120199)

Gambar 6. Grafik Top 25 Fasilitas, Karakteristik Perumahan, dan Faktor Serupa yang Paling Berkontribusi Positif terhadap Revenue

Revenue lebih tinggi ditemukan pada listings dengan kebijakan pembatalan ketat, status Super Host, pengalaman check-in yang baik, dan tipe kamar "Seluruh Rumah atau Apartemen". Karakteristik properti yang paling berkontribusi positif meliputi Chalet, Tent, Cabin, Apartment, House, Bed & Breakfast, Townhouse, Dormitory, Bungalow, Treehouse, dan Yurt. Fasilitas bernilai tinggi termasuk Doorman, Other Pets, Hot Tub, Breakfast, Washer, Laptop-friendly Workplace, Pool, Buzzer/Wireless Intercom, serta Washer & Dryer.

7. Fasilitas, karakteristik perumahan, dan faktor apa yang berkontribusi positif terhadap ratings?

![Jawaban pertanyaan 7](https://github.com/user-attachments/assets/4d85c626-8514-4d97-b476-cf8f65b00291)

Gambar 7. Grafik Top 25 Fasilitas, Karakteristik Perumahan, dan Faktor Serupa yang Paling Berkontribusi Positif terhadap Rating

Ratings lebih tinggi ditemukan pada listings dengan host berstatus Super Host dan terverifikasi, serta rating positif untuk nilai, kebersihan, akurasi, komunikasi, check-in, dan lokasi. Properti asrama dan rumah dengan lebih banyak kamar mandi juga berkontribusi positif. Fasilitas yang meningkatkan rating termasuk Washer & Dryer, Elevator, Pets live on property, Suitable for Events, Other Pets allowed, Safety Card, Kitchen, dan Smoker-friendly. Lingkungan dengan rating tinggi meliputi Rainier Valley, Central Area, Beacon Hill, Delridge, West Seattle, dan Capitol Hill.

