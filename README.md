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

Masalah Umum pada Data:
   - Banyak missing values terutama pada kolom skor ulasan dan informasi host.
   - Beberapa kolom numerik disimpan sebagai string dengan simbol $, ,, dan %.
   - Kategori boolean disimpan dalam format string ("t" atau "f") dan perlu diubah menjadi numerik (0/1).
   - Fitur amenities disimpan dalam format string JSON-like yang memerlukan parsing.

## Data Preparation
Pada tahap ini, dilakukan serangkaian proses pembersihan dan transformasi data untuk memastikan dataset siap digunakan dalam pemodelan Machine Learning. Berikut tahapan yang dilakukan:
1. Penanganan Missing Values
   - Mengisi nilai kosong dengan median berdasarkan neighbourhood_cleansed untuk fitur numerik seperti skor review.
   - Untuk fitur boolean dan jumlah integer, nilai kosong diisi dengan 0.
   - Untuk bathrooms, bedrooms, dan beds, nilai kosong diisi dengan median berdasarkan grup yang relevan.
2. Feature Engineering
   - Membuat fitur baru revenue sebagai hasil perkalian price dengan minimum_nights.
   - Mengekstrak daftar fasilitas dari kolom amenities dan mengubahnya menjadi fitur biner (dummy features).
3. Feature Encoding
   - Melakukan one-hot encoding pada fitur kategorikal seperti neighbourhood_group_cleansed, property_type, room_type, dan cancellation_policy.
4. Feature Scaling
   - Melakukan standardisasi dan normalisasi (StandardScaler dan MinMaxScaler) untuk fitur numerik seperti beds, bathrooms, host_total_listings_count, dan skor review agar berada dalam skala yang seragam.
5. Menggabungkan semua fitur numerik, kategorikal, hasil encoding, dan engineered features menjadi satu dataset yang siap digunakan untuk modeling.

## Modeling

Pada tahap ini, model Linear Regression digunakan untuk menyelesaikan permasalahan terkait prediksi rating dan revenue listing Airbnb di Seattle. Model dibangun untuk memahami faktor-faktor penting yang mempengaruhi performa listing.
A. Model Linear Regression untuk Prediksi Rating
   - untuk memprediksi skor rating keseluruhan berdasarkan skor komponen seperti accuracy, cleanliness, checkin, communication, location, dan value.
   - Model berhasil menjelaskan sekitar 56,76% variasi skor rating (R² = 0,5676). 
   - Fitur value, cleanliness, dan accuracy menjadi faktor paling berpengaruh   positif terhadap rating.
   - Memberikan interpretasi sederhana terhadap pentingnya masing-masing faktor.
   - Model tidak mempertimbangkan kemungkinan interaksi non-linear antar fitur.
B. Model Linear Regression untuk Prediksi Revenue
   - Untuk memprediksi estimasi revenue listing berdasarkan fasilitas properti, karakteristik rumah, dan skor review.
   - Model menjelaskan 23,34% variasi revenue (R² = 0,2334).
   - Faktor yang paling berkontribusi positif terhadap revenue termasuk fasilitas mewah seperti Hot Tub, Doorman, dan tipe properti seperti Entire Home/Apt.
   - Mengidentifikasi faktor yang berkontribusi terhadap peningkatan pendapatan.
   - Hubungan revenue dengan fitur lebih kompleks dan mungkin membutuhkan model non-linear untuk hasil lebih akurat.

Berikut jawaban dan analisis dari 7 pertanyaan yang telah dijelaskan sebelumnya:
1. Apa saja area dengan peringkat tertinggi untuk memesan akomodasi di Seattle?

Top 10 lingkungan Terbaik dengan Peringkat Tertinggi terdaftar di atas dalam urutan menurun.

2. Apa saja lingkungan dengan revenue tertinggi di Seattle?

Top 10 Lingkungan dengan Pendapatan Tertinggi terdaftar di atas dalam urutan menurun.

3. Apa saja fasilitas yang paling banyak disediakan oleh tuan rumah di Seattle?

Top 15 Fasilitas Teratas yang Paling Banyak Disediakan tercantum di atas dalam urutan menurun.

4. Skor mana yang paling penting untuk ratings keseluruhan?

Tiga faktor riview teratas yang mempengaruhi penilaian keseluruhan untuk seorang tuan rumah adalah Value, Cleanliness dan Accuracy.

5. Apakah tuan rumah dengan ratings lebih tinggi secara keseluruhan menghasilkan revenue lebih tinggi?

Rating yang lebih tinggi tidak secara signifikan meningkatkan revenue. Hubungan antara rating dan revenue sangat lemah (R² hanya 0,11%), sehingga faktor lain di luar rating lebih berpengaruh terhadap potensi revenue sebuah listing.

6. Fasilitas, karakteristik perumahan, dan faktor apa yang berkontribusi positif terhadap revenue?

Revenue lebih tinggi ditemukan pada listings dengan kebijakan pembatalan ketat, status Super Host, pengalaman check-in yang baik, dan tipe kamar "Seluruh Rumah atau Apartemen". Karakteristik properti yang paling berkontribusi positif meliputi Chalet, Tent, Cabin, Apartment, House, Bed & Breakfast, Townhouse, Dormitory, Bungalow, Treehouse, dan Yurt. Fasilitas bernilai tinggi termasuk Doorman, Other Pets, Hot Tub, Breakfast, Washer, Laptop-friendly Workplace, Pool, Buzzer/Wireless Intercom, serta Washer & Dryer.

7. Fasilitas, karakteristik perumahan, dan faktor apa yang berkontribusi positif terhadap ratings?

Ratings lebih tinggi ditemukan pada listings dengan host berstatus Super Host dan terverifikasi, serta rating positif untuk nilai, kebersihan, akurasi, komunikasi, check-in, dan lokasi. Properti asrama dan rumah dengan lebih banyak kamar mandi juga berkontribusi positif. Fasilitas yang meningkatkan rating termasuk Washer & Dryer, Elevator, Pets live on property, Suitable for Events, Other Pets allowed, Safety Card, Kitchen, dan Smoker-friendly. Lingkungan dengan rating tinggi meliputi Rainier Valley, Central Area, Beacon Hill, Delridge, West Seattle, dan Capitol Hill.

Sebagai hasil akhir dari modeling, terdapat beberapa rekomendasi yang dapat diberikan kepada tuan rumah Airbnb untuk meningkatkan performa listing mereka. Untuk meningkatkan rating, tuan rumah disarankan untuk fokus pada peningkatan nilai untuk harga, menjaga kebersihan properti secara konsisten, serta memberikan deskripsi properti yang akurat dan sesuai dengan kondisi nyata. Sementara itu, untuk meningkatkan revenue, tuan rumah dapat mempertimbangkan untuk menyediakan fasilitas tambahan seperti Hot Tub, Washer/Dryer, layanan Doorman Service, serta menerapkan kebijakan pembatalan yang ketat dan memperoleh status Superhost, karena faktor-faktor tersebut terbukti berkontribusi positif terhadap peningkatan pendapatan listing.

## Evaluation
Dalam project ini, evaluasi performa model regresi dilakukan menggunakan empat metrik yaitu sebagai berikut:
1. Nilai Prediksi Revenue
Model | MAE |	MSE | RMSE | R² |
:-----:|:-----:|:-----:|:-----:|:-----:|
Prediksi Revenue | 2605.32 | 14788958.46 | 3845.44 | 0.2334 |

Interpretasi: Model dapat menjelaskan sekitar 23,34% variasi revenue dalam data uji. Nilai RMSE yang cukup besar menunjukkan bahwa ada banyak variabel lain yang tidak dimodelkan secara optimal atau ketidakteraturan dalam data revenue.

2. Nilai Prediksi Rating
Model | MAE |	MSE | RMSE | R² |
:-----:|:-----:|:-----:|:-----:|:-----:|
Prediksi Rating | 2.30 | 13.76 | 3.71 | 0.5623 |

Interpretasi: Model mampu menjelaskan sekitar 56,23% variasi skor rating dengan tingkat kesalahan prediksi yang cukup kecil. Ini mengindikasikan model cukup baik dalam mengestimasi rating berdasarkan fitur yang dipilih.
