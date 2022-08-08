---
# type: docs 
title: Konfigurasi DNS untuk custom domain Github Pages
date: 2022-04-01T15:27:13Z
featured: true
draft: false
comment: true
toc: true
reward: true
pinned: false
carousel: true
series:
  - Artikel
categories:
  - Github
tags: 
  - Domain
  - DNS
authors:
  - Jalil khoironi
images: ["images/gpage.jpeg"]
---


Langkah berikut untuk melakukan custom domain GitHub, Dan pastikan konfigurasi DNS yang digunakan tepat.

<!--more-->
- - -
{{< adstex >}}
- - -

## Konfigurasi DNS

Pertama, Anda bisa login ke Member Area/ Dns record ,
sebagai contoh disini saya menggunakan Cloudflare, maka masuk ke [Dashboard](https://dash.cloudflare.com/login/) juga bisa mengunakan aplikasi ColdCloud untuk mengatur dns.

Pilih Domain yang akan di gunakan.

![Float Right](/Screenshot_20220401_225335.jpg#width=300px)

Kemudian, pilih Menu DNS

![Float Left](/Screenshot_20220401_223812.jpg#width=300px)


Langkah berikutnya, Anda bisa klik Add New Record / dalam aplikasi tanda +

![Float Right](/Screenshot_20220401_225312.jpg#width=300px)

Pada bagian Record Type, pastikan pilihannya adalah A Record. Kemudian, Anda bisa mengisikan IP Address yang digunakan oleh GitHUb berikut satu per satu:

> 185.199.108.153 
>
> 185.199.109.153 
>
> 185.199.110.153 
>
> 185.199.111.153 


{{< adsparagrap >}}


Jangan lupa untuk selalu klik Save Record setiap selesai memasukkan data IP Address. 

Jika sudah berhasil, semua IP address yang Anda masukkan akan otomatis tercatat pada menu DNS management seperti ini: 

![dns list](/Screenshot_20220401_225317.jpg#width=300px)

Tahapan untuk konfigurasi DNS sudah selesai. Anda cukup menunggu proses propagasi domain terlebih dahulu hingga maksimal 1×24 jam. 

## Setting Domain github pages


Setelah berhasil, Buka repostory yang akan di custom domain, Bukan Setting -> Pages. Dan masukan custom domain yang akan digunakan.
kemudian klik save, tunggu proses nya hingga muncul tulisan {{< alert "Your site is published at https://nama_domain/" success >}}

![Center](/Screenshot_20220401_225429.jpg#width=300px)

