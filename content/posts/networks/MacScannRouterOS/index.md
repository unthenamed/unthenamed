+++
	title = "Mac Scann via RouterOS | Mac List Discovery untuk bypass filter hostpot"
	date = 2022-08-06T00:22:35+07:00
#	description = "" # Used by description meta tag, summary will be used instead if not set or empty.
	robotsdisallow = false
	featured = false
	draft = false
	comment = true
	toc = true
	reward = true
	carousel = true
	pinned = false

		categories = [
			""
		]

		tags = [
			"Mac Spoof",
			"Mikrotik"
		]

		series = [
			"Artikel"
		]

		images = ["/images/rmacscann.png"]

		aliases = [
			"/MacScannRouterOS"
		]
+++
Mac-scan di RouterOS adalah alat yang berguna untuk mengidentifikasi alamat MAC perangkat yang terhubung dalam sebuah jaringan lokal (LAN). 
<!--more-->
Terkadang, kita menghadapi kesulitan dalam menentukan alamat MAC perangkat yang terhubung, terutama saat ada filter hotspot yang diterapkan. Filter hotspot biasanya hanya menampilkan alamat MAC dari server hotspot, membuat kita sulit untuk mengetahui perangkat lain yang terhubung. Artikel ini akan membahas bagaimana kita dapat memanfaatkan alat Mac-scan yang disediakan oleh MikroTik RouterOS untuk membuat daftar alamat MAC perangkat yang terhubung di jaringan. Kami juga akan menjelaskan cara melakukan ini dengan perangkat MikroTik, seperti Sxtsq2nd, dan bahkan dengan menggunakan MikroTik yang dijalankan dalam VirtualBox dengan antarmuka terhubung ke LAN yang sesuai.

## Langkah-langkah Penggunaan Mac-Scan di RouterOS

1. **Masuk ke Terminal RouterOS**: Pertama, akses perangkat RouterOS Anda melalui antarmuka administratif, entah itu melalui SSH atau melalui terminal di webfig.
![Center](potossh.png#width=300px)

2. **Jalankan Perintah Mac-Scan**: Setelah Anda masuk ke terminal MikroTik, ketik perintah berikut untuk menjalankan Mac-Scan. Pastikan untuk mengganti `interface=wlan1` dengan nama antarmuka yang terhubung ke LAN yang akan Anda scan. Anda tidak perlu mengatur alamat IP pada antarmuka ini karena kita akan melakukan pemindaian terhadap semua perangkat yang terhubung di LAN tersebut.

   ```
   /tool mac-scan interface=wlan1
   ```
## Hasil Scan
1. **Hasil Scan Alamat MAC**: Hasil dari pemindaian akan menampilkan daftar alamat MAC perangkat yang terhubung bersama dengan alamat IP mereka.
![Center](potoscan.png#width=300px)

2. **Simpan Hasil Scan**: Anda dapat menyimpan hasil pemindaian ini dengan menekan tombol "D" (Dump), dan Anda dapat mengambilnya dari perangkat MikroTik dalam file dengan nama `console-dump.txt` Anda dapat menggunakan FTP atau cara lain untuk mengambil file ini dari root file sistem MikroTik.

![Center](dump.png#width=300px)

Hasil dari Mac-Scan dapat digunakan untuk tujuan pengetahuan perangkat yang terhubung ke jaringan Anda atau bahkan untuk keperluan lain, seperti Spoofing alamat MAC. Selalu gunakan alat ini dengan bijak dan dengan mematuhi kebijakan keamanan dan hukum yang berlaku. Semoga artikel ini bermanfaat dalam mengidentifikasi perangkat yang terhubung ke jaringan Anda.
- - -
