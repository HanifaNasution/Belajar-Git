# Laporan Proyek Machine Learning Kedua (Sistem Rekomendasi) - Hanifa Rahmacindia Nasution

## Project Overview

Seiring dengan berkembangnya industri hiburan digital, jumlah konten film dan serial yang tersedia di berbagai platform seperti Netflix, Disney+, dan Amazon Prime semakin melimpah. Meskipun kondisi ini memberikan banyak pilihan kepada pengguna, hal tersebut juga menimbulkan masalah baru, yakni kesulitan dalam memilih film yang sesuai dengan preferensi pribadi. Dalam konteks ini, sistem rekomendasi (recommender system) menjadi salah satu solusi penting untuk membantu pengguna menemukan konten yang relevan secara cepat dan efisien.

Sistem rekomendasi bekerja dengan menganalisis data pengguna, seperti riwayat tontonan, ulasan, atau rating, untuk menyarankan film yang kemungkinan besar disukai oleh pengguna tersebut. Terdapat beberapa pendekatan utama dalam pengembangan sistem rekomendasi, antara lain content-based filtering, collaborative filtering, dan hybrid methods yang menggabungkan keduanya. Menurut Desrosiers et al. (2011), sistem rekomendasi telah terbukti meningkatkan keterlibatan pengguna dan mendorong konsumsi konten yang lebih luas.

Urgensi pengembangan sistem rekomendasi film juga terlihat dari bagaimana perusahaan-perusahaan besar memanfaatkan teknologi ini untuk mempertahankan pelanggan dan meningkatkan waktu tonton. Netflix, misalnya, mengklaim bahwa lebih dari 80% film yang ditonton penggunanya berasal dari sistem rekomendasi yang mereka sediakan. Ini menunjukkan bahwa sistem rekomendasi bukan hanya alat bantu, melainkan elemen inti dari strategi bisnis dalam industri hiburan digital.

Selain itu, perkembangan teknologi machine learning dan big data telah membuka peluang baru dalam menyempurnakan akurasi dan personalisasi sistem rekomendasi. Penelitian oleh Aggarwal (2016) menekankan bahwa pemanfaatan algoritma pembelajaran mesin yang kompleks dapat meningkatkan kualitas prediksi dalam sistem rekomendasi.

Dengan latar belakang tersebut, proyek ini bertujuan untuk mengembangkan sistem rekomendasi film yang mampu memberikan rekomendasi secara akurat berdasarkan preferensi pengguna. Sistem ini diharapkan dapat memberikan nilai tambah baik bagi pengguna maupun penyedia layanan streaming, sekaligus menjadi kontribusi dalam pengembangan teknologi kecerdasan buatan di bidang hiburan.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:

- Bagaimana cara merekomendasikan film yang disukai oleh pengguna berdasarkan pada data film yang pernah ditonton (kemiripan film yang pernah ditonton oleh pengguna dengan film lainnya) oleh pengguna tersebut?
- Bagaimana cara merekomendasikan film yang disukai oleh pengguna berdasarkan pada film yang pernah ditonton dan direkomendasikan oleh pengguna lain?

### Goals

Menjelaskan tujuan dari pernyataan masalah:

- Membuat sistem rekomendasi film yang mampu merekomendasikan film tertentu berdasarkan pada data film yang pernah ditonton oleh pengguna 
- Membuat sistem rekomendasi film yang mampu merekomendasikan film tertentu berdasarkan pada rekomendasi film pengguna lainnya

### Solution statements

Solusi yang digunakan untuk mencapai tujuan dari pernyataan masalah adalah menggunakan:

- Content Based Filtering, yaitu algoritma yang merekomendasikan item serupa dengan item yang pernah disukai oleh pengguna. Memanfaatkan aktivitas pengguna di masa lalu. (untuk mencapai tujuan 1)
- Collaborative Filtering, yaitu algoritma yang memanfaatkan pendapat atau rekomendasi pengguna lainnya. Memanfaatkan pendapat pengguna lainnya (untuk mencapai tujuan 2)

## Data Understanding
Data yang digunakan pada proyek ini merupakan dataset tentang film yang dapat diakses pada [Kaggle](https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data). Data ini terdiri dari 4 dataset, yaitu links, movies, ratings, dan tags yang lebih lanjut akan dijelaskan pada penjelasan variabel nantinya. Secara keseluruhan terdapat 9742 data film dengan 610 pengguna. Total terdapat 285761 baris data (sebelum preprocess). 

### Variabel-variabel pada Dataset Rekomendasi Film adalah sebagai berikut:

1. Dataset Links, terdiri dari variabel :
- movieID : kode ID unik tiap film yang tampaknya digenerate tanpa ada keunikan tertentu karena hanya berupa data integer dimulai dari 1
- imdbID : ID film menurut Internet Movie Database
- tmdbID : ID film menurut The Movie Database

2. Dataset Movies, terdiri dari variabel :
- movieID : kode ID unik tiap film yang tampaknya digenerate tanpa ada keunikan tertentu karena hanya berupa data integer dimulai dari 1
- title : judul film
- genres : genre film

3. Dataset Ratings, terdiri dari variabel :
- userID : kode ID unik tiap user yang tampaknya digenerate tanpa ada keunikan tertentu karena hanya berupa data integer dimulai dari 1
- movieID : kode ID unik tiap film yang tampaknya digenerate tanpa ada keunikan tertentu karena hanya berupa data integer dimulai dari 1
- rating : rating film yang diberikan oleh user dengan rentang nilai dari 1-5
- timestamp : pencatatan waktu ketika user memberikan rating

4. Dataset Tags, terdiri dari variabel :
- userID : kode ID unik tiap user yang tampaknya digenerate tanpa ada keunikan tertentu karena hanya berupa data integer dimulai dari 1
- movieID : kode ID unik tiap film yang tampaknya digenerate tanpa ada keunikan tertentu karena hanya berupa data integer dimulai dari 1
- tag : review singkat pengguna tentang film tersebut
- timestamp : pencatatan waktu ketika user memberikan tag

### EDA and Data Visualization

Guna memahami struktur data lebih baik, dilakukan pula beberapa tahapan Exploratory Data Analysis dan Data Visualization, yaitu melihat struktur data menggunakan fungsi info dan melihat bagaimana persebaran datanya

1. Dataset Links

    **Insight Dataset Links :** 

    Dataset links hanya berisikan data ID.

    Namun, karena variabel lainnya yaitu imdbId dan tmdbId tidak terdapat di dataset lainnya, maka dataset links tidak terlalu berguna sehingga tidak digunakan dalam proyek sistem rekomendasi ini.

2. Dataset Movies 

    **Insight Dataset Movies :**
    1. Dataset movies terdiri dari 9742 film dengan 951 kombinasi genre yang bersigat unik (saya katakan kombinasi karena dalam 1 film dapat terdapat beberapa genre)
    2. Film yang terdapat pada dataset tersebut didominasi oleh film bergenre "Drama" sebanyak 1053 film
    3. Terdapat keanehan pada informasi "top" variabel title karena informasi tersebut berisi "Emma (1996)" kemudian informasi "freq" yang menghitung banyaknya kemunculan data mayoritas menunjukkan bahwa "top" variabel title muncul sebanyak 2 kali, diindikasikan terdapat duplikat film "Emma (1996)" pada dataset movies -> akan dilakukan pengecekan lebih lanjut pada bagian pengecekan data duplikat

3. Dataset Ratings
    **Insight Dataset Ratings :**
    1. Rating total yang diberikan oleh seluruh users pada film terdapat sebanyak 100836 data
    2. Rata-rata rating yang diberikan oleh users sebesar 3.501557 atau 3.52 (pembulatan) yang berarti mayoritas film mendapatkan respon positif dari users
    3. Terdapat keanehan pada informasi "min" dari variabel rating. Nilai "min" pada rating berada pada nilai "0.5" padahal nilai rating seharusnya berada pada interval 1-5 saja -> perlu dilakukan pengecekan lebih lanjut dan akan dilakukan penanganan pada bagian pengecekan data invalid

    ![Data Invalid](https://drive.google.com/uc?export=view&id=1-J6zjsJz7J8jFUyJffXuFM80gzOdu54v)

    Tampak bahwa banyak rating yang aneh, misalnya 0,5 dan lainnya (bukan bilangan bulat antara 1-5)

4. Dataset Tags
    **Insight Dataset Tags :**
    1. Tag yang diberikan oleh users pada dataset tags tampak seperti review singkat atau top of mind review terhadap film yang ditonton oleh pengguna
    2. Total terdapat 3683 data tags
    3. Tags yang paling banyak muncul adalah "In Netflix queue" yang berarti film tersebut dalam antrian tontonan pengguna yang dapat dimaknai bahwa film tersebut cukup populer dan diminati oleh pengguna. Tags tersebut muncul sebanyak 131 kali

## Data Preparation dan Preprocessing

### Membuat Dataset Movies ALL

Proses ini bertujuan untuk menggabungkan ketiga dataset (movies, ratings, dan tags) menggunakan data movieID dan didapat informasi bahwa jumlah keseluruhan film berdasarkan data movieID sejumlah 9742 film.

### Membuat Dataset Users ALL

Proses ini bertujuan untuk menggabungkan dataset yang memiliki data users. Pada proyek ini data yang mengandung data users adalah dataset ratings dan tags. Dataset Users akan dibentuk dengan menggabungkan kedua dataset tersebut menggunakan data userID. Berdasarkan proses ini didapatkan terdapat 610 users.

### Membuat Dataset Gabungan dari Dataset Movies ALL dan Users ALL

Dataset ini dibentuk untuk mendapatkan dataframe secara keseluruhan yang nantinya akan masuk dalam proses modelling. 

```
full = pd.concat([movies, ratings, tags])
full = pd.merge(ratings, full , on='movieId', how='left')
```

Terdapat banyak informasi yang diperoleh ketika mengeksplorasi dataset gabungan ini. Misalnya, rata-rata rating pada suatu film 

```
full.groupby('movieId').mean(numeric_only=True)
```

Menggunakan kode diatas akan didapatkan hasil sebagai berikut 

![Tabel Agregat Film yang Mampu Memberikan Informasi Rataan Rating Tiap Film](https://drive.google.com/uc?export=view&id=14sqVRcM0k-fd9MFHepg2V3SQMdVFcYfZ)

Namun, hasil gabungan tersebut tidak seperti yang diharapkan, karena terlalu banyak data NULL dan sangat sulit dilakukan penanganan karena menghapus terlalu banyak data sehingga dibuat data gabungan dengan cara lain sebagai berikut 

```
all_movie_rate = pd.merge(ratings, movies[['movieId','title','genres']], on='movieId', how='left')
all_movie = pd.merge(all_movie_rate, tags[['movieId','tag']], on='movieId', how='left')
```

Data ini cukup baik karena tampak tidak terlalu banyak data NULL namun lebih lengkapnya akan ditinjau pada bagian "Pengecekan Missing Values"

### Pengecekan Missing Values 

Tahapan ini dilakukan untuk mendeteksi data NULL dan memberikan penanganan yang tepat terhadap data NULL tersebut

```
all_movie.isnull().sum()
```

![Data NULL](https://drive.google.com/uc?export=view&id=1KfJB--l4H0J0mnZKhPVV8av5hJLsWkKj)

Tampak bahwa seluruh variabel tidak terdapat data NULL kecuali variabel tag. Terdapat missing value yang sangat banyak pada variabel tag sebanyak 52549 data

Variabel tag berupa string dan bersifat unik didasarkan pada preferensi pengguna sehingga akan sulit untuk dilakukan imputasi data, mengingat data yang digunakan cukup banyak, maka akan dilakukan penghapusan data NULL saja

Setelah penghapusan terdapat 233213 baris data dari yang sebelumnya sebanyak 285762 baris data

### Pengecekan Data Duplikat

Pengecekan ini diperlukan untuk menghapus data yang duplikat persis, misalnya user memberikan rating berulang kali pada film yang sama dengan nilai rating yang sama 

Karena sama persis maka informasi ini dianggap tidak berguna dan lebih baik dihapus

```
all_movie_clean.duplicated().sum()
```

Didapatkan 13807 data duplikat dan akan dihapus

### Pengecakan Data Invalid

Pengecekan ini untuk mengonfirmasi temuan rating yang bernilai 0,5 (bukan bilangan bulat namun desimal).

![Distribusi Rating Film](https://drive.google.com/uc?export=view&id=1-J6zjsJz7J8jFUyJffXuFM80gzOdu54v)

Tampak bahwa data rating berada pada rentang 0 - 5 dengan selisih tiap data point terdekat adalah 0,5

Diasumsikan bahwa terdapat 10 kategori nilai rating, misal seharusnya 1-10 tapi dari dataset dikonversi dalam rentang 0-5 dengan selisih 0,5 

Oleh karena itu, tiap data rating yang diberikan pengguna bersifat valid dan tidak akan dilakukan penghapusan data

### Membuat Dictionary Film dengan Genrenya

Akan dibuat dictionary berupa :
* ID = movieID
* Movie Name = movie_name
* Genre = movie_genre

Dictionary ini dibuat dengan tujuan agar memberikan output pemodelan yang terstruktur, yaitu output berupa ID, Movie Name, dan Genre film tersebut

```
# Mengonversi data series ‘movieId’ menjadi dalam bentuk list
movie_id = all_movie_clean['movieId'].tolist()
 
# Mengonversi data series ‘title’ menjadi dalam bentuk list
movie_name = all_movie_clean['title'].tolist()
 
# Mengonversi data series ‘genres’ menjadi dalam bentuk list
movie_genre = all_movie_clean['genres'].tolist()
 
print(len(movie_id))
print(len(movie_name))
print(len(movie_genre))
```

Kode di atas telah mengubah dataset dalam bentuk list namun masih terjadi duplikat sehingga beberapa baris berisi film yang sama mengingat 1 film mendapat rating dan tags dari banyak pengguna sehingga selanjutnya akan dipilih yang unik saja

```
movie_dict = pd.DataFrame({
    'id': movie_id,
    'movie_name': movie_name,
    'genre': movie_genre
})
movie_fix = movie_dict.drop_duplicates()
```

Didapatkan bahwa data film sebanyak 1553 film (bersifat unik)

## Modeling

Pemodelan sistem rekomendasi film ini akan terdiri dari 2 pendekatan, yaitu :
1. Content Based Filtering 
2. Collaborative Based Filtering

### Model Development dengan Content Based Filtering

Model Content Based Filtering memberikan rekomendasi yang didasarkan pada kemiripan item tersebut dengan item yang pernah diakses oleh pengguna

>>Kelebihan :
1. Personalisasi Tinggi
    Memberikan rekomendasi berdasarkan preferensi unik masing-masing pengguna, tanpa bergantung pada data pengguna lain.
2. Tidak Terpengaruh oleh Popularitas
    Mampu merekomendasikan item yang kurang populer asalkan sesuai dengan preferensi pengguna.
3. Mengatasi Masalah Cold Start untuk Item Baru
    Dapat merekomendasikan item baru yang belum memiliki rating karena menggunakan atribut konten item tersebut

>> Kekurangan :
1. Kurangnya Keanekaragaman (Serendipity): 
    Cenderung merekomendasikan item yang mirip dengan yang sudah disukai, sehingga mengurangi kemungkinan penemuan item baru yang berbeda.
2. Ketergantungan pada Kualitas Data Atribut: 
    Jika data deskriptif item tidak lengkap atau tidak akurat, kualitas rekomendasi dapat menurun.
3. Kesulitan dalam Menangani Data Non-Tekstual: 
    Ekstraksi fitur dari data seperti gambar, audio, atau video memerlukan teknik yang lebih kompleks.

Berikut merupakan proses modelling Content Based Filtering yang dilakukan pada proyek ini : 

#### TF-IDF Vectorizer

Akan dilakukan TF-IDF Vectorizer yang didasarkan pada genre film tersebut sehingga pada pemodelan content based filtering, rekomendasi yang diberikan menyesuaikan dengan genre film yang pernah ditonton pengguna sebelumnya

TF-IDF didasarkan pada genre film karena content based filtering dibangun berdasarkan preferensi genre

```
# Inisialisasi TfidfVectorizer
Tf = TfidfVectorizer()

# Melakukan perhitungan idf pada data genre
Tf.fit(movie_fix['genre'])

# Mapping array dari fitur index integer ke fitur nama
Tf.get_feature_names_out()
```

Dengan hasil sebagai berikut 

```
array(['action', 'adventure', 'animation', 'children',     'comedy', 'crime',
       'documentary', 'drama', 'fantasy', 'fi', 'film', 'genres',
       'horror', 'imax', 'listed', 'musical', 'mystery', 'no', 'noir',
       'romance', 'sci', 'thriller', 'war', 'western'], dtype=object)
```

Kemudian disimpan dalam matrix 

Selanjutnya akan dilihat bagaimana nilai tf-idf pada data nama film berdasarkan genre filmnya, misal film hanya genre drama maka akan mendapat nilai genre drama = 1 dan lainnya = 0

Jika dalam film tersebut terdapat lebih dari 1 genre maka nilai totalnya akan berupa 1 dan didapatkan probabilitas yang mengikuti rumusan tf-idf

![Hasil TF-IDF Film Berdasarkan Genre](https://drive.google.com/uc?export=view&id=1z7BUOuNSOJcDeNWpC52sjFL-l-DdA1Pu)

#### Cosine Similarity 

Cosine Similarity digunakan untuk menghitung derajat kesamaan suatu film dengan film lainnya

Cosine similarity dikonstruksi dari matriks TF-IDF yang telah didapatkan sebelumnya

```
cosine_sim = cosine_similarity(tfidf_matrix) 
```

Selanjutnya kita dapat melihat kedekatan atau kemiripan satu film dengan film lainnya

```
cosine_sim_df = pd.DataFrame(cosine_sim, index=movie_fix['movie_name'], columns=movie_fix['movie_name'])
print('Shape:', cosine_sim_df.shape)
 
cosine_sim_df.sample(5, axis=1).sample(10, axis=0)
```

![Hasil Cosine Similarity](https://drive.google.com/uc?export=view&id=1fX9GVtXchC1nV84rThY459o0cp6lELfk)

#### Mendapatkan Rekomendasi Content Based Filtering

Akan didapatkan rekomendasi film sebanyak 10 buah berdasarkan genre yang ditonton pengguna

```
def movie_recommendations(movie_name, similarity_data=cosine_sim_df, items=movie_fix[['movie_name', 'genre']], k=10):
   
 
    # Mengambil data dengan menggunakan argpartition untuk melakukan partisi secara tidak langsung sepanjang sumbu yang diberikan    
    # Dataframe diubah menjadi numpy
    # Range(start, stop, step)
    index = similarity_data.loc[:,movie_name].to_numpy().argpartition(
        range(-1, -k, -1))
    
    # Mengambil data dengan similarity terbesar dari index yang ada
    closest = similarity_data.columns[index[-1:-(k+2):-1]]
    
    # Drop nama_movie agar nama movie yang dicari tidak muncul dalam daftar rekomendasi
    closest = closest.drop(movie_name, errors='ignore')
 
    return pd.DataFrame(closest).merge(items).head(k)
```

Makna parameter :
* Nama Movie = Nama film yang akan dicari kesamaannya dengan film lainnya 
* Similarity Data = matriks cosine similarity 
* Items = Data yang akan dicocokan dengan Nama Movie menggunakan matriks cosine similarity
* k = rekomendasi sebanyak-n

```
movie_fix[movie_fix['movie_name'] == 'Spider-Man (2002)']
```

![Film yang akan Dicari Rekomendasinya](https://drive.google.com/uc?export=view&id=1wyuDPXW1goaDtuGEM_b82R_N-QPQNtFT)

Film Spider-Man (2002) memiliki genre Action|Adventure|Sci-Fi|Thriller sehingga dengan sistem rekomendasi content based filtering akan dicari film dengan genre serupa

```
movie_recommendations('Spider-Man (2002)')
```

![Hasil 10 TOP Rekomendasi Menggunakan Content Based Filtering](https://drive.google.com/uc?export=view&id=1G_-ZAf1aJReAxMEa0FkM4CFsjqpNDj16)

Didapatkan 10 rekomendasi film dengan 9 film teratas memiliki genre yang sesuai dengan film Spider-Man (2002) sedangkan 1 film sisanya yaitu X-Men (2000) memiliki genre Action|Adventure|Scifi

Film tersebut tidak memiliki genre yang persis sama dengan Spider-Man (2002) namun masih cukup relevan (hanya nggak ada genre Thriller saja)

### Model Development dengan Collaborative Filtering

Model Collaborative Based Filtering merupakan model rekomendasi yang memberikan rekomendasi item tertentu pengguna berdasarkan preferensi pengguna yang mirip dengan pengguna tersebut 

>>Kelebihan :
1. Menangkap Preferensi Kolektif
    Mampu merekomendasikan item berdasarkan kesamaan preferensi antar pengguna, seringkali menghasilkan rekomendasi yang tidak terduga namun relevan.
2. Tidak Memerlukan Informasi Detail Item
    Beroperasi efektif tanpa perlu data deskriptif item, hanya berdasarkan interaksi pengguna.
3. Skalabilitas Baik
    Dapat diterapkan pada berbagai domain tanpa perlu penyesuaian signifikan pada data item

>>Kekurangan :
1. Masalah Cold Start
    Kesulitan memberikan rekomendasi untuk pengguna atau item baru yang belum memiliki interaksi atau rating.
2. Data Sparsity
    Dalam dataset besar, interaksi pengguna-item yang jarang dapat mengurangi akurasi rekomendasi.
3. Ketergantungan pada Partisipasi Pengguna
    Membutuhkan data interaksi yang cukup dari pengguna untuk menghasilkan rekomendasi yang akurat.

Berikut merupakan proses modelling Collaborative Based Filtering yang dilakukan pada proyek ini : 

#### Data Preprocessing (khusus untuk model Collaborative Filtering)

Pada proses ini akan dikontruksi dataset yang cocok untuk Collaborative Filtering, yaitu memanfaatkan dataset rating yang telah diberikan oleh pengguna lainnya

```
# Mengubah userID menjadi list tanpa nilai yang sama
users_id = ratings['userId'].unique().tolist()
print('list userID: ', users_id)
 
# Melakukan encoding userID
user_to_user_encoded = {x: i for i, x in enumerate(users_id)}
print('encoded userID : ', user_to_user_encoded)
 
# Melakukan proses encoding angka ke ke userID
user_encoded_to_user = {i: x for i, x in enumerate(users_id)}
print('encoded angka ke userID: ', user_encoded_to_user)
```

Kode diatas mengubah data usersID menjadi list agar mudah dicari data uniknya dan mudah dijadikan dataframe untuk collaborative filtering selanjutnya

```
# Mengubah movieId menjadi list tanpa nilai yang sama
movie_ids = all_movie_clean['movieId'].unique().tolist()
 
# Melakukan proses encoding movieId
movie_to_movie_encoded = {x: i for i, x in enumerate(movie_ids)}
 
# Melakukan proses encoding angka ke movieId
movie_encoded_to_movie = {i: x for i, x in enumerate(movie_ids)}
 
# Selanjutnya, petakan userId dan movieId ke dataframe yang berkaitan.
 
# Mapping userId ke dataframe genres
ratings['genres'] = ratings['userId'].map(user_to_user_encoded)
 
# Mapping movieD ke dataframe movies
ratings['movies'] = all_movie_clean['movieId'].map(movie_to_movie_encoded)
```

Kode diatas mengubah data movieID menjadi list agar mudah dicari data uniknya dan mudah dijadikan dataframe untuk collaborative filtering selanjutnya

#### Membagi Data Training dan Testing

Dataset akan dibagi menjadi 70% data training dan 30% data testing

Namun, sebelumnya akan dilakukan pengecekan terlebih dahulu untuk menghindari adanya kemungkinan dependensi urutan atau sebagai salah satu cara untuk menghindari bias urutan

```
df = ratings.sample(frac=1, random_state=94)

# Membuat variabel x untuk mencocokkan data genres  dan movies menjadi satu value
x = df[['genres', 'movies']].values
 
# Membuat variabel y untuk membuat ratings dari hasil 
y = df['ratings'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values
 
# Membagi menjadi 70% data train dan 30% data testing
train_indices = int(0.7 * df.shape[0])
x_train, x_val, y_train, y_val = (
    x[:train_indices],
    x[train_indices:],
    y[:train_indices],
    y[train_indices:]
)
 
print(x, y)
```

#### Training Model Menggunakan RecommenderNet

Proses training akan memanfaatkan model dari tensorflow 

```
import tensorflow as tf

class RecommenderNet(tf.keras.Model):
 
  # Insialisasi fungsi
  def __init__(self, num_users, num_movie, embedding_size, **kwargs):
    super(RecommenderNet, self).__init__(**kwargs)
    self.num_users = num_users
    self.num_movie = num_movie
    self.embedding_size = embedding_size
    self.user_embedding = layers.Embedding( # layer embedding user
        num_users,
        embedding_size,
        embeddings_initializer = 'he_normal',
        embeddings_regularizer = keras.regularizers.l2(1e-6)
    )
    self.user_bias = layers.Embedding(num_users, 1) # layer embedding user bias
    self.movie_embedding = layers.Embedding( # layer embeddings movies
        num_movie,
        embedding_size,
        embeddings_initializer = 'he_normal',
        embeddings_regularizer = keras.regularizers.l2(1e-6)
    )
    self.movie_bias = layers.Embedding(num_movie, 1) # layer embedding movies bias
 
  def call(self, inputs):
    user_vector = self.user_embedding(inputs[:,0]) # memanggil layer embedding 1
    user_bias = self.user_bias(inputs[:, 0]) # memanggil layer embedding 2
    movie_vector = self.movie_embedding(inputs[:, 1]) # memanggil layer embedding 3
    movie_bias = self.movie_bias(inputs[:, 1]) # memanggil layer embedding 4
 
    dot_user_movie = tf.tensordot(user_vector, movie_vector, 2) 
 
    x = dot_user_movie + user_bias + movie_bias
    
    return tf.nn.sigmoid(x) # activation sigmoid

class myCallback(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
    if logs.get('root_mean_squared_error') is not None and logs['root_mean_squared_error'] < 0.2:
      print("\nRMSE sudah sangat rendah. Stop training!")
      self.model.stop_training = True
callbacks = myCallback()
```

Kemudian model dicompile agar dapat digunakan

```
model = RecommenderNet(num_users, num_movie, 10) # inisialisasi model
 
# model compile
model.compile(
    loss = tf.keras.losses.BinaryCrossentropy(),
    optimizer = keras.optimizers.Adam(learning_rate=0.001),
    metrics=[tf.keras.metrics.RootMeanSquaredError()]
)
```

Setelah dilakukan compile, model sudah siap untuk dicoba pada data training 

```
history = model.fit(
    x = x_train,
    y = y_train,
    batch_size = 128,
    epochs = 100,
    validation_data = (x_val, y_val),
    callbacks = callbacks
)
```
#### Mendapatkan Rekomendasi Collaborative Based Filtering

Setelah dilakukan training, maka dapat dilakukan prediksi hasil rekomendasi menggunakan tambahan kode berikut

```
movie_df = movie_fix
df = ratings
 

user_id = df.userId.sample(1).iloc[0]
movie_watched_by_user = df[df.userId == user_id]
 

movie_not_watched = movie_df[~movie_df['id'].isin(movie_watched_by_user.movieId.values)]['id'] 
movie_not_watched = list(
    set(movie_not_watched)
    .intersection(set(movie_to_movie_encoded.keys()))
)
 
movie_not_watched = [[movie_to_movie_encoded.get(x)] for x in movie_not_watched]
user_encoder = user_to_user_encoded.get(user_id)
user_movie_array = np.hstack(
    ([[user_encoder]] * len(movie_not_watched), movie_not_watched)
)
```

Kemudian menggunakan kode berikut juga 

```
ratings = model.predict(user_movie_array).flatten()
 
top_ratings_indices = ratings.argsort()[-10:][::-1]
recommended_movie_ids = [
    movie_encoded_to_movie.get(movie_not_watched[x][0]) for x in top_ratings_indices
]
 
print('Showing recommendations for users: {}'.format(user_id))
print('===' * 9)
print('movie with high ratings from user')
print('----' * 8)
 
top_movie_user = (
    movie_watched_by_user.sort_values(
        by = 'rating',
        ascending=False
    )
    .head(5)
    .movieId.values
)
 
movie_df_rows = movie_df[movie_df['id'].isin(top_movie_user)]
for row in movie_df_rows.itertuples():
    print(row.movie_name, ':', row.genre)
 
print('----' * 8)
print('Top 10 movie recommendation')
print('----' * 8)
 
recommended_movie = movie_df[movie_df['id'].isin(recommended_movie_ids)]
for row in recommended_movie.itertuples():
    print(row.movie_name, ':', row.genre)
```

Akhirnya didapatkan hasil rekomendasi berikut

![Rekomendasi TOP 10 Collaborative Based Filtering](https://drive.google.com/uc?export=view&id=1ytV8XpV4sr_u3Ta7MB9VHWowJepF6Xeb)

Hasil di atas menunjukkan hasil rekomendasi yang akan diberikan pada pengguna 

Salah satu hasilnya, pengguna ID ke 42 memberikan rating tinggi pada film Clerks (1994) dengan genre Comedy dan Scarface (1983) dengan genre Action|Crime|Drama kemudian sistem memberikan rekomendasi 10 film paling relevan mempertimbangkan dari rekomendasi pengguna lain dengan mencocokkan informasi rating dan preferensi yang diberikan oleh pengguna 

## Evaluation

### Evaluasi Content Based Filtering

Evaluasi pada model Content Based Filtering menggunakan metrik precision dengan rumusan berikut 

![Rumus Precision Sistem Rekomendasi](https://drive.google.com/uc?export=view&id=1UOszSSnpPJoyGhvqzFWGIzdNA2AkJhuk)

Precision menghitung jumlah kesesuaian sistem rekomendasi dengan membandingkan jumlah kemunculan rekomendasi yang sesuai dengan total rekomendasi yang diberikan oleh sistem

Berdasarkan hasil rekomendasi pada bagian sebelumnya, didapatkan hasil bahwa 9 dari 10 film hasil rekomendasi memiliki genre yang sama persis dengan film Spider-Man(2002) yaitu genre Action|Adventure|Scifi|Thriller sehingga precision sistem rekomendasi film ini sebesar 9/10 atau 90% yang mana model ini bekerja dengan sangat baik dalam merekomendasikan film yang sesuai dengan genre yang disukai oleh pengguna

### Evaluasi Collaborative Based Filtering

Evaluasi pada model Collaborative Based Filtering menggunakan metrik evaluasi RMSE 

RMSE adalah akar dari MSE
  
Kelebihan : mengembalikan nilai ke satuan asli karena telah di akar kuadratkan sehingga lebih mudah untuk dimaknai
  
Kekurangan : masih sensitif terhadap outlier karena berbasis kuadrat error

![RMSE](https://drive.google.com/uc?export=view&id=1UbAdgkkvaO0J3wxRkgnEr36mllegjMkf) 

Penggunaan RMSE sebagai metrik evaluasi juga digunakan pada penelitian lain contohnya penelitian Syah (2020) tentang [Performa Algoritma User K-Nearest Neighbors pada Sistem Rekomendasi di Tokopedia] (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Performa+Algoritma+User+K-Nearest+Neighbors+pada+Sistem+Rekomendasi+di+Tokopedia&btnG=)

```
plt.plot(history.history['root_mean_squared_error'])
plt.plot(history.history['val_root_mean_squared_error'])
plt.title('model_metrics')
plt.ylabel('root_mean_squared_error')
plt.xlabel('epoch')
plt.legend(['train', 'test'], loc='upper left')
plt.show()
```

![Plot Loss](https://drive.google.com/uc?export=view&id=1RtlYr_XqVRONkdpQ4QMHciBMdtb-QYz2)

Tampak dari plot bahwa loss dari data training dan testing sama sama kecil sekitar 0.612 sehingga dapat disimpulkan bahwa tidak terdapat overfitting atau dalam artian lainnya model mampu menggeneralisasi hasil dengan baik dan memberikan rekomendasi secara akurat dan relevan 

Kemudian metrik RMSE juga bernilai kecil baik pada evaluasi metrik data training maupun data testing di kisaran angka 0,213 sehingga dapat disimpulkan model bekerja dengan baik

## Simpulan 

Kedua pendekatan memiliki kelebihan dan kekurangan sendiri tetapi memiliki kesamaan kekurangan yaitu permasalahan cold start

Penelitian lainnya memberikan informasi bahwa terdapat pendekatan lainnya yang lebih andal, yaitu pendekatan Hybrid yang mana menggabungkan model Content Based Filtering dengan Collaborative Filtering. Misalnya pada penelitian Arfisko et al. (2022). Oleh karena itu, disarankan proyek ini lebih lanjut menggunakan pendekatan Hybrid untuk mengoptimalkan sistem rekomendasi yang telah dibangun

## Daftar Pustaka
Daftar pustaka ditulis menggunakan format APA

Aggarwal, C. C. (2016). Recommender systems (Vol. 1). Cham: Springer International Publishing. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=%5B3%5D+C.+C.+Aggarwal%2C+Recommender+Systems%3A+The+Textbook%2C+Springer%2C+2016&btnG=)

Arfisko, H. H., & Wibowo, A. T. (2022). Sistem Rekomendasi Film Menggunakan Metode Hybrid Collaborative Filtering Dan Content-Based Filtering. eProceedings of Engineering, 9(3). (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Sistem+Rekomendasi+Film+Menggunakan+Metode+Hybrid+Collaborative+Filtering+Dan+Content-based+Filtering.&btnG=)

Desrosiers, C., Karypis, G., Ricci, F., Rokach, L., Shapira, B., & Kantor, P. B. (2011). Recommender Systems Handbook. In ch. A Comprehensive Survey of Neighborhood-based Recommendation Methods. Springer. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=F.+Ricci%2C+L.+Rokach%2C+B.+Shapira%2C+and+P.+B.+Kantor%2C+Recommender+Systems+Handbook%2C+Springer%2C+2011.&btnG=)

Syah, R. D. (2020). Performa Algoritma User K-Nearest Neighbors pada Sistem Rekomendasi di Tokopedia. Jurnal Informatika Universitas Pamulang, 5(3), 302-306. (https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=Performa+Algoritma+User+K-Nearest+Neighbors+pada+Sistem+Rekomendasi+di+Tokopedia&btnG=)

**---Ini adalah bagian akhir laporan---**