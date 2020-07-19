# Twitter-Sentiment Analysis

Sentiment Classification using Fasttext Embeddings with Convolutional Neural Networks (CNN)

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/Word_Cloud_Gnuplot.PNG" width="750"></p>

## Getting Started

[![Generic badge](https://img.shields.io/badge/fastText-0.9.2-BLUE.svg)](https://github.com/facebookresearch/fastText/)
[![Generic badge](https://img.shields.io/badge/bokeh-2.1.1-RED.svg)](https://docs.bokeh.org/en/latest/index.html)
[![Generic badge](https://img.shields.io/badge/PySastrawi-1.2.0-YELLOW.svg)](https://github.com/har07/PySastrawi)
[![Generic badge](https://img.shields.io/badge/TwitterScraper-1.0.0-GREEN.svg)](https://github.com/taspinar/twitterscraper)

Berikut ini merupakan Rancangan Program yang akan dibangun :

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/System_Flowmap.png" width="750"></p>

### [Part 1] Crawling Twitter Data

<p align="justify">
Data yang digunakan merupakan dokumen berbahasa Indonesia. Data tersebut diambil dari Twitter dengan cara crawling menggunakan library TwitterScraper yang dikembangkan oleh Ahmet Taspinar 2. Total data yang berhasil terkumpul berjumlah sebanyak 3582 tweet dalam bentuk tidak terstruktur serta belum memiliki informasi label sentimen. Pemberian label dilakukan secara manual dengan bersifat subjektif sesuai pandangan penulis. 
  
Data dibagi menjadi dua bagian, yaitu 2900 tweet sebagai data latih dengan rincian : 834 positif, 978 netral dan 1088 negatif, serta 682 tweet sebagai data uji dengan rincian : 218 positif, 240 netral, 224 negatif. Data uji digunakan sebagai tolak ukur untuk menghitung keberhasilan dari model klasifikasi yang telah dibangun dengan menggunakan data latih. Berikut merupakan Tabel 1 yang menggambarkan tweet yang berhasil diperoleh.
</p>

### [Part 2] Exploratory Data Analysis

<p align="justify">
Preprocessing dilakukan setelah data diberi label sentimen. Tahapan ini berfungsi untuk menghilangkan beragam masalah yang dapat mengganggu hasil dari model yang dibangun. Proses yang dilakukan yaitu mengubah maupun menghapus angka, huruf, simbol serta kata yang tidak memiliki makna, atau bernilai informasi rendah dengan menggunakan library PySastrawi. Contoh proses yang dilakukan yaitu seperti pada Tabel 2 berikut.
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/Preprocessing.PNG" width="600"></p>

### [Part 3] Fasttext Embeddings

<p align="justify">
Proyek open-source yang dikembangkan oleh Tim Facebook Research Lab sebagai metode yang efektif dan cepat dalam melakukan vektorisasi kata maupun klasifikasi teks. Dalam merepresentasi kata, fasttext memiliki cara kerja yang berbeda dibandingkan word2vec.
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/n-grams.png" width="700"></p>

### [Part 4] Convolutional Neural Network

<p align="justify">
Penelitian ini menggunakan 2 convolutional layers, 2 batch normalization layers serta 2 pooling layers. Penelitian dibangun dengan menggunakan TensorFlow serta dijalankan pada Google Colaboratory dengan menggunakan pengaturan GPU dari Google. Arsitektur jaringan yang digunakan dapat dilihat pada Gambar berikut.
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/Conv_Layer.png" width="700"></p>

<p align="justify">
Dalam penerapannya, operasi konvolusi menggunakan matriks kernel untuk mendeteksi local features berdasarkan posisi kata yang berurutan. Penggunaan satu kernel tidaklah cukup untuk mendeteksi keseluruhan jenis local features. Pada penelitian ini, jumlah kernel yang digunakan sebanyak 64 kernel yang berbeda dengan ukuran sebanyak 7 x 100 (dim). Nilai tersebut dipilih karena dapat menangkap pola atau informasi yang penting pada suatu frasa kalimat. Hasil dari proses konvolusi tersebut mengubah bentuk matriks yang awalnya berbentuk 42 x 100 menjadi 42 x 64 seperti pada Gambar berikut.
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/Layer_1.png" width="700"></p>

<p align="justify">
Ketiga operasi yang dijelaskan sebelumnya juga diterapkan pada layer kedua seperti pada Gambar 7 dibawah. Perbedaan yang cukup berpengaruh terdapat pada bagian pooling layer. Berbeda dengan layer pertama yang menggunakan max pooling layer, maka pada layer kedua berikut menggunakan global max pooling, yang bekerja dengan cara mengambil nilai maksimum pada tiap channel. Hasil dari proses tersebut akan mereduksi matriks 21 x 64 menjadi bentuk skalar dengan ukuran 64.
</p>

<p align="justify">
Bagian layer kedua juga memiliki operasi lain seperti dropout. Selama proses training, dropout akan menjadi bagian yang paling penting dengan memecahkan masalah utama dalam machine learning, yaitu overfitting. Dropout bekerja dengan cara melepaskan neuron secara acak selama proses training untuk mencegah co-adaptation. Hasil dari operasi dropout akan dilanjutkan oleh dense layer. Dense layer umumnya diposisikan diakhir proses training yang berfungsi untuk mendefinisikan hasil klasifikasi. Secara berurutan, dense layer akan mereduksi ukuran skalar 64 menjadi 32 dan diakhiri dengan ukuran 3 sesuai dengan jumlah klasifikasi sentimen. Dapat dilihat pada Gambar dibawah berikut, dense layer akan menerapkan softmax sebagai fungsi aktivasi untuk mendapatkan probabilitas tiap hasil klasifikasi. Berdasarkan hasil tersebut, dapat diketahui bahwa kalimat ”semangat teman teman
pengusahaa tidak mudah insya allah hitung berat timbang akhirat kelak aamiin” bernilai sentimen positif.
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/Layer_2.png" width="700"></p>

## Testing

<p align="justify">
Confusion matrix merupakan suatu konsep dalam machine learning yang menjelaskan mengenai informasi klasifikasi aktual dan prediksi dari suatu sistem klasifikasi. Confusion matrix diperlukan untuk mengetahui baik atau tidaknya suatu model dalam memberikan prediksi terhadap suatu data uji yang diberikan
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/ConfusionMatrix.png" width="500"></p>

<p align="justify">
Tabel berikut, merupakan potongan dari hasil prediksi yang dihasilkan dari data uji yang telah disediakan. Terlihat bahwa pada kelima tweet tersebut mendapatkan prediksi yang cukup tepat. Pembahasan seperti pujian pada tweet pertama merupakan salah satu contoh dari sentimen yang bersifat positif, juga pembahasan seputar penandatanganan petisi pada tweet ketiga umumnya tidak berisikan ujaran yang bersifat reaktif, serta pembahasan seperti ujaran kebencian pada tweet kelima merupakan bukti jelas yang menandakan sentimen negatif. Beberapa tweet seperti tweet kedua dan keempat tidak mendapatkan hasil prediksi yang sesuai. Hasil tersebut dipengaruhi diakibatkan adanya kata (token) yang bernilai ekstrim seperti ”narkoba” pada tweet kedua yang memiliki makna negatif serta ”lindung” yang memiliki makna positif pada tweet kelima.
</p>

<p align="center"><img src="https://github.com/farhanalfaa/twitter-sentiment-analysis/blob/master/images/Klasifikasi_Sentimen_Gnuplot.PNG" width="750"></p>

## Authors
   Copyright (c) 2020 [Farhan Alfariqi](https://github.com/farhanalfaa)
