# Laporan Proyek Machine Learning - Hanifa Rahmacindia Nasution

## Domain Proyek

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

![Struktur Data](https://drive.google.com/uc?export=view&id=1YoH2CUd1-SwhdfF6R6L9cO5BLTQh7YZg)

Tampak bahwa tipe data masih berupa objek sehingga perlu dilakukan beberapa pengubahan format, yaitu data "Tanggal" menjadi datetime. Data "Terakhir", "Pembukaan", "Terendah", "Tertinggi", dan "Perubahan%" ke tipe data float.

#### Persebaran Time Series

![Plot Time Series Data](https://drive.google.comuc?export=view&id=1ibVrw7y9WGBvQop84aHJryTTp8bewuDV)

![Plot Perubahan Harga Saham IHSG](https://drive.google.com/uc?export=view&id=1ioETcdjW_9tGRz5Gos-WALIfkJ1PVwzK)

## Data Preparation

### Mengubah Skala Data
Berdasarkan informasi yang telah didapatkan pada EDA, keseluruhan struktur data masih pada data object sehingga perlu melakukan adjusting skala data. Data "Tanggal" akan diubah menjadi datetime, dan data lainnya yang akan digunakan, yaitu data "Terakhir", "Pembukaan", "Tertinggi", "Terendah", dan "Perubahan%" akan diubah menjadi tipe data float. Data tersebut perlu diubah menjadi tipe data yang tepat agar dapat dianalisis.

![Struktur Data Setelah Pengubahan Tipe Data](https://drive.google.com/uc?export=view&id=1ZteAPyEvLTRLUiQHiQFY8ts0Zrgw3D0r)

### Train Test Splitting Data
Selanjutnya data akan dibagi menjadi data train dan data test. Data yang tersimpan sebelum pada tanggal 6 September 2024 akan dimasukkan dalam data train sedangkan sisanya akan masuk dalam data test. Data train terdiri dari 80% data sedangkan data test terdiri dari 20% data. Hal ini dilakukan agar dapat mengevaluasi performa model dengan data test nantinya. 

![Splitting Data](https://drive.google.comuc?export=view&id=1g--ToXbA9RXuNYFkbxZex8YN6t9QCaQx)

### Membuat training set 7 time steps 1 output
Pembuatan data ini didasarkan pada ukuran data yang relatif kecil untuk model machine learning sehingga time steps yang dipilih cukup sempit. Model machine learning seperti LSTM, GRU, MLP, dan CNN tidak tahu otomatis urutan waktu di data sehingga kita memberikan informasi berupa bentuk window dari data sebelumnya agar model memperlajari polanya. Selain itu, jika model hanya diberikan 1 titik data, model tidak akan bisa menangkap pola naik-turun, musiman, atau tren. 
7 time steps 1 output maksudnya adalah model menggunakan 7 hari sebelumnya untuk menentukan output pada waktu berikutnya.

![Proses Pembuatan Training Set 7 Time Steps dan 1 Output](https://drive.google.com/uc?export=view&id=1P0YU-lxBuFtpw3gKdBDjfBd8uOWz6r4G)

## Modeling

### Model 1 : LSTM

LSTM adalah jenis Recurrent Neural Network (RNN) yang dirancang untuk menangani masalah long-term dependency. Model ini efektif dalam memproses data sekuensial seperti deret waktu karena memiliki mekanisme gate (input, forget, output) yang memungkinkan model menyimpan atau melupakan informasi relevan (Milniadi & Adiwijaya, 2023). 
>>Kelebihan: 
1. Mampu menangani data sekuensial panjang
2. Mengurangi masalah vanishing gradient

>>Kekurangan:
1. Memiliki banyak parameter sehingga waktu pelatihan lebih lama
2. Membutuhkan tuning yang tepat dan cermat agar tidak overfitting

Model LSTM dikonstruksi menggunakan 4 hidden layer yang terdiri dari 2 hidden layer LSTM dan 2 hidden layer Dense. 
Model ini menggunakan oprimizer Adam dan metrics MAE, serta penggunaan callback. Menggunakan callback, model optimum di epoch 47. 

*MODEL LSTM*
```
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
```

![Plot Loss LSTM](https://drive.google.com/uc?export=view&id=1Mw0y2wqVCqi0_bDQLBERVauT_JBGSR-t)

### Model 2 : GRU

GRU adalah penyempurnaan dan pengembangan dari model LSTM dengan struktur yang lebih sederhana, karena hanya memiliki reset gate dan update gate. Model ini lebih cepat dilatih dibandingkan LSTM, meskipun performanya kerap serupa (Sofi et al., 2021).
>>Kelebihan:
1. Lebih ringan dan cepat dibandingkan LSTM
2. Sering menunjukkan performa serupa di banyak kasus (stabil)

>>Kelemahan:
1. Bisa kurang efektif menangkap pola yang sangat panjang dibanding LSTM
2. Masih rentan overfitting jika tanpa regularisasi

Model GRU dikonstruksi menggunakan 4 hidden layer yang dioptimumkan dengan dropout (0.2). Model ini menggunakan optimizer adam, metrics MAE, dan menggunakan callback.

*MODEL GRU*
```
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
```

![Plot Loss GRU](https://drive.google.com/uc?export=view&id=1ut5owaZeNk0fLfueIl8U0-0XmkJVGuSY)

### Model 3 : Multilayer Perceptron

Model Multilayer Perceptron (MLP) adalah jaringan saraf feedforward yang terdiri dari beberapa layer perceptron. Meski tidak dirancang khusus untuk data sekuensial panjang, MLP dapat digunakan pada time series dengan input yang telah diubah ke format window (Ramadhan & Saputra, 2023).
>>Kelebihan:
1. Sederhana dan cepat dilatih
2. Cocok untuk data kecil

>> Kelemahan:
1. Tidak memiliki mekanisme memori seperti LSTM dan GRU, sehingga pola jangka panjang sulit untuk ditangkap
2. Rentan overfitting jika arsitektur terlalu kompleks

Model MLP dikonstruksi menggunakan 3 hidden layer dengan optimizer adam, metrics MAE, dan menggunakan callback.

*MODEL MLP*
```
model_mlp = Sequential()
model_mlp.add(Dense(64, activation='relu', input_dim=x_train.shape[1]))
model_mlp.add(Dense(128, activation='relu'))
model_mlp.add(Dense(256, activation='relu'))
model_mlp.add(Dense(1))
model_mlp.compile(loss='mse', optimizer="adam", metrics= ['mean_absolute_error'])

callbacks = [EarlyStopping(monitor= 'loss', patience= 10 , restore_best_weights= True)]
mlp_result = model_mlp.fit(x_train, y_train, epochs=100, batch_size=32, callbacks=callbacks)
```

![Plot Loss MLP](https://drive.google.com/uc?export=view&id=1GR0jaeBrJr3GHBCOpqaaVfzmqmSV6RzC)

### Model 4 : CNN

CNN atau Convolutional Neural Network umumnya digunakan untuk pemrosesan data gambar, namun arsitektur 1D-CNN dapat diterapkan untuk menangkap pola lokal dalam data sekuensial seperti time series. CNN menggunakan filter (kernel) untuk mengekstraksi fitur penting (Julianto et al., 2024).

>>Kelebihan:
1. Cepat diproses, cocok untuk menangkap pola lokal
2. Memiliki jumlah parameter lebih sedikit dibanding LSTM/GRU

>>Kelemahan:
1. Kurang mampu menangkap dependensi jangka panjang
2. Memerlukan konfigurasi kernel yang tepat

Model CNN dikonstruksi menggunakan 4 hidden layer dimana layer Conv1D dilanjutkan dengan layer MaxPooling, kemudian layer Flatten, dan Dense Model ini menggunakan optimizer adam, metrics MAE, dan menggunakan callback. Model ini optimum di epoch ke 35

*MODEL CNN*
```
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
```

![Plot Loss CNN](https://drive.google.com/uc?export=view&id=1dDJFMepsMoZoicIKDFDxAsGSDvclmFJk)

## Evaluation

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

Berdasarkan informasi metrik evaluasi yang telah saya terangkan sebelumnya, baik pada data training dan data testing, pemodelan *Multilayer Perceptron dan CNN* memberikan nilai metrik evaluasi paling kecil. Kedua pemodelan tersebut lebih lanjut akan dilakukan forecasting harga IHSG dengan variasi skenario waktu, yaitu jangka pendek, jangka menengah, dan jangka panjang. 

Adapun penjabaran lengkap mengenai metrik tersebut sebagai berikut:
1. Mean Squared Error (MSE)
MSE menghitung rata-rata dari kuadrat selisih antara nilai aktual (observed) dan nilai prediksi
Kelebihan : menghukum lebih keras jika prediksi meleset jauh, karena kesalahan pengkuadratan
Kelemahan : tidak mudah diinterpretasikan dalam satuan asli data karena satuannya sudah dikuadratkan

![MSE](https://drive.google.com/uc?export=view&id=1OynYitE3773UVgIUs9TDEXKpvOLGLMqw)

Pada penelitian oleh Urrochman et al. (2023), MSE digunakan untuk mengevaluasi model prediksi harga saham, menunjukkan bahwa nilai MSE yang lebih kecil mengindikasikan model yang lebih akurat. 

2. Root Mean Squared Error (RMSE)
RMSE adalah akar dari MSE
Kelebihan : mengembalikan nilai ke satuan asli karena telah di akar kuadratkan sehingga lebih mudah untuk dimaknai
Kekurangan : masih sensitif terhadap outlier karena berbasis kuadrat error

![RMSE](https://drive.google.com/uc?export=view&id=1UbAdgkkvaO0J3wxRkgnEr36mllegjMkf) 

Pada penelitian yang dilakukan oleh Ben & Dolapo (2019), RMSE digunakan untuk mengevaluasi model prediksi penjualan, dengan hasil RMSE yang lebih rendah menunjukkan model yang lebih baik.

3. Mean Absolute Error (MAE)
MAE menghitung rata-rata dari nilai absolut selisih antara nilai aktual dengan nilai prediksi
Kelebihan : lebih robust terhadap outlier karena tidak ada kuadrat
Kekurangan : tidak menghukung kesalahan besar secara ekstra, jadi mungkin kurang sensitif pada kasus dimana outlier memberikan pengaruh penting

![MAE](https://drive.google.com/uc?export=view&id=14EXM4rz-6U6xYsqM5hkZZD2MprtFwH3m)

Penelitian yang dilakukan oleh Nugraha (2024), menggunakan metrik evaluasi MAE dan memberikan informasi bahwa pemodelan dengan nilai MAE lebih kecil memberikan keakuratan prediksi jangka panjang

## Forecasting 

Sesuai dengan problem statement pada proyek ini, akan dilakukan forecasting harga saham pada berbagai skenario waktu yang dapat memberikan informasi saham kedepan dan menjadi alarm dini bagi pemerintah untuk menentukan kebijakan selanjutnya. Model terbaik yang didapat pada proyek ini adalah *model MLP dan CNN* sehingga forecasting akan dilakukan pada 2 model tersebut. 

### Forecasting Model MLP

#### Jangka Pendek (3 Hari Kedepan)

Berdasarkan model MLP, prediksi harga saham 3 hari kedepan adalah :
Hari ke-1 -> 6800.8330078125
Hari ke-2 -> 6819.2861328125
Hari ke-3 -> 6859.5498046875

#### Jangka Menengah (7 Hari Kedepan)

Berdasarkan model MLP, prediksi harga saham 7 hari kedepan adalah :
Hari ke-1 -> 6800.8330078125
Hari ke-2 -> 6819.2861328125
Hari ke-3 -> 6859.5498046875
Hari ke-4 -> 6885.9833984375
Hari ke-5 -> 6888.646484375
Hari ke-6 -> 6884.03955078125
Hari ke-7 -> 6900.15625

#### Jangka Panjang (2 Minggu atau 14 Hari Kedepan)

Berdasarkan model MLP, prediksi harga saham 3 hari kedepan adalah :
Hari ke-1 -> 6800.8330078125
Hari ke-2 -> 6819.2861328125
Hari ke-3 -> 6859.5498046875
Hari ke-4 -> 6885.9833984375
Hari ke-5 -> 6888.646484375
Hari ke-6 -> 6884.03955078125
Hari ke-7 -> 6900.15625
Hari ke-8 -> 6922.34521484375
Hari ke-9 -> 6930.58984375
Hari ke-10 -> 6936.45849609375
Hari ke-11 -> 6947.33935546875
Hari ke-12 -> 6961.296875
Hari ke-13 -> 6973.2939453125
Hari ke-14 -> 6982.63671875

### Forecasting Model CNN

#### Jangka Pendek (3 Hari Kedepan)

Berdasarkan model CNN, prediksi harga saham 3 hari kedepan adalah :
Hari ke-1 -> 6742.41796875
Hari ke-2 -> 6782.2060546875
Hari ke-3 -> 6802.50439453125

#### Jangka Menengah (7 Hari Kedepan)

Berdasarkan model CNN, prediksi harga saham 7 hari kedepan adalah :
Hari ke-1 -> 6742.41796875
Hari ke-2 -> 6782.2060546875
Hari ke-3 -> 6802.50439453125
Hari ke-4 -> 6802.78662109375
Hari ke-5 -> 6799.08447265625
Hari ke-6 -> 6790.09130859375
Hari ke-7 -> 6770.15771484375

#### Jangka Panjang (2 Minggu atau 14 Hari Kedepan)

Berdasarkan model CNN, prediksi harga saham 3 hari kedepan adalah :
Hari ke-1 -> 6742.41796875
Hari ke-2 -> 6782.2060546875
Hari ke-3 -> 6802.50439453125
Hari ke-4 -> 6802.78662109375
Hari ke-5 -> 6799.08447265625
Hari ke-6 -> 6790.09130859375
Hari ke-7 -> 6770.15771484375
Hari ke-8 -> 6756.8154296875
Hari ke-9 -> 6758.7861328125
Hari ke-10 -> 6753.48388671875
Hari ke-11 -> 6743.31884765625
Hari ke-12 -> 6733.04150390625
Hari ke-13 -> 6723.05126953125
Hari ke-14 -> 6715.27978515625

## Kesimpulan Hasil Forecasting

Forecasting menggunakan pemodelan MLP cukup stabil dan nampak memberikan informasi bahwa harga saham akan terus meningkat, sedankan pemodelan CNN memberikan harga saham yang fluktuatif dan harga terus turun. Mempertimbangkan data historis terdekat beberapa waktu lalu, model CNN tampak lebih baik menangkap fluktuasi harga saham daripada model MLP. Hal ini juga membuktikan bahwa MLP tidak memiliki mekanisme memori sehingga cukup sulit menangkap pola data meskipun metrik evaluasinya kecil. 

## Saran Penelitian Selanjutnya

Forecasting harga saham tidak bisa hanya didasarkan pada data saham itu sendiri, perlu data lain, mengingat fluktuasi harga saham dipengaruhi oleh banyak faktor. Oleh karena itu, proyek penelitian selanjutnya disarankan menggunakan multivariate time series sehingga memberikan hasil lebih relevan dan reliabel.

## Daftar Pustaka
Daftar pustaka pada laporan proyek ini menggunakan standar APA, kecuali sumber berita yang digunakan pada latar belakang kemudian daftar pustaka sudah terurut sesuai abjad.
Format sumber berita ditulis sebagai berikut.
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

[Anggaran pendidikan dasar dan menengah dipangkas Rp8 triliun – Bagaimana nasib guru honorer dan program pembangunan sekolah?] (https://www.bbc.com/indonesia/articles/ckgxe99qyzno)

Ben, S. O., & Dolapo, D. K. (2019). Evaluating forecasting methods for breast cancer reported cases in Nigeria. License This work is licensed under a Creative Commons Attribution 4.0 International License., 55(286), 540-556. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Evaluating+Forecasting+Methods+for+Breast+Cancer+Reported+Cases+in+Nigeria&btnG=)

[Cara Membaca IHSG dengan Sederhana: Kapan Tren Naik dan Turun] (https://www.tempo.co/ekonomi/cara-membaca-ihsg-dengan-sederhana-kapan-tren-naik-dan-turun-1230677)

[IHSG Anjlok, Apa Dampaknya bagi Indonesia?] (https://www.kompas.com/tren/read/2025/03/20/074500865/ihsg-anjlok-apa-dampaknya-bagi-indonesia-)

[IHSG Anjlok, Apa saja Kemungkinan Dampaknya terhadap Pendapatan dan Belanja Pemerintah?] (https://djpb.kemenkeu.go.id/kppn/jakarta6/id/data-publikasi/berita-terbaru/2912-dampak-penurunan-ihsg-terhadap-pendapatan-dan-pengeluaran-pemerintah.html)

Julianto, M. F., Iqbal, M., Hidayat, W. F., & Malau, Y. (2024). PERBANDINGAN PENERAPAN ALGORITMA DEEP LEARNING DALAM PREDIKSI HARGA EMAS. INTI Nusa Mandiri, 19(1), 71-76. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=PERBANDINGAN+PENERAPAN+ALGORITMA+DEEP+LEARNING+DALAM+PREDIKSI+HARGA+EMAS&btnG=)

Milniadi, A. D., & Adiwijaya, N. O. (2023). Analisis perbandingan model arima dan lstm dalam peramalan harga penutupan saham (studi kasus: 6 kriteria kategori saham menurut peter lynch). SIBATIK JOURNAL: Jurnal Ilmiah Bidang Sosial, Ekonomi, Budaya, Teknologi, dan Pendidikan, 2(6), 1683-1692. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=ANALISIS+PERBANDINGAN+MODEL+ARIMA+DAN+LSTM+DALAM+PERAMALAN+HARGA+PENUTUPAN+SAHAM+%28STUDI+KASUS+%3A+6+KRITERIA+KATEGORI+SAHAM+MENURUT+PETER+LYNCH%29&btnG=)

Nugraha, R. I. (2024). Time Series Analysis for Electricity Demand Forecasting: A Comparative Study of ARIMA and Exponential Smoothing Models in Indonesia. Information Technology International Journal, 2(2). (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Time+Series+Analysis+for+Electricity+Demand+Forecasting%3A+A+Comparative+Study+of+ARIMA+and+Exponential+Smoothing+Models+in+Indonesia&btnG=)

Ramadhan, A. F., & Saputra, R. A. (2023). Prediksi Jumlah Penumpang Bandar Udara Halu Oleo Kendari Menggunakan Multi-layer Perceptron. JOINTER: Journal of Informatics Engineering, 4(02), 33-38. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Prediksi+Jumlah+Penumpang+Bandar+Udara+Halu+Oleo+Kendari+Menggunakan+Multi-layer+Perceptron&btnG=)

Sofi, K., Sunge, A. S., Riady, S. R., & Kamalia, A. Z. (2021). Perbandingan algoritma linear regression, LSTM, dan GRU dalam memprediksi harga saham dengan model time series. PROSIDING SEMINASTIKA, 3(1), 39-46. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Perbandingan+algoritma+linear+regression%2C+LSTM%2C+dan+GRU+dalam+memprediksi+harga+saham+dengan+model+time+series&btnG=)

Urrochman, M. Y., Asy'ari, H., & Hizham, F. A. (2025). PERFORMANCE COMPARISON OF RANDOM FOREST REGRESSION, SVR MODELS IN STOCK PRICE PREDICTION. Jurnal Pilar Nusa Mandiri, 21(1), 16-23. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=PERFORMANCE+COMPARISON+OF+RANDOM+FOREST+REGRESSION%2C+SVR+MODELS+IN+STOCK+PRICE+PREDICTION&btnG=)

**---Ini adalah bagian akhir laporan---**