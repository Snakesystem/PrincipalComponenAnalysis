# Principal Component Analysis
Dokumentasi pembelajaran machine learning Dimentionality Reduction

### Introduction
Principal Component Analysist adalah bagian dari machine learning *unsupervised learning* dimana metode yang digunakan adalah *Dimentionality Reduction*. Metode ini adalah dengan memanipulasi dimensi dari sebuah dataset menjadi lebih kecil seperti pada gambar berikut:

![dimensi](https://user-images.githubusercontent.com/90812378/179361838-ca349d53-db80-451e-aa58-2bf2ced9f824.png)

Seperti gambar diatas di ilustrasikan gambar dengan 3D di ubah menjadi 2D

### Dataset Case
Dokumentasi dataset bisa diakses melalui: https://github.com/zalandoresearch/fashion-mnist

Dataset ini disediakan oleh `Tensor Flow` dimana dimensi dari datset ini adalah berupa array (70.000, 28, 28). 

![d1](https://user-images.githubusercontent.com/90812378/179361760-cdd7d1ab-ba82-42de-8fa0-78763f0227d3.png)

Namun setelah di cek isinya tapi mengapa isinya adalah angka 0 dan jumlahnya sangat banyak

![d2](https://user-images.githubusercontent.com/90812378/179361936-fa703dc4-6a04-4371-83a2-79fc7ee9dfae.png)

Ketika di cek pada array ke(0) muncul nilai-nilai lain namun data tersebut masih belum memberikan informasi kurang jelas.

![d3](https://user-images.githubusercontent.com/90812378/179362005-c40d9a49-aa8e-4808-9ced-a51260b9521d.png)

Setelah di visualisasikan data pada array ke(0) tersebut membentuk gambar seperti sepatu

![d4](https://user-images.githubusercontent.com/90812378/179362053-fff7a9a8-9692-4451-8e85-99f37a9cd497.png)

Dan pada bagian lain juga membentuk seperti gambar tas, dugaan saya data-data tersebut adalah pixel dari banyak gambar dengannukuran 28x28 pixel.Setelah membaca dokumentasi dari dataset ternyata data tersebut memang berupa gambar yang di pecah kedalam bentuk pixel dan ada 10 jenis gambar produk facion yaitu:
- Label 0: T-Shirt (Kaos)
- Label 1: Trouser (Celana Panjang)
- Label 2: Pullover (Kaos Lengan Panjang)
- Label 3: Dress (Gaun)
- Label 4: Coat (Jaket, Sweater, dll)
- Label 5: Sandal
- Label 6: Shirt (Kemeja)
- Label 7: Sneaker (Sepatu)
- Label 8: Bag (Tas)
- Label 9: Ankle Boot (Sepatu Boots)

### Model PCA

Karena setiap gambar memiliki ukuran tinggil dan lebar 28 pixel maka artinya luas nya adalah 784 dimana jika diubah ke dalam bentuk dataframe maka akan menghasilkan data dengan 70.000 baris dan 784 kolom. Disinilah teknik *Dimentionality Reduction* diperlukan karena kita akan mengecilkan ukuran dataset yang sangat besar menjadi lebih kecil tanpa mengurangi nilai yang ada di dalamnya. Untuk formula konsep PCA bisa dilihat di artikel berikut https://www.rumusstatistik.com/2015/03/analisis-komponen-utama-principal.html

![d5](https://user-images.githubusercontent.com/90812378/179382238-647e3cbc-b020-4d0a-a72a-0b2872147563.png)

Ini adalah hasil data setelah di lakukan PCA, bisa di lihat meskipun data yang sebelumnya 784 kolom kemudian di kecilkan menjadi 2 kolom dengan PCA namun bentuk keaslian datanya masih bisa di selamatkan.

Bisa di lihat pada acatter plot bahwa data masih bisa di bedakan antara `dress, boots dan sneakers` dan antara `boots dan sneaker` sangat berdekatan karena memang produk sneakers dan boot merupakan produk yang sama yaitu alas kaki. Dress terlihat memisah karena dress memang bukanlah alas kaki.

![d6](https://user-images.githubusercontent.com/90812378/179382355-7fe4db64-1284-4dfe-97c5-3b0614ced0fc.png)

Kemudian saya bandingkan antara `T-Shirt, Dress dan Sneakers` dimana `Sneakers` memisah dengan produk `Dress` dan `T-Shirt` karena `T-Shirt` dan `Dress` merupakan pakaian sedangkan `Sneakers` adalah alas kaki.
Jadi kesimpulanya dengan dengan menggunakan PCA kita bisa mengecilkan ukuran data tanpa menghilangkan nilai-nilai yang terkandung di dalamnya.

### Logistic Regression
Berdasarkan visualisasi nilai pada data masih bisa di selamatkan meskipun ukuran datanya telah diperkecil. Kita akan mencoba apakah performa penggunaan PCA dengan menggunakan Model Klasifikasi **Logistic regression**.

![d7](https://user-images.githubusercontent.com/90812378/179382842-308a1a32-aa7c-4046-9f12-5f339c0c04d2.png)

Ternyata meskipun ukuran data di perkecil namun kita tetap mendapatkan hasil model machine learning 84 accuracy

### Conclution
**Principal Component Analysis** adalah teknik unsupervised learning yang sangat membantu jika kita menemukan data dengan ukuran yang sangat besar. Karena PCA akan mengurangi ukuran dataset kita namun nilai yang ada di dalam dataset bisa kita selamatkan dan waktu training model dengan klasifikasi masih menghasilkan model yang baik dan mempercepat waktu.

