---
layout: post
title: Menghilangkan Background Objek Gambar Secara Otomatis
date:   2021-07-29 00:00:00 +0300
image:  '/images/post5-cover.png'
image-name: 'Source Image'
image-link: https://pub-static.haozhaopian.net/static/web/site/features/magic-clipper/images/magic-clipper_01295c4dddd7f8629f7657bae114de3906.png
tags:   [AI Technology]
---

Di dunia yang ramai dengan konten digital saat ini sangat penting untuk memiliki kualitas gambar yang relevan dengan target pengguna. Umumnya kita bisa mencari sumber-sumber gambar di internet untuk digunakan sebagai bahan membuat konten yang berkualitas.

Tetapi tetap perlu ada usaha untuk menyatupadukan gambar tersebut agar konten lebih maksimal. Mulai dari menghilangkan background, mengubah ukuran, melakukan clipping dan lainnya. Hal tersebut menjadi tantangan bagi sebagian orang yang tidak mempunyai skill design yang memadai dan keterbatasan waktu.

Khususnya tentang cara menghilangkan background objek di sebuah gambar. Proses manual yang biasanya harus melakukan pembuatan garis tepi dari sebuah objek utama secara manual pada aplikasi edit gambar. Tentu saja proses ini memakan waktu apalagi tingkat kesulitan objek yang tinggi.

Di artikel kedua di sub-tema [#reviewproductAI](http://indranugraha.com/tags/#AI%20Technology) ini akan dibahas sebuah produk yang saya sendiri sudah lama terfikir untuk membuat prototype solusi sejenis yaitu menghilangkan background objek pada sebuah gambar dengan bantuan teknologi AI.

### Product Check
![](/images/post5-content2.png)

Photo by [removal.ai Website](https://removal.ai/)

Banyak perusahaan yang menyediakan produk yang cukup mirip service nya seperti [removal.ai](https://removal.ai/), [removebg](https://www.remove.bg/), [slazzer](https://www.slazzer.com/), [fotor](https://www.fotor.com/) dan lainnya. Disini saya coba ambil contoh dari [removal.ai](https://removal.ai/) yang saya lebih dahulu tahu produknya dibanding kompetitornya.

Pertama ketika melihat website produk tersebut terlihat produk ini mensasar beberapa profil pengguna seperti designer, developers, marketing dan profil umum yang memiliki kebutuhan untuk menghilangkan background pada objek di sebuah gambar. 

Sehingga pengguna bisa mengolah objek tersebut untuk lebih lanjut secara cepat dan mudah. Secara umum market mereka terbagi dua mulai dari B2C bagi individual dan B2B bagi enterprise yang memiliki kebutuhan pemrosesan secara banyak. 

Produk tersebut berupa Software as a Service (SaaS) dengan format akses berupa Desktop App dan API-based. Model bisnis dimana pengguna berlangganan berdasarkan jumlah kuota yang telah dipilih.

Pengguna bisa mengakses aplikasi untuk menggunakan secara langsung untuk Desktop App ataupun menggunakan API untuk pemrosesan data yang banyak. Dari yang saya lihat penggunaan tools ini cukup mudah dipahami.

Khusus untuk format API tersedia dokumentasi cara menggunakan pada beberapa bahasa pemrograman seperti Python, PHP, C#, Javascript dan Nodejs. Juga menyediakan semacam demo sederhana dimana pengguna bisa mengunggah gambar dan melihat hasil gambar ketika sudah dihilangkan backgroundnya.

### AI Perspective
![](/images/post5-content1.png)

Photo by [Deep Machine Learning AI](http://deepmachinelearningai.com/wp-content/uploads/2020/02/Semantic-segmentation-1024x684.png)

Mari kita lihat dari perspektif metode AI yang digunakan pada produk tersebut. Secara umum saya melihat produk tersebut menggunakan metode [image segmentation](https://medium.com/swlh/image-segmentation-using-deep-learning-a-survey-e37e0f0a1489) sebagai metode utama pemrosesan gambar. 

Sistem akan melakukan segmentasi atau penandaan menyeluruh bagian objek yang telah ditentukan. Akan dilakukan partisi dari gambar menjadi beberapa bagian berbeda yang memiliki kesamaan atribut di level pixel gambar. 

Misal target dari segmentasi adalah sepeda, sistem akan melakukan penandaan terhadap objek sepeda yang telah didaftarkan secara menyeluruh. Kemudian akan menghilangkan bagian non sepeda dan menganggapnya sebagai background. Sehingga gambar hasilnya hanya akan ada objek sepeda dan background kosong.

![](/images/post5-content3.png)

Photo by [Image segmentation results of DeepLabV3 on sample images](https://arxiv.org/pdf/2001.05566.pdf)

Untuk membuat segmentasi gambar terdapat banyak metode yang bisa digunakan. Mulai dari metode yang old-school seperti thresholding, K-means clustering, histogram-based image segmentation dan edge detection. Sampai dengan metode kekinian seperti CNN, ensemble learning dan lainnya. 

Untuk melihat perkembangan metode terkini dari ranah riset bisa dicek laman [paperswithcode](https://paperswithcode.com/task/semantic-segmentation) ini. Disana terdapat banyak metode terkait segmentasi gambar yang bisa dipelajari dan digunakan. Apabila beruntung ada juga repositori kode program yang bisa di reproduce.

### Experiment

Sekarang mari kita melakukan sedikit uji coba dengan membandingkan produk [removal.ai](https://removal.ai/) dengan repositori open source untuk menguji performa hasil segmentasi pada gambar. Saya menggunakan metode [DeeplabV3-Resnet101](https://pytorch.org/hub/pytorch_vision_deeplabv3_resnet101/) dengan library [Pytorch](https://pytorch.org/) yang dijalankan di laptop saya dengan GPU GTX 1060ti.

Skenario nya saya menggunakan tiga gambar yang saya uji coba. Yang perlu diperhatikan disini saya langsung memasukan gambar ke source code [DeeplabV3-Resnet101](https://pytorch.org/hub/pytorch_vision_deeplabv3_resnet101/) dengan parameter standar dan tidak melakukan editing hasil pemrosesan di [removal.ai](https://removal.ai/).

![](/images/post5-exp1.png)
![](/images/post5-exp2.png)
![](/images/post5-exp3.png)

Photo by [Complex](https://images.complex.com/complex/images/c_fill,dpr_auto,q_90,w_920/fl_lossy,pg_1/g2xgonr3wqzkt5amviih/giannis-antetokounmpo-dunk-bucks-76ers-2019), [NBA](https://www.nba.com/bucks/sites/bucks/files/3_7.jpg), [The Salt Lake Tribune](http://local.sltrib.com/charts/jazz/fans.jpg)

Dari beberapa gambar diatas terlihat bagaimana performa [DeeplabV3-Resnet101](https://pytorch.org/hub/pytorch_vision_deeplabv3_resnet101/) masih menyisakan objek-objek yang seharusnya bisa terhapus menjadi background. Ini tentu saja hal yang sangat mungkin terjadi karena model tersebut dasarnya digunakan untuk keperluan penelitian yang terbatas untuk keperluan uji coba.

Berbeda dengan hasil dari [removal.ai](https://removal.ai/) dimana cukup berhasil dalam menghilangkan background dari objek utama. Hanya saja untuk gambar baris kedua terlihat ada objek orang yang terpotong. Juga di gambar baris ketiga ada bagian kaki yang seharusnya menajadi background tapi tidak menghilang. 

Hal ini sudah diakomodir oleh fitur dari produk tersebut dimana pengguna bisa memvalidasi batasan objek yang harus terhapus atau tidak. Hanya saja fitur ini ada bagian yang berbayar apabila ingin melakukannya di resolusi full alias hanya bisa pada resolusi preview.

![](/images/post5-content4.png)

Photo by [removal.ai](https://removal.ai/)

### Kesimpulan

Terlihat jelas bagaimana sebuah produk yang memang disiapkan untuk komersial lebih mampu lebih menjawab kebutuhan pengguna. Tentu saja ini bukan komparasi yang apple-to-apple jika dibandingkan dengan repositori riset publik.

Prodak ini memiliki sistem yang lebih robust terhadap kondisi objek sapa saja yang harus dideteksi dan mana yang harus menjadi background. Juga mekanisme penanganan apabila ada kesalahan yang sangat membantu pengguna untuk mencapai kualitas gambar yang diinginkan.

Hanya saja hal ini membuka wawasan kita juga apabila banyak repositori publik AI diluar sana yang berpeluang untuk dibundling menjadi sebuah produk komersil. Tentu saja banyak tantangan yang menunggu seperti data latih model, ekspektasi pengguna dan komputasi tinggi yang menjadi momok para startup AI.

Solusi yang ditawarkan cukup menjawab permasalahan pengguna yaitu membutuhkan hasil kualitas yang baik dan waktu pemrosesan yang cepat. Cara akses yang bisa digunakan secara langsung ataupun dengan API sangat membantu pengguna untuk menyelesaikan pekerjaan pengguna.



