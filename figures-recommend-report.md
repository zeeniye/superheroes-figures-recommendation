# Laporan Proyek Machine Learning - Muhammad Difagama Ivanka

## Project Overview

<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/59215827/138017796-b083cf9c-1610-4d14-8287-b3efe152cc73.png">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/59215827/138018614-de84c049-e638-49b7-8078-633f68ff3a26.png"><br>
  <sup><sub><a href="https://www.pxfuel.com/en/free-photo-xtdqo"><i>image source</i></a></sub></sup>
  <sup><sub><a href="https://www.flickr.com/photos/levork/4966756896"><i>image source</i></a></sub></sup>
</p>

Penggemar cerita superhero tentu sudah mengenal dengan adanya dua *universe* fiksi populer yaitu [**Marvel *Universe***](https://www.marvel.com/explore) dan [**DC *Universe***](https://www.dccomics.com/). Adanya cerita superhero tersebut terutama bagi seorang yang merupakan warga kebangsaan Amerika Serikat sudah menjadi suatu budaya dan peradaban bagi kehidupan sehari-hari yang tidak dapat dilepaskan. [<sup>1</sup>](https://scholarship.richmond.edu/cgi/viewcontent.cgi?article=2397&context=honors-theses) Perkembangan cerita superhero yang berawal dari komik dan kemudian mulai banyak diadaptasi ke dalam perfilman atau media lainnya lantas menjadikan cerita ini semakin populer bahkan hingga ke seluruh penjuru dunia. [<sup>2</sup>](https://core.ac.uk/download/pdf/61661616.pdf) Dalam perjalanan keduanya telah menjadi perdebatan panjang sebagai rival tentang siapa yang terbaik di antara keduanya baik dalam aspek superhero itu sendiri maupun jalan cerita dalam komik dan atau media lainnya. [<sup>3</sup>](https://www.qualitycomix.com/learn/marvelvdc#:~:text=While%20both%20comics%20publishers%20present,Batman)

Perdebatan tersebut tidak terkecuali juga memiliki pengaruh terhadap orang yang juga menggemari tokoh superhero dalam dua cerita tersebut didalam menentukan *action figures* siapakah yang akan dibeli atau dikumpulkan. Tentu bagi seorang yang memiliki dana besar akan sangat mudah baginya untuk dapat membeli keseluruhan *figures* tersebut tanpa peduli dengan syarat khusus. Namun berdasarkan data dari diantaranya empat *marketplace* populer yaitu [Amazon](https://www.amazon.com/Superhero-figures/s?k=Superhero+figures), [eBay](https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2499334.m570.l1313&_nkw=superhero+action+figures&_sacat=220), [Tokopedia](https://www.tokopedia.com/find/action-figure-super-hero), dan [Shopee](https://shopee.co.id/search?keyword=superhero%20figures) menunjukkan rata-rata hanya superhero populer saja baik itu berdasarkan cerita dalam komik, film, atau media lainnya yang terdapat dalam katalog penjualan, serta semakin populer superhero tersebut akan semakin diminati untuk dibeli. 

Hal ini selain akan menyulitkan bagi penggemar yang akan mengoleksi juga akan dapat mengurangi keuntungan dari pihak pemilik cerita karena penikmat memiliki kecenderungan untuk menyukai hanya karakter superhero yang populer saja walaupun nantinya akan ada superhero dengan jalan cerita jauh lebih bagus dan menarik serta kekuatan yang unik tidak akan dapat menarik minat mereka. Oleh karena itu dibuatkan sebuah sistem rekomendasi yang dapat membantu menyelesaikan permasalahan tersebut. Diharapkan hasil rekomendasi dapat membantu karakter-karakter yang jarang terekspos terutama dikarenakan kurang populer menjadi digemari banyak pihak. Sehingga dapat membantu pihak pemilik cerita dalam meningkatkan keuntungan serta dapat memudahkan bagi seseorang dalam menentukan siapa saja karakter superhero favoritnya terlebih bagi pengoleksi *action figures*nya.

---
<sub><sup>1. Lydia Dubois. (2019). Superheroes and "the American way" : popular culture, national identity, and American notions of heroism and leadership. Honors Theses. 1380.</sup></sub><br>
<sub><sup>2. Alex Brundige. (2015). The Rise of Marvel and DC's Transmedia Superheroes: Comic Book Adaptations, Fanboy Auteurs, and Guiding Fan Reception. Electronic Thesis and Dissertation Repository. 3104.</sup></sub><br>
<sub><sup>3. Brent Moeshlin. (2021). QUALITYCOMIX: What is the difference between Marvel and DC?</sup></sub>

## Business Understanding
Bagian ini menjelaskan proses klarifikasi masalah dengan mengajukan beberapa solusi dalam menyelesaikannya.

### Problem Statements
Berangkat dari *overview* tersebut, maka rincian masalah yang dapat diselesaikan diantaranya:
1. Apa **sistem rekomendasi** yang paling baik dan sesuai untuk diterapkan pada proyek ini?
2. Bagaimana cara membuat **sistem rekomendasi** tersebut agar dapat merekomendasikan karakter superhero terbaik bagi pengoleksi *action figures*?

### Goals
Berikut merupakan tujuan dibuatnya proyek ini:
1. Memilih serta membuat sistem rekomendasi karakter superhero yang baik dan sesuai bagi pengoleksi *action figures*.
2. Merekomendasikan setidaknya lima karakter superhero terbaik yang mungkin juga disukai oleh pengoleksi *action figures*.

### Solution approach
Solusi yang dapat diterapkan untuk mencapai tujuan tersebut diantaranya:
- Memilih sistem rekomendasi [*content-based filtering*](https://codeburst.io/explanation-of-recommender-systems-in-information-retrieval-13077e1d916c) yang memiliki kesesuaian dengan dataset dimana tidak harus memerlukan adanya informasi dari sang pengoleksi *action figures*. Kemudian sebelum dilakukan pembuatan sistem rekomendasi, dataset akan dilakukan proses *preparation* terlebih dahulu dan setelahnya akan ditampilkan hasil rekomendasi yang ada (jika memungkinkan juga akan dievaluasi seberapa baik hasil rekomendasi tersebut).
- Memilih dua algoritma yang diajukan dalam sistem rekomendasi tersebut, yaitu:
  * Algoritma `Nearest Neighbors (NN)` yang menerapkan jarak **Jaccard**. 
    
    Algoritma ini dipilih mengingat kesederhanaan dalam penggunaan, kemudian karena permasalahan berkaitan dengan *unsupervised learning* (fleskibel sehingga dapat digunakan padanya) serta penggunaan jarak dimaksudkan untuk dataset yang memiliki fitur [*binary*](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.DistanceMetric.html#sklearn.neighbors.DistanceMetric). Cara kerja algoritma adalah dengan menemukan jumlah beberapa *neighbors* terdekat dari suatu titik baru untuk kemudian menentukan termasuk dari kelompok mana titik tersebut. [<sup>4</sup>](https://scikit-learn.org/stable/modules/neighbors.html#unsupervised-neighbors)
    
    <img width="450" height="450" src="https://user-images.githubusercontent.com/59215827/138034285-7088c8b9-5700-4749-a337-463e140a6133.png"><br>
    <sup><sub><a href="https://towardsdatascience.com/9-distance-measures-in-data-science-918109d069fa"><i>image source</i></a></sub></sup>
    
    Sedangkan jarak Jaccard sebagaimana pada gambar di atas, membandingkan anggota pada dua set untuk melihat anggota yang terbagi atau yang terdapat perbedaan. Jarak ini memiliki rentang dari 0% hingga 100% dengan semakin tinggi persentasenya, maka semakin mirip kedua populasi tersebut. Meskipun mudah diinterpretasikan, namun penggunaan jarak ini sangat sensitif terhadap ukuran sampel kecil dan dapat memberikan hasil yang salah, terutama pada sampel sangat kecil atau kumpulan data dengan pengamatan yang hilang. [<sup>5</sup>](https://www.statisticshowto.com/jaccard-index/) Cara kerja jarak Jaccard adalah dengan mendapatkan dua anggota yang beririsan dan membaginya dengan gabungan dari dua anggota tersebut. [<sup>6</sup>](https://towardsdatascience.com/9-distance-measures-in-data-science-918109d069fa)
    
  * Algoritma `Cosine Similarity`.
    
    <img width="450" height="450" src="https://user-images.githubusercontent.com/59215827/138036908-ab9768df-0fa2-4b4d-81d8-6718b1cbea77.png"><br>
    <sup><sub><a href="https://towardsdatascience.com/9-distance-measures-in-data-science-918109d069fa"><i>image source</i></a></sub></sup>

    Algoritma ini sebagaimana pada gambar di atas menghitung persamaan antara dua vektor sesuai dengan sudut kosinus di antara keduanya. Memiliki keunggulan dalam kemudahan interpretasi, pada ruang multidimensi bekerja baik akibat penghitungan yang berdasarkan sudut, dan mampu menangkap hal yang mungkin dideteksi sangat berbeda pada jarak [Euclidian](https://www.cuemath.com/euclidean-distance-formula/). [<sup>7</sup>](https://www.geeksforgeeks.org/cosine-similarity/)

---
<sub><sup>4. sklearn. (2021). "1.6. Nearest Neighbors".</sup></sub><br>
<sub><sup>5. Stephanie. (2016). statisticshowto: Jaccard Index / Similarity Coefficient.</sup></sub><br>
<sub><sup>6. Maarten Grootendorst. (2021). towardsdatascience: 9 Distance Measures in Data Science.</sup></sub><br>
<sub><sup>7. Sharadarao. (2020). geeksforgeeks: Cosine Similarity.</sup></sub>

## Data Understanding
Berikut merupakan informasi datasets yang digunakan:

Detail | Keterangan
-- | --
Source | [Kaggle: FiveThirtyEight Comic Characters Dataset](https://www.kaggle.com/fivethirtyeight/fivethirtyeight-comic-characters-dataset)
License | [Public (CC0 1.0)](https://creativecommons.org/publicdomain/zero/1.0/)
Domain | Superheroes, Figures, Fantasy
Data | dc-wikia-data.csv & marvel-wikia-data.csv
Size | < 4 MB

Dengan preview singkat dataset sebagai berikut:

![image](https://user-images.githubusercontent.com/59215827/138038489-a96af1a4-f64f-4220-8447-c1b914f4cbc5.png)
<sub>
  "origins" merupakan kolom tambahan yang nanti baru akan dilakukan di proses <i>preparation</i>
</sub>

### Fitur-fitur pada datasets
Datasets berisi sebanyak ±23000 baris dan 13 fitur menunjukkan informasi tentang karakter superhero pada komik baik itu [DC](https://dc.fandom.com/wiki/DC_Comics_Database) atau [Marvel](https://marvel.fandom.com/wiki/Marvel_Database) yang terakhir diperbarui pada tanggal 02 September 2014. Selengkapnya penjelasan fitur pada datasets:  

No | Fitur | Rincian
-- | -- | --
1.| `page_id` | ID unik yang menunjukkan halaman dimana karakter muncul pada wikia (*integer*)
2.| `name` | Nama dari superhero (*string*)
3 | `urlslug` | URL unik yang mengarahkan ke halaman wikia superhero (*string*)
4 | `ID` | Status identitas karakter (*string*)
5 | `ALIGN` | Menunjukkan apakah karakter baik, villain, atau netral (*string*)
6 | `EYE` | Warna/tipe mata superhero (*string*)
7 | `HAIR` | Warna/tipe rambut superhero (*string*)
8 | `SEX` | Jenis kelamin superhero (*string*)
9 | `GSM` | Orientasi seksual superhero (*string*)
10 | `ALIVE` | Menunjukkan apakah superhero masih hidup atau tidak (*string*)
11 | `APPEARANCES` | Menunjukkan jumlah kemunculan superhero pada komik (*float*)
12 | `FIRST APPEARANCE` | Bulan dan tahun pertama kali kemunculan superhero pada komik (*string*)
13 | `YEAR` | Tahun kemunculan pertama kali superhero pada komik (*float*)

<sub>
* Keterangan tambahan:
  Data karakter superhero DC terdapat pada file "dc-wikia-data.csv" sedangkan superhero Marvel pada "marvel-wikia-data.csv".
</sub>

### Visualisasi data pada fitur *categorical*
![newplot (6)](https://user-images.githubusercontent.com/59215827/138041464-d0a52377-d670-4ea4-a678-1b1052053062.png)
![newplot (7)](https://user-images.githubusercontent.com/59215827/138041508-0a99f54a-303a-4cc0-83aa-fc8739e4a2b5.png)
![newplot (8)](https://user-images.githubusercontent.com/59215827/138041595-a3beb7bb-9969-4b53-9405-5b57ebe4916a.png)
![newplot (9)](https://user-images.githubusercontent.com/59215827/138041665-c07f06e9-3133-432d-a739-8f20ca7183c8.png)
![newplot (10)](https://user-images.githubusercontent.com/59215827/138041676-b8fece96-7508-47db-b108-7a1c1425e528.png)
![newplot (11)](https://user-images.githubusercontent.com/59215827/138041694-e2186924-d9f9-4945-be8d-546a2277b819.png)
![newplot (12)](https://user-images.githubusercontent.com/59215827/138041724-ddebbf0c-0970-4545-8304-d6402c5ef6e4.png)
![newplot (13)](https://user-images.githubusercontent.com/59215827/138041763-7f181179-1b6e-4c31-9aef-4d0a9c305a1f.png)

### Visualisasi data pada fitur *continuous*
![newplot (14)](https://user-images.githubusercontent.com/59215827/138041949-9e552502-2976-456e-b644-3da826e43251.png)

### Visualisasi distribusi data yang menunjukkan *relationships* beberapa fitur
![image](https://user-images.githubusercontent.com/59215827/138042055-dc25caf9-1d00-452b-be94-86a0985fcead.png)
![image](https://user-images.githubusercontent.com/59215827/138042093-3a0e6d04-3496-402e-953f-3089699e5929.png)
![image](https://user-images.githubusercontent.com/59215827/138042130-c2221df7-786f-40d7-bc25-8276edd68a74.png)
![image](https://user-images.githubusercontent.com/59215827/138042187-88a0790a-2231-40f9-8614-b80a580d7796.png)
![image](https://user-images.githubusercontent.com/59215827/138042231-6a29b375-5509-4077-9b06-53c8f1941217.png)

---

## Data Preparation
Bagian ini terbagi menjadi dua yaitu *`data preprocessing`* dan *`data wrangling`*:
### ***Data Preprocessing***
Proses *preparation* yang dilakukan langsung setelah data mentah diambil sebelum dilakukan proses *exploratory*.
* Menambahkan fitur asal superhero

  Hal ini dilakukan karena data dari kedua superhero terpisah, sehingga perlu ditambahkan fitur yang dapat menunjukkan asalnya.
  
* Menggabungkan dataset DC dan Marvel
  
  Untuk memudahkan didalam pembuatan sistem rekomendasi, maka kedua dataset tersebut digabungkan menjadi satu dengan melakukan proses *concat* berdasarkan baris (tentu setelah dipastikan bahwa fitur-fitur yang ada terutama penamaan adalah sama.
  
* Menangani NaN Values pada dataset
![image](https://user-images.githubusercontent.com/59215827/138044521-e13ccde8-3c24-4005-b91e-b5a884bd4f0a.png)

  Sebagaimana ditunjukkan pada gambar di atas bahwa terdapat beberapa fitur yang memiliki Nan values padanya. Untuk itu dilakukan beberapa cara didalam menangani Nan values tersebut:
  
  * *Drop* fitur: Proses dengan menghilangkan fitur akibat terlalu banyaknya nilai NaN seperti yang terdapat pada *GSM* yang jika dilakukan proses lainnya dapat mengakibatkan distorsi pada data (dengan alasan lain juga bersamaan dengan fitur *page_id* dan *urlslug* dihilangkan karena tidak memberikan informasi yang dibutuhkan oleh sistem rekomendasi).
  * *Drop* baris pada fitur: Proses ini dilakukan terhadap fitur *APPEARANCES*, *FIRST APPEARANCE*, *YEAR*, dan *ALIVE* dimana penghapusan baris berdasarkan nilai Nan yang terdeteksi pada keempat fitur tersebut dikarenakan tidak memungkinkannya dilakukan pengisian (*impute*) dengan nilai baru (dapat mengakibatkan salah interpretasi) serta jumlah yang tidak terlalu banyak didalam mempengaruhi keseluruhan data.
  * *Impute* dengan kategori *others*: Pada fitur-fitur tersisa dilakukan pengisian dengan nilai *others* yang menunjukkan bahwa itu adalah kategori lain.

* Membuat fitur *MONTH*

  Untuk menambahkan informasi agar lebih memperkuat hasil sistem rekomendasi, maka diambil dari fitur *FIRST APPERANCE* informasi berupa bulan yang pertama kali sang superhero muncul pada komik. Kemudian dilakukan proses penyamaan format nama pada fitur *MONTH* ini. Terakhir pada informasi yang tidak sesuai (seperti hanya berisi tahun) akan dihilangkan baris berdasarkan hal ini dengan alasan tidak dapat dilakukan apapun dan jumlahnya yang tidak begitu besar (`freq <1000`).
  
* *Formatting* kategori fitur
  Langkah terakhir pada *preprocessing* adalah memperbaiki kelas dari fitur *categorical* lainnya agar lebih rapi dan sesuai untuk diinterpretasikan sistem yaitu:
  * Fitur `ID`: Mengubah kelas '*others*' menjadi '*Identity Unknown*' dan mengubah kelas '*Known to Authorities Identity*' menjadi '*Secret Identity*' karena memiliki makna yang kurang lebih sama.
  * Fitur `ALIGN`: Mengubah kelas '*Reformed Criminals*' menjadi '*others*'.
  * Fitur `SEX`: Memasukkan kelas yang memiliki frekuensi (dengan *threshold*) kurang dari 50 menjadi '*others*'.
  * Fitur `EYE`: Memasukkan kelas yang memiliki frekuensi (dengan *threshold*) kurang dari 100 menjadi '*rare*', hal ini dibedakan dengan hasil pengisian Nan Values untuk menghindari adanya kemungkinan bias yang dapat ditimbulkan.
  * Fitur `HAIR`: Mengganti kelas '*Bald*' menjadi '*No Hair*' karena memiliki arti sama, serta memasukkan kelas yang memiliki frekuensi (dengan *threshold*) kurang dari 100 menjadi '*rare*', hal ini dibedakan dengan hasil pengisian Nan Values untuk menghindari adanya kemungkinan bias yang dapat ditimbulkan.

### ***Data Wrangling***
Proses *preparation* yang dilakukan setelah dataset dilakukan proses *exploratory* untuk menyesuaikan agar dapat membuat sistem rekomendasi yang baik.
* *Discretize* fitur *APPEARANCES*

  Proses mengubah fitur *continuous* ke dalam bentuk *categorical* yang dilakukan untuk memenuhi kebutuhan penggunaan algoritma berbasis jarak (semua fitur dalam bentuk *binary*). Pada fitur *`APPEARANCES`* proses ini dilakukan dengan tetap mempertahankan jumlah di bawah tiga puluh ([*inclusive*](https://www.merriam-webster.com/dictionary/inclusive#:~:text=Definition%20of%20inclusive%201%20a%20%3A%20broad%20in,of%20all%20humankind%2C%20not%20just%20an%20elite%20few.)). Adapun jumlah di atas batas tersebut akan dilakukan proses [*binning*](https://towardsdatascience.com/data-preprocessing-with-python-pandas-part-5-binning-c5bd5fd1b950) yaitu menjadikan fitur ke dalam suatu interval dikarenakan frekuensi yang cukup sedikit.
  
* *Discretize* fitur *YEAR*

  Proses yang sama seperti pada fitur *APPEARANCES* sebelumnya. Namun pada fitur *`YEAR`* ini dilakukan proses ***binning*** terhadap keseluruhan default data dengan interval tahun sekitar lima (ada lebih dari sepuluh pada data terlampau lama dan juga yang memiliki frekuensi sedikit di lima belas tahun belakang).
  
* *One-hot* seluruh fitur
  
  Menjadikan seluruh fitur ke dalam *categorical* tidaklah cukup guna menggunakan beberapa jarak yang ada pada algoritma sebagaimana telah disampaikan pada bagian ***Solution Approach*** sebelumnya. Sehingga keseluruhan fitur tersebut perlu dikonversi ke dalam bentuk *binary* dengan menerapkan metode [*one-hot encoding*](https://machinelearningmastery.com/how-to-one-hot-encode-sequence-data-in-python/#:~:text=A%20one%20hot%20encoding%20is,is%20marked%20with%20a%201.) yang dapat mengeluarkan setiap kelas yang terdapat pada setiap fitur menjadi suatu fitur baru yang dilambangkan dengan *True* atau *False* (*binary*).

---

## Modeling
Data yang telah dilakukan *preparation* kemudian dilakukan pembuatan sistem rekomendasi content based filtering dengan mengajukan karakter yang diambil dari masing-masing *origins* yaitu DC dan Marvel.

* Algoritma **Nearest Neighbors (NN) - jarak Jaccard**

  Mengimplementasikan *library* [NearestNeighbors (sklearn)](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.NearestNeighbors.html) dengan parameter metrik yaitu Jaccard. Selanjutnya *library* model tersebut diinisiasikan untuk kemudian dilakukan fitting terhadap dataset. Setelah itu dengan bantuan fungsi `get_recommended_heroes` akan diberikan rekomendasi terhadap beberapa superhero terbaik (dalam hal ini sebanyak 5) berdasarkan superhero yang disukai atau telah dimiliki oleh pengoleksi ***action figures*** sebagai kemungkinan superhero yang juga mungkin disukai olehnya. Adapun, hasil rekomendasinya adalah:
  
  ![image](https://user-images.githubusercontent.com/59215827/138208430-4ce0c010-8981-4dc4-8acb-d9d3311d5847.png)
  ![image](https://user-images.githubusercontent.com/59215827/138208229-0a985fec-a584-4956-b920-2d1ec4b3388f.png)

* Algoritma **Cosine Similarity**

  Proses dengan algoritma ini juga masih menggunakan fungsi bantuan yang sama (`get_recommended_heroes`). Akan tetapi selain dengan tidak digunakannya model, juga dataset perlu dilakukan proses penghitungan Cosine Similarity terlebih dahulu untuk kemudian mendapatkan hasil rekomendasi dengan bantuan fungsi tersebut. Adapun, hasil rekomendasinya adalah:
  
  ![image](https://user-images.githubusercontent.com/59215827/138208149-8bcea7ef-b6b6-42bc-8214-11f606397289.png)
  ![image](https://user-images.githubusercontent.com/59215827/138208185-5f0834c1-de15-4bd8-9e89-ab4c092798ff.png)

---

## Evaluation
Metrik yang digunakan dalam permasalahan ini adalah **Silhouette Coefficient**, **Calinski & Harabasz score**, dan **Davies-Bouldin score** dengan melakukan pendekatan dari setiap hasil rekomendasi algoritma (terdapat 5 hasil rekomendasi) akan diberikan label berdasarkan superhero acuan (Aquaman atau Captain America). Kemudian nama-nama superhero hasil rekomendasi tersebut (beserta [*ground truth*](https://towardsdatascience.com/in-ai-the-objective-is-subjective-4614795d179b) (2 superhero acuan) diikutkan juga) akan mengambil informasi terhadap fitur-fitur yang ada dari *ID* hingga *YEAR_CAT*, selanjutnya proses hitung dari *cluster* pada setiap hasil rekomendasi dilakukan dengan menerapkan set 1 dan set 2 seperti pada gambar di bawah yang akan memperhitungkan masing-masing metrik pada setiap *loop*. Terakhir hasil metrik dari total sepuluh *loop* tadi diambil rata-ratanya.

![fold of metric cluster](https://user-images.githubusercontent.com/59215827/138242857-b3fbf335-ccee-4178-9c5d-7ea8ff14d623.png)

Berikut penjelasan lebih lengkap terkait metrik-metrik tersebut yang kemudian ditampilkan hasil performa setelahnya:

### Silhouette Coefficient
Pada kasus *unsupervised learning*, proses evaluasi dilakukan dengan model/algoritma yang ada. Metrik ini memiliki rentang skor dari -1 (menunjukkan salah *cluster*) hingga satu 1 (hasil *cluster* sangat baik), sedangkan nilai di sekitar 0 menunjukkan adanya *cluster* yang saling tumpang tindih. [<sup>8</sup>](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html#sklearn.metrics.silhouette_score) Persamaan Silhouette (s) [<sup>9</sup>](https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient) didefinisikan untuk setiap sampel dan terdiri dari dua skor untuk sampel tunggal adalah:

a: Jarak rata-rata antara sampel dan semua titik lain di kelas yang sama.

b: Jarak rata-rata antara sampel dan semua titik lain di cluster terdekat berikutnya.

![image](https://user-images.githubusercontent.com/59215827/138210924-f178c2ce-6b5b-4d60-8bfe-2165d1b33fe6.png)<br>
<sup><sub><a href="https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient"><i>image source</i></a></sub></sup>

Kelebihan | Kekurangan
-- | --
Rentang skor yang ada memberikan penilaian jelas terhadap hasil *cluster* (terutama jika terpisah dengan baik maka skor akan semaki tinggi)| Skor lebih besar terhadap *convex cluster* dibandingkan tipe *cluster* lain seperti *density cluster* pada DBSCAN 

### Calinski & Harabasz score
Memiliki nama lain Variance Ratio Criterion. Metrik ini menunjukkan jika skor semakin tinggi maka *cluster* memiliki data poin padat sangat baik serta terpisahkan dengan sangat jelas (*boundary*nya). [<sup>9</sup>](https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient) Persamaan dari metrik (s) ini adalah:

![image](https://user-images.githubusercontent.com/59215827/138217112-43594144-fd95-449b-85fe-7ff47226b136.png)<br>
![image](https://user-images.githubusercontent.com/59215827/138216332-85a6eb62-a077-4d1d-b479-b234b20d2ca7.png)<br>
<sup><sub><a href="https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient"><i>image source</i></a></sub></sup>

Kelebihan | Kekurangan
-- | --
Skor yang dihasilkan menunjukkan dengan jelas kualitas *cluster* | Sama dengan kekurangan pada metrik Silhouette sebelumnya
Prose penghitungan yang sangat cepat |

### Davies-Bouldin score
Metrik ini menunjukkan kesamaan rata-rata antara *cluster* yang didapatkan dengan membandingkan jarak antara *cluster* dengan ukuran dari *cluster* tersebut. Skor yang semakin mendekati 0 menandakan *cluster* terpisah dengan sangat jelas. [<sup>9</sup>](https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient) Persamaan dari metrik (DB) ini adalah:

![image](https://user-images.githubusercontent.com/59215827/138217268-9f5718e9-f21b-499b-9ade-a09f0602c13b.png)<br>
![image](https://user-images.githubusercontent.com/59215827/138217051-48d5325d-7dfa-4035-b7e2-deb7c1fd015f.png)<br>
<sup><sub><a href="https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient"><i>image source</i></a></sub></sup>

Kelebihan | Kekurangan
-- | --
Perhitungan lebih sederhana dibandingkan metrik Silhouette | Sama dengan kekurangan pada metrik Silhouette sebelumnya
Metrik hanya menghitung berdasarkan jumlah dan fitur yang terdapat pada dataset | Implementasi *centroid* menyebabkan jarak hanya dapat diukur dengan Euclidian

### Hasil Performa
* Algoritma **NN - Jaccard**
  * Aquaman
 
    ![image](https://user-images.githubusercontent.com/59215827/138233009-1a781a77-0c77-4826-bcc8-0707fd2bf943.png)

  * Captain America
    
    ![image](https://user-images.githubusercontent.com/59215827/138233068-73104b14-1e9a-49aa-bad3-0bfff431872c.png)

* Algoritma **Cosine Similarity**
  * Aquaman
 
    ![image](https://user-images.githubusercontent.com/59215827/138233159-7dae1428-0424-4b3a-8462-10a0ddf812b2.png)

  * Captain America
    
    ![image](https://user-images.githubusercontent.com/59215827/138233213-426819d1-1101-4d6a-941b-a097b3ed3c83.png)

Hasil keseluruhan terhadap evaluasi algoritma menunjukkan,
1. Berdasarkan metrik Silhouette dari masing-masing performa di atas mendekati nilai 0 yang menandakan adanya tumpang tindih pada ***cluster*** (atau dapat disebut sebagai `data poin` dengan `labelnya` berupa nama superhero). Hal ini menunjukkan bahwa hasil rekomendasi telah berada pada keadaan yang persis atau tingkat kesamaan tinggi.
2. Berdasarkan metrik Calinski & Harabasz dari masing-masing performa di atas menunjukkan nilai yang kecil (hanya pada 1. sekian (tidak ada batas maksimum nilai metrik ini)) dan menandakan kurang terpisah atau jelasnya batas antara label tadi. Hal ini juga menunjukkan hasil bagus bahwa rekomendasi memiliki tingkat kesamaan yang tinggi satu sama lainnya.
3. Berdasarkan metrik Davies-Bouldin dari masing-masing performa di atas juga menunjukkan nilai cenderung besar (bisa saja nilai terendah ada pada 0.00001 atau kurang). Hal ini juga menunjukkan label tidak begitu terpisah dengan baik atau dengan kata lain memiliki kemiripan (tingkat kesamaan yang tinggi).

---
<sub><sup>8. Sklearn. (2021). "sklearn.metrics.silhouette_score".</sup></sub><br>
<sub><sup>9. Sklearn. (2021). "2.3. Clustering".</sup></sub>

## Kesimpulan
Algoritma yang digunakan pada sistem rekomendasi superhero (*`content-based filtering`*) telah menunjukkan hasil yang bagus dengan dibuktikan pada proses evaluasi. Selain itu sistem telah berhasil merekomendasikan sebanyak 5 superhero lain yang mungkin disukai oleh pengoleksi *action figures*. Untuk hasil lebih meyakinkan juga dapat melihat adanya hasil rekomendasi sama diantara dua algoritma tadi.

> **Ini adalah bagian akhir laporan**
