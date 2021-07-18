---
layout: post
title: Menghilangkan Noise Menggangu Pada Meeting Online
date:   2021-01-04 15:01:35 +0300
image:  '/images/post-20210104-cover.jpg'
image-name: 'lucas law on Unsplash'
image-link: https://unsplash.com/@lucaslaw__?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText
tags:   [AI Technology]
---

Di saat pandemi seperti ini banyak dari kita yang beralih dari awalnya masuk ke kantor setiap hari menjadi kerja di rumah atau istilah kerennya <em>Work from Home (WFH)</em> atau <em>Remote Working</em>. Mungkin sedikit terlambat ya kalo mau bahas gimana cara WFH agar kerjaan tetap produktif. 

Banyak artikel lalu-lalang di internet menjelaskan cara WFH yang efektif. Mulai dari bangun rutinitas, senyapkan handphone agar fokus, sampai bela-belain setup meja kerja yang keren biar semakin semangat kerjanya. Diluar solusi itu saya akan membahas secara spesifik tentang permasalahan ramai nya kondisi rumah yang terkadang menggangu meeting. 

Buat saya yang WFH di rumah dan tinggal bersama orang tua. Tentu saja suara-suara aktifitas dari orang-orang dirumah ini hal yang tidak bisa dielakan. Mulai dari suara mesin cuci, ada yang memasak, kadang ada yang bermain bola voli depan rumah. Hal-hal tersebut tentunya menimbulkan suara yang terdakang menggangu kita disaat meeting. Banyak cara yang bisa dicoba untuk masalah tersebut yang saya ketahui.

Pertama mulai dari upgrade hardware dengan membeli microphone yang memiliki fitur [cardiodid polar pattern](https://yourfreesounds.com/blogposts/cardioid-microphone-polar-pattern-explained/) yang membantu mengurangi noise dari sekitar area kita. Tapi untuk membeli mic dengan fitur tersebut tentu saja membutuhkan biaya yang tidak sedikit dan setup yang perlu diperhitungkan dengan environment meja kerja.

Kedua bisa dengan menggunakan aplikasi tambahan yang berfungsi untuk mengurangi noise pada audio laptop/ pc. Seperti [Krisp](https://krisp.ai/) dimana aplikasi tersebut bisa membantu mengurangi bahkan menghilangkan noise yang tidak perlu selain suara kita. Seperti noise bayi menangis, kendaraan di jalan raya, dan lainnya. Untuk aplikasi ini dikenai biaya sekitar $60 per tahun atau sekitar 800 ribuan dengan kurs di awal bulan Januari 2021 ini.

Nah kalo diliat dari dua opsi diatas penggunaan software terlihat lebih murah dan mudah ya dibanding kita harus invest beli hardware baru. Tapi tetap aja mahal juga semisal meeting dalam sebulan gak terlalu banyak dan meetingnya pun santai dengan tim sendiri. Tenang saya ada solusinya untuk masalah ini.

Memperkenalkan [NoiseTorch](https://github.com/lawl/NoiseTorch), yeay!

Tenang ini bukan konten promo atau apa, tetapi saya mau cerita pengalaman saya menggunakan software/ aplikasi tersebut untuk permasalahan noise pada meeting. Ada beberapa hal yang menarik dari aplikasi ini.

NoiseTorch ini adalah aplikasi ini open source khusus untuk Linux yang menggunakan library PulseAudio untuk membuat virtual microphone yang menekan noise disekitar. Kalian bisa mengecek langsung pada link diatas dimana ada repository Github nya yang bisa di akses atau di fork semisal ingin berkontribusi source code. 

Kemudian timbul pertanyaan tentang bagaimana aplikasi ini bisa memecahkan masalah noise pada meeting. Sederhananya seperti pengertian diatas kalo aplikasi ini membuat virtual microphone untuk menekan noise. Sederhana sekali bukan? Tapi tidak dengan kerumitan dibelakangnya. 

Aplikasi ini menggunakan [RNNNoise](https://jmvalin.ca/demo/rnnoise/) semacam metode deep learning yang diaplikasikan untuk menekan noise pada sinyal audio input. Ide dasarnya dengan mengkombinasikan teknik pemrosesan sinyal klasik dengan metode deep learning untuk membuat algoritma peredam bising secara real-time. Kelebihan metode ini selain berukuran kecil dan cepat diclaim juga tidak memerlukan GPU untuk komputasinya bahkan bisa berjalan di Raspberry Pi.

Singkatnya cara kerja metode NoiseTorch ini, pertama-tama audio terbaca oleh virtual microphone di laptop/ pc kalian. Kemudian diproses audio input tersebut dengan metode RNNNoise yang hasilnya berupa audio input yang telah ditekan noisenya yang kemudian diteruskan ke audience meeting anda.

Beberapa hal dari pengalaman saya yang perlu anda diperhatikan apabila ingin menggunakan aplikasi NoiseTorch:
1. Saat ini baru bisa digunakan untuk sistem operasi Linux, yaa ini yang paling berat pasti. Mungkin kalian disini banyak yang pake Windows/ Mac. Solusinya bisa instal ulang sistem operasinya ke Linux *canda.
2. Proses instalasi yang membutuhkan effort, untuk ini membutuhkan ketelitian dalam membaca cara instalasinya. 
3. Untuk pengoperasiannya membutuhkan setting manual berkali-kali untuk memilih virtual microphone di menu Linux saya. Ini terkadang bikin ribet karena sudah banyak-banyak berbicara di meeting ternyata masih belum terpilih yang NoiseTorch.

Diluar poin-poin diatas, sejujurnya saya sangat terbantu dengan adanya aplikasi NoiseTorch ini. Apalagi pada jam-jam kondisi rumah kurang kondusif dan sesi meeting yang butuh aktif berbicara. NoiseTorch ini sangat mampu meredam noise sehingga audio yang didengar oleh peserta meeting pun menjadi lebih jernih. 

Semoga kalian bisa terbantu juga ya masalah soal noie di meeting dengan menggunakan aplikasi ini. Apabila kalian punya solusi lain menghilangkan noise di meeting bisa diskusi bareng yaa via Email/ Twitter.

