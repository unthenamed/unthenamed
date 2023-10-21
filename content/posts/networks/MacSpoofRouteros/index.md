+++
	title = "Spoof Hostpot Mikrotik | otomatis mencari Mac Address yang terhubng ke internet"
	date = 2022-08-05T20:34:04+07:00
#	description = "" # Used by description meta tag, summary will be used instead if not set or empty.
	robotsdisallow = false
	featured = false
	draft = false
	comment = true
	toc = true
	reward = true
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

		images = ["/images/macspoof.png"]

		aliases = [
			"/Macspoof"
		]
+++



<!--more-->
- - -
# MAC Spoofing: Membongkar Teknik Pengalihan Alamat MAC

---

## Pendahuluan

Pengalihan alamat MAC (MAC Spoofing) adalah teknik yang digunakan dalam jaringan komputer untuk mengganti alamat Media Access Control (MAC) perangkat dengan alamat MAC palsu. Ini adalah praktik yang umumnya digunakan untuk berbagai tujuan, termasuk mengelabui sistem keamanan, mengakses jaringan terbatas, atau menyembunyikan identitas perangkat. Dalam artikel ini, kita akan menjelaskan lebih lanjut tentang MAC Spoofing, bagaimana teknik ini berfungsi, dan potensi konsekuensinya.

## Apa Itu MAC Spoofing?

**MAC Spoofing** adalah tindakan mengganti alamat MAC perangkat jaringan dengan alamat palsu. Alamat MAC adalah identitas unik yang diberikan kepada setiap perangkat yang terhubung ke jaringan. Ini digunakan untuk mengidentifikasi perangkat dalam jaringan dan memungkinkan router dan switch untuk mengarahkan paket data ke perangkat yang benar.

## Bagaimana MAC Spoofing Bekerja?

Proses MAC Spoofing melibatkan beberapa langkah:

1. **Pemahaman Alamat MAC Target**: Langkah pertama dalam MAC Spoofing adalah memahami alamat MAC dari perangkat target yang akan diganti. Ini bisa ditemukan dengan berbagai cara, termasuk pemindaian jaringan atau inspeksi lalu lintas.

2. **Mengganti Alamat MAC**: Setelah alamat MAC target diketahui, penyerang mengganti alamat MAC perangkat mereka dengan alamat yang sama dengan alamat target. Ini dapat dilakukan dengan menggunakan perangkat lunak khusus atau alat yang dirancang untuk tujuan ini.

3. **Mengirim Lalu Lintas**: Dengan alamat MAC palsu yang sudah diganti, penyerang dapat mengirim atau menerima lalu lintas jaringan seperti yang diinginkan. Ini bisa digunakan untuk menyusup ke dalam jaringan atau melakukan serangan lainnya.


## Konsekuensi dan Risiko

Pengalihan MAC, baik untuk tujuan yang sah maupun tidak, memiliki risiko dan konsekuensi. Beberapa di antaranya termasuk:

- **Pelanggaran Keamanan**: Pengalihan MAC ilegal dapat melanggar kebijakan dan hukum keamanan. Ini dapat mengakibatkan konsekuensi hukum serius.

- **Gangguan Jaringan**: Pengalihan MAC yang tidak dilakukan dengan benar dapat mengganggu kinerja jaringan, membuatnya tidak stabil, dan menyebabkan masalah konektivitas.


## Menambahkan Skrip Melalui Winbox

Berikut adalah langkah-langkah untuk menambahkan skrip di RouterOS MikroTik melalui aplikasi Winbox:

1. **Unduh dan Buka Winbox**: Pastikan Anda telah mengunduh aplikasi Winbox dan terhubung ke perangkat RouterOS Anda melalui Winbox.

2. **Masuk ke Winbox**: Masukkan kredensial yang diperlukan untuk masuk ke perangkat RouterOS Anda melalui Winbox.

3. **Buka Menu "System"**: Di jendela utama Winbox, klik pada menu "System."

4. **Pilih "Scripts"**: Dalam menu "System," klik pada opsi "Scripts." Ini akan membuka jendela "Scripts."

5. **Buat Skrip Baru**: Klik tombol "Add New" untuk membuat skrip baru.

6. **Tambahkan Nama Skrip**: Beri nama skrip Anda dalam kolom "Name."

7. **Isi Skrip**: Masukkan skrip di kolom "Source" dengan mengisi skirp [Mac Spoof](https://raw.githubusercontent.com/unthenamed/Spoof-MAC-RouterOS/main/Spoof.rsc)
![Center](scr.png#width=300px)

8. **Ubah onfigurasikan skcript**
	```
	:local name "Spoof1" #nama skrip
	:local mode "0"; # mode: #1 scan list ke save mac | 0 normal 
	:local interface "wlan1";  # interface wireles
	:local maclist "macid.txt"; # jika belu punya list mac -> cari di tutor sebelumnya
	:local succes "macsave"; # list mac yang terubung akan di simpan
	:local namehost "f09f98912047616b2067616e676775206b6f2c2063756d61206d696e746120696e7465726e65742074657263657061742040"; # Hostname dhcp request menggunakan HEX (setiap request beda)
	:local keepalive "15"; # waktu loop pengecekan netwatch
	:local dstcheck "142.250.4.136" ; # ip luar acuan mendapatkan internet
	:local gateway "192.168.5.1" # gateway mikrotik target
	```
9.  **Simpan Skrip**: Klik tombol "OK" atau "Apply" untuk menyimpan skrip.

10. **Jalankan Skrip**: Anda dapat menjalankan skrip dengan mengkliknya dalam daftar skrip dan memilih opsi "Run Script."

## Membuat Scheduler MacSpoof Winbox

1. **Buka Aplikasi Winbox**: Pastikan Anda sudah mengunduh dan menginstal Winbox. Buka aplikasi dan masuk ke perangkat RouterOS Anda.

2. **Masuk ke Perangkat**: Setelah masuk, Anda akan melihat tampilan utama Winbox yang menampilkan informasi konfigurasi perangkat Anda.

3. **Buka Menu "System"**: Di bagian kiri jendela Winbox, cari dan klik menu "System."

4. **Pilih "Scheduler"**: Di dalam menu "System," Anda akan menemukan opsi "Scheduler." Klik pada "Scheduler" untuk membuka jendela konfigurasi scheduler.

5. **Tambahkan Scheduler Baru**: Klik tombol "Add New" untuk membuat scheduler baru.

6. **Konfigurasi Scheduler**:
    ```
	:if ([:len [/system script job find script=spoof1]] = 0) do={/system script run spoof1} ;
	```
 	![Center](scr2.png#width=300px)

7. **Simpan Konfigurasi**: Klik tombol "OK" atau "Apply" untuk menyimpan konfigurasi scheduler.

8. **Lihat dan Kelola Scheduler**: Setelah disimpan, Anda dapat melihat, mengedit, dan mengelola scheduler Anda sesuai kebutuhan.

9.  **Aktifkan Scheduler**: Pastikan untuk mengaktifkan scheduler dengan mencentang kotak "Enabled" jika Anda ingin scheduler berjalan sesuai jadwal yang telah Anda atur.


## Cek status internet di Netwatch
Dan untuk mengetahui script mana yang mendapatkan internet bisa di lihat di menu netwatch `tools/netwatch`
![Center](net.png#width=300px)
## Kesimpulan

MAC Spoofing adalah teknik yang digunakan dalam dunia jaringan yang memiliki potensi baik dan buruk. Penggunaannya harus diperlakukan dengan bijak dan hanya dalam konteks yang sah. Pengalihan MAC yang ilegal dapat mengakibatkan pelanggaran keamanan, kerusakan jaringan, dan konsekuensi hukum serius. Oleh karena itu, penting untuk memahami teknik ini dan menggunakan pengetahuan ini secara bijak dan bertanggung jawab dalam pengaturan jaringan.

- - -



