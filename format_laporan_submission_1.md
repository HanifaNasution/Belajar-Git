# Laporan Proyek Machine Learning - Hanifa Rahmacindia Nasution

## Domain Proyek

(Pada bagian ini, kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.
**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa dan bagaimana masalah tersebut harus diselesaikan
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.)

IHSG atau singkatan dari Indeks Harga Saham Gabungan merupakan indeks pasar saham utama di Bursa Efek Indonesia (BEI) mencerminkan pergerakan harga seluruh saham yang tercatat di BEI. Secara umum, IHSG memberikan informasi umum bagaimana rata-rata harga saham yang tercatat di Indonesia. Singkatnya, IHSG menjadi salah satu indikator utama yang mencerminkan kondisi pasar saham Indonesia. 

Melansir dari laman djpb.kemenkeu.go.id [IHSG Anjlok, Apa saja Kemungkinan Dampaknya terhadap Pendapatan dan Belanja Pemerintah?] (https://djpb.kemenkeu.go.id/kppn/jakarta6/id/data-publikasi/berita-terbaru/2912-dampak-penurunan-ihsg-terhadap-pendapatan-dan-pengeluaran-pemerintah.html), pertengahan Maret 2025, IHSG mengalami penurunan drastis sebesar 6,12 persen atau 395,86 poin, turun hingga level 6.078,08. Mengutip dari pemberitaan Tempo.co [Cara Membaca IHSG dengan Sederhana: Kapan Tren Naik dan Turun] (https://www.tempo.co/ekonomi/cara-membaca-ihsg-dengan-sederhana-kapan-tren-naik-dan-turun-1230677), pada tanggal 8 April, ketika perdagangan efek kembali dibuka usai libur panjang lebaran, bukannya justru bangkit dari keterpurukan, IHSG justru terjun bebas ke zona merah. IHSG anjlok 9,19 persen atau turun 598,55 poin ke level 5.912,06. 

Penurunan IHSG tidak hanya mencerminkan lesunya pasar modal tetapi juga akan berdampak pada perekonomian negara secara keseluruhan. Jika tren penurunan tersebut berlangsung dalam jangka panjang, negara perlu membayar mahal yang berkaitan dengan pendapatan dan pendanaan negara. Melansir dari Kompas.com [IHSG Anjlok, Apa Dampaknya bagi Indonesia?] (https://www.kompas.com/tren/read/2025/03/20/074500865/ihsg-anjlok-apa-dampaknya-bagi-indonesia-), negara akan menghadapi beberapa konsekuensi akibat hal tersebut, diantaranya :
1. Berkurangnya pendapatan negara
Ketika nilai saham perusahaan menurun, maka potensi keuntungan perusahaan berkurang, yang berdampak pada menurunnya pendapatan dari dividen. Hal ini akan berdampak terhadap pendapatan negara yang didapat dari pajak perusahaan tersebut.
2. Hambatan dalam pendanaan proyek infrastruktur
Proyek infrastruktur yang bergantung pada investasi swasta dengan skema public-private partnerships (PPP) akan terkendala jika IHSG terus melemah. Hal tersebut terjadi karena para investor hengkang dari partisipasi proyek-proyek pembangunan.
3. Ketergantungan yang lebih besar pada utang
Berkurangnya pendapatan negara akibat melemahnya IHSG membuat pemerintah kesulitan memenuhi terget belanjanya sehingga pemerintah akan meningkatkan nominal utang sebagai sumber pendanaan alternatif.
4. Pengurangan belanja pada sektor non-prioritas
Jika penerimaan negera terus menurun dalam jangka panjang, maka pemerintah akan melakukan "efisiensi anggaran" dengan menunda belanja pada sektor-sektor yang tidak mendesak. Proyek pembangunan jangka panjang yang tidak berdampak langsung terhadap stabilitas ekonomi, seperti sektor "pendidikan dan kesehatan" akan dikurangi atau ditunda [Anggaran pendidikan dasar dan menengah dipangkas Rp8 triliun – Bagaimana nasib guru honorer dan program pembangunan sekolah?] (https://www.bbc.com/indonesia/articles/ckgxe99qyzno)
5. Ketidakstabilan sektor sosial dan politik
Menurunnya IHSG juga dapat menciptakan ketidakpastian ekonomi yang lebih luas, yang berpotensi memicu gejolak sosial dan politik. Jika terus berlanjut, tekanan terhadap pemerintah akan semakin besar.
6. Menurunnya kepercayaan investor
Menurunnya kepercayaan investor terhadap perekonomian Indonesia akan menyebabkan investor pesimis terhadap prospek ekonomi dan memilih menarik investasinya dari pasar Indonesia yang lesu. 

Sederet permasalahan yang diikuti buntut panjang penurunan IHSG menyebabkan peramalan harga IHSG menjadi penting. Peramalan IHSG yang akurat dan reliabel mampu memberikan alarm dini bagi pemerintah di berbagai lini untuk mempersiapkan diri mengeksekusi rencana darurat guna mempertahankan kestabilan ekonomi Indonesia. Oleh karena itu, pada proyek machine learning ini, saya akan membuat forecasting harga saham IHSG. 
  
## Business Understanding

(Pada bagian ini, kamu perlu menjelaskan proses klarifikasi masalah.
Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Statement” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution statement. Misalnya, menggunakan dua atau lebih algoritma untuk mencapai solusi yang diinginkan atau melakukan improvement pada baseline model dengan hyperparameter tuning.
    - Solusi yang diberikan harus dapat terukur dengan metrik evaluasi.

Bagian laporan ini mencakup:)

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:

- Bagaimana model prediksi IHSG yang dapat digunakan sebagai alarm dini pemerintah dalam menjaga kestabilan ekonomi Indonesia?
- Bagaimana kondisi saham IHSG diukur dari berbagai skenario waktu : 
1. jangka pendek (3 hari kedepan)
2. jangka menengah (7 hari kedepan)
3. jangka panjang (2 minggu kedepan)

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Membangun model prediksi IHSG yang dapat digunakan sebagai alarm dini pemerintah dalam menjaga kestabilan ekonomi Indonesia
- Memprediksi pergerakan saham IHSG dari berbagai skenario waktu sehingga mampu memberikan pertimbangan berbasis data dan analisis dalam setiap horizon waktu berbeda:
1. jangka pendek (3 hari kedepan)
2. jangka menengah (7 hari kedepan)
3. jangka panjang (2 minggu kedepan)

### Solution Statements

Penguraian langkah untuk mencapai goals
- Menerapkan 3 algoritma machine learning untuk data time series, yaitu
1. LSTM
2. GRU
3. Multilayer Perceptron
4. CNN
- Membandingkan performa model dengan metrik evaluasi dan memilih model dengan metrik evaluasi terkecil. Berikut merupakan metrik evaluasi yang digunakan: 
1. MSE
2. MAE
3. RMSE
- Melakukan hyperparameter tuning pada kedua model untuk meningkatkan performa prediksi menggunakan early stopping.

## Data Understanding
(Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. 
**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.)

Data yang digunakan pada projek ini adalah data historis IHSG yang didapatkan dari laman website id.investing.com [Investing.com](https://id.investing.com/indices/idx-composite-historical-data) dengan periode waktu 1 Januari 2023 hingga 30 April 2025 sehingga terdapat 552 data points. Alasan penggunaan periode waktu tersebut karena per tanggal 21 Juni 2023 telah dihentikan kebijakan COVID-19 yang secara implisit menandakan bahwa ekonomi Indonesia telah mampu bergerak secara normal. Namun, dipilih mulai 1 Januari 2023 karena adanya syarat penggunaan data pada projek ini yaitu minimal 500 data points. 

### Variabel-variabel pada Dataset Saham IHSG adalah sebagai berikut:
- Tanggal : menunjukkan tanggal perdagangan, hanya mencakup hari bursa (Senin - Jumat, tidak termasuk hari libur dan akhir pekan)
- Terakhir : harga penutupan IHSG di akhir sesi perdagangan pada hari tersebut. umumnya data ini yang paling sering digunakan untuk analisis dan prediksi
- Pembukaan : harga IHSG saat pasar dibuka di pagi hari, data ini dapat dibandingkan dengan "Terakhir" untuk melihat apakah IHSG naik atau turun sepanjang hari
- Tertinggi : harga tertinggi yang dicapai IHSG sepanjang sesi perdagangan hari itu
- Terendah : harga terendah yang dicapai IHSG sepanjang hari
- Volume : jumlah saham yang diperdagangkan pada hari itu dalam seluruh indeks
- Perubahan% : persentase perubahan harga penutupan hari tersebut dibandingkan dengan hari sebelumnya, yang bermakna jika nilai positif maka IHSG naik dan berlaku sebaliknya

### EDA and Data Visualization

Guna memahami struktur data lebih baik, dilakukan pula beberapa tahapan Exploratory Data Analysis dan Data Visualization, yaitu melihat struktur data menggunakan fungsi info dan melihat persebaran time series data. 

#### Struktur Data

![Struktur Data](![Struktur Data](https://drive.google.com/uc?export=view&id=1YoH2CUd1-SwhdfF6R6L9cO5BLTQh7YZg))

Tampak bahwa tipe data masih berupa objek sehingga perlu dilakukan beberapa pengubahan format, yaitu data "Tanggal" menjadi datetime. Data "Terakhir", "Pembukaan", "Terendah", "Tertinggi", dan "Perubahan%" ke tipe data float.

#### Persebaran Time Series

gambar 

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

### Mengubah Skala Data
Berdasarkan informasi yang telah didapatkan pada EDA, keseluruhan struktur data masih pada data object sehingga perlu melakukan adjusting skala data. Data "Tanggal" akan diubah menjadi datetime, dan data lainnya yang akan digunakan, yaitu data "Terakhir", "Pembukaan", "Tertinggi", "Terendah", dan "Perubahan%" akan diubah menjadi tipe data float. 

gambar

### Train Test Splitting Data
Selanjutnya data akan dibagi menjadi data train dan data test. Data yang tersimpan sebelum pada tanggal 6 September 2024 akan dimasukkan dalam data train sedangkan sisanya akan masuk dalam data test. Data train terdiri dari 80% data sedangkan data test terdiri dari 20% data.

gambar

### Membuat training set 7 time steps 1 output
Pembuatan data ini didasarkan pada ukuran data yang relatif kecil untuk model machine learning sehingga time steps yang dipilih cukup sempit. Model machine learning seperti LSTM, GRU, MLP, dan CNN tidak tahu otomatis urutan waktu di data sehingga kita memberikan informasi berupa bentuk window dari data sebelumnya agar model memperlajari polanya. Selain itu, jika model hanya diberikan 1 titik data, model tidak akan bisa menangkap pola naik-turun, musiman, atau tren. 
7 time steps 1 output maksudnya adalah model menggunakan 7 hari sebelumnya untuk menentukan output pada waktu berikutnya.

## Modeling
(Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.)

### Model 1 : LSTM

LSTM adalah jenis Recurrent Neural Network (RNN) yang dirancang untuk menangani masalah long-term dependency. Model ini efektif dalam memproses data sekuensial seperti deret waktu karena memiliki mekanisme gate (input, forget, output) yang memungkinkan model menyimpan atau melupakan informasi relevan (Fikri & Azzuhri, 2024). 
>>Kelebihan: 
1. Mampu menangani data sekuensial panjang
2. Mengurangi masalah vanishing gradient

>>Kekurangan:
1. Memiliki banyak parameter sehingga waktu pelatihan lebih lama
2. Membutuhkan tuning yang tepat dan cermat agar tidak overfitting


Model LSTM dikonstruksi menggunakan 4 hidden layer yang terdiri dari 2 hidden layer LSTM dan 2 hidden layer Dense. 
Model ini menggunakan oprimizer Adam dan metrics MAE, serta penggunaan callback. Menggunakan callback, model optimum di epoch 47. 

*MODEL LSTM*
lstm_model = Sequential([
    LSTM(50, return_sequences= True, input_shape= (x_train.shape[1], 1)),
    LSTM(64, return_sequences= False),
    Dense(32),
    Dense(16),
    Dense(1)
])

lstm_model.compile(optimizer= 'adam', loss= 'mse' , metrics= ['mean_absolute_error'])
callbacks = [EarlyStopping(monitor= 'loss', patience= 10 , restore_best_weights= True)]
lstm_result = lstm_model.fit(x_train, y_train, epochs= 100, batch_size= 32, callbacks=callbacks)

plot lstm

### Model 2 : GRU

GRU adalah penyempurnaan dan pengembangan dari model LSTM dengan struktur yang lebih sederhana, karena hanya memiliki reset gate dan update gate. Model ini lebih cepat dilatih dibandingkan LSTM, meskipun performanya kerap serupa (Putri & Hidayat, 2024).
>>Kelebihan:
1. Lebih ringan dan cepat dibandingkan LSTM
2. Sering menunjukkan performa serupa di banyak kasus (stabil)

>>Kelemahan:
1. Bisa kurang efektif menangkap pola yang sangat panjang dibanding LSTM
2. Masih rentan overfitting jika tanpa regularisasi

Model GRU dikonstruksi menggunakan 4 hidden layer yang dioptimumkan dengan dropout (0.2). Model ini menggunakan optimizer adam, metrics MAE, dan menggunakan callback.

*MODEL GRU*
model_GRU = Sequential()
model_GRU.add(GRU(32, return_sequences=True, input_shape=(x_train.shape[1], 1)))
model_GRU.add(Dropout(0.2))
model_GRU.add(GRU(64, return_sequences=True))
model_GRU.add(Dropout(0.2))
model_GRU.add(GRU(128, return_sequences=True))
model_GRU.add(Dropout(0.2))
model_GRU.add(GRU(32))
model_GRU.add(Dropout(0.2))
model_GRU.add(Dense(1))
model_GRU.compile(optimizer= 'adam', loss= 'mse' , metrics= ['mean_absolute_error'])

gru_result = model_GRU.fit(x_train, y_train,epochs=100,batch_size=32, callbacks=callbacks)

plot gru

### Model 3 : Multilayer Perceptron

Model Multilayer Perceptron (MLP) adalah jaringan saraf feedforward yang terdiri dari beberapa layer perceptron. Meski tidak dirancang khusus untuk data sekuensial panjang, MLP dapat digunakan pada time series dengan input yang telah diubah ke format window (Saputra & Prasetyo, 2024).
>>Kelebihan:
1. Sederhana dan cepat dilatih
2. Cocok untuk data kecil

>> Kelemahan:
1. Tidak memiliki mekanisme memori seperti LSTM dan GRU, sehingga pola jangka panjang sulit untuk ditangkap
2. Rentan overfitting jika arsitektur terlalu kompleks

Model MLP dikonstruksi menggunakan 3 hidden layer dengan optimizer adam, metrics MAE, dan menggunakan callback.

*MODEL MLP*
model_mlp = Sequential()
model_mlp.add(Dense(64, activation='relu', input_dim=x_train.shape[1]))
model_mlp.add(Dense(128, activation='relu'))
model_mlp.add(Dense(256, activation='relu'))
model_mlp.add(Dense(1))
model_mlp.compile(loss='mse', optimizer="adam", metrics= ['mean_absolute_error'])

callbacks = [EarlyStopping(monitor= 'loss', patience= 10 , restore_best_weights= True)]
mlp_result = model_mlp.fit(x_train, y_train, epochs=100, batch_size=32, callbacks=callbacks)

plot MLP

### Model 4 : CNN

CNN atau Convolutional Neural Network umumnya digunakan untuk pemrosesan data gambar, namun arsitektur 1D-CNN dapat diterapkan untuk menangkap pola lokal dalam data sekuensial seperti time series. CNN menggunakan filter (kernel) untuk mengekstraksi fitur penting (Setiawan & Sari, 2024).

>>Kelebihan:
1. Cepat diproses, cocok untuk menangkap pola lokal
2. Memiliki jumlah parameter lebih sedikit dibanding LSTM/GRU

>>Kelemahan:
1. Kurang mampu menangkap dependensi jangka panjang
2. Memerlukan konfigurasi kernel yang tepat

Model CNN dikonstruksi menggunakan 4 hidden layer dimana layer Conv1D dilanjutkan dengan layer MaxPooling, kemudian layer Flatten, dan Dense Model ini menggunakan optimizer adam, metrics MAE, dan menggunakan callback. Model ini optimum di epoch ke 35

*MODEL CNN*
model_cnn = Sequential()
model_cnn.add(Conv1D(filters=64, kernel_size=2, activation='relu', input_shape=(x_train.shape[1], x_train.shape[2])))
model_cnn.add(MaxPooling1D(pool_size=2))
model_cnn.add(Conv1D(filters=128, kernel_size=2, activation='relu'))
model_cnn.add(MaxPooling1D(pool_size=2))
model_cnn.add(Flatten())
model_cnn.add(Dense(50, activation='relu'))
model_cnn.add(Dense(1))
model_cnn.compile(loss='mse', optimizer="adam",metrics= ['mean_absolute_error'])

callbacks = [EarlyStopping(monitor= 'loss', patience= 10 , restore_best_weights= True)]
cnn_result = model_cnn.fit(x_train, y_train, epochs=100, batch_size=32, callbacks=callbacks)

plot cnn

## Evaluation
(Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.
Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.)

Pada proyek ini saya menggunakan 3 metrik evaluasi, yaitu MSE, RMSE, dan MAE. Semakin kecil metrik evaluasi tersebut, maka semakin baik pula pemodelan yang telah dilakukan. 

Berikut merupakan metrik evaluasi model yang digunakan : 
1. Model LSTM
Training :
Train rmse: 300.04548165679887
MSE: 90027.29106266044
MAE: 252.21878637471332

Testing : 
MSE: 29375.49236464541
RMSE: 171.3928013793036
MAE: 133.07064492984696

2. Model GRU
Training :
Train rmse: 7018.921137285058
MSE: 49265253.931426965
MAE: 7012.505044562663

Testing : 
MSE: 50858552.70849978
RMSE: 7131.518261106802
MAE: 7130.423512078109

3. Model MLP
Training :
Train rmse: 64.70045806346816
MSE: 4186.149273622602
MAE: 51.08824729429473

Testing : 
MSE: 10114.95288389928
RMSE: 100.57312207493253
MAE: 83.26579639668368

4. Model CNN
Training :
Train rmse: 76.25642727276168
MSE: 5815.042700405993
MAE: 58.55357059023795

Testing : 
MSE: 13445.090184706098
RMSE: 115.95296539850155
MAE: 89.64458107461734

Berdasarkan informasi metrik evaluasi yang telah saya terangkan sebelumnya, baik pada data training dan data testing, pemodelan Multilayer Perceptron dan CNN memberikan nilai metrik evaluasi paling kecil. Kedua pemodelan tersebut lebih lanjut akan dilakukan forecasting harga IHSG dengan variasi skenario waktu, yaitu jangka pendek, jangka menengah, dan jangka panjang. 

Adapun penjabaran lengkap mengenai metrik tersebut sebagai berikut:
1. Mean Squared Error (MSE)
MSE menghitung rata-rata dari kuadrat selisih antara nilai aktual (observed) dan nilai prediksi
Kelebihan : menghukum lebih keras jika prediksi meleset jauh, karena kesalahan pengkuadratan
Kelemahan : tidak mudah diinterpretasikan dalam satuan asli data karena satuannya sudah dikuadratkan

gambar

Pada penelitian oleh Fadli & Saputra (2023), MSE digunakan untuk mengevaluasi model prediksi harga saham, menunjukkan bahwa nilai MSE yang lebih kecil mengindikasikan model yang lebih akurat. 

2. Root Mean Squared Error (RMSE)
RMSE adalah akar dari MSE
Kelebihan : mengembalikan nilai ke satuan asli karena telah di akar kuadratkan sehingga lebih mudah untuk dimaknai
Kekurangan : masih sensitif terhadap outlier karena berbasis kuadrat error

gambar 

Pada penelitian yang dilakukan oleh Sidiq (2023), RMSE digunakan untuk mengevaluasi model prediksi penjualan, dengan hasil RMSE yang lebih rendah menunjukkan model yang lebih baik.

3. Mean Absolute Error (MAE)
MAE menghitung rata-rata dari nilai absolut selisih antara nilai aktual dengan nilai prediksi
Kelebihan : lebih robust terhadap outlier karena tidak ada kuadrat
Kekurangan : tidak menghukung kesalahan besar secara ekstra, jadi mungkin kurang sensitif pada kasus dimana outlier memberikan pengaruh penting

gambar

Penelitian yang dilakukan oleh Nisa & Adikara (2024), menggunakan metrik evaluasi MAE dan memberikan informasi bahwa pemodelan dengan nilai MAE lebih kecil memberikan keakuratan prediksi jangka panjang

## Forecasting 

xxx

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

## Daftar Pustaka
Daftar pustaka pada laporan proyek ini menggunakan standar APA

xxx
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

Fadli, M. I., & Saputra, R. (2023). Performance Comparison of Random Forest and Support Vector Regression in Stock Price Prediction. Jurnal Pilar Nusa Mandiri.

Sidiq, B. O. (2023). Evaluating Forecasting Methods for Breast Cancer Reported Cases in Nigeria. Discovery.

Nisa, N. R., & Adikara, M. (2024). Time Series Analysis for Electricity Demand Forecasting: A Comparative Study of ARIMA and Exponential Smoothing Models in Indonesia. ResearchGate.

Fikri, A., & Azzuhri, M. (2024). Perbandingan Model LSTM dan ARIMA untuk Peramalan Harga Komoditas di Indonesia. Jurnal Teknologi Informasi dan Ilmu Komputer (JTIIK), 11(2), 245–256.

Putri, L. A., & Hidayat, R. (2024). Prediksi Data Deret Waktu Menggunakan GRU dan LSTM: Studi Kasus Pada Peramalan Penjualan. Jurnal RESTI, 8(1), 12–20.

Saputra, M., & Prasetyo, E. (2024). Implementasi MLP untuk Peramalan Jumlah Penumpang Transportasi Publik di Indonesia. Jurnal Ilmu Komputer dan Informasi, 17(1), 33–44.

Setiawan, B., & Sari, D. (2024). Penerapan CNN untuk Prediksi Time Series Penjualan E-Commerce. Jurnal Teknologi dan Sistem Komputer, 12(2), 121–130.