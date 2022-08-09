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
`Mac-scan` di RouterOS adalah suatu alat untuk keperluan menyurpai alamat mac mana saja yang terhubung di suatu LAN. 
<!--more-->
Ada kalanya kita kesulitan mengetahui mac manasaja yang terubung pada suatu LAN. Terlebih jika dalam jaringan LAN tersebut terdapat Mangement hostpot. Karna jika terdapat Management hospot kita menggunakan tool-tool lain seperti yang tool yang banyak tersedia contohnya dalam android Alamat mac yang terdeteksi hanya akan menampilkan alamat Mac mikrotik tersebut (server hostpot).

Bagaimana solusinya?  disini kita memenfaatkan tool yang di sediakan mikrotik tersebut untuk melist mana saja mac yang terhubung dalam suatu Lan.

kali ini saya menggunakan mikrotik Sxtsq2nd untuk mencoba menggunakan mac-scanner. Dan bagaimana jika kita tidak mempunyai  mikrotik? Bisa menggunakan Mikrotik crack di Virtualbox dengan interface yang terbridge ke LAN Tersebut. 


oke langsung saja ke tutuorial.
Karna Mac-scan hanya tersedia via terminal maka kita masuk ke mikrotik melalui ssh ataupun via terminal di webfig itu sendiri

![Center](potossh.png#width=300px)

jika sudah masuk ke terminal mikrotik kita ketikan perintah
```
/tool mac-scan interface=wlan1
```
Dan jika berhasil akan muncul list Mac beserta ip

![Center](potoscan.png#width=300px)

perlu di ingat interface harus di sesuaikan dengan mana yang terhubung ke LAN yang akan kita Scann dan tidak perlu mengatur ip di interface tersebut karna kita akan menscan seluruhnya mana saja mac yang terhubung dalam LAN tersebut.

Arahkan up/down untuk mengetahui seberapa banyak mac yang terlist
Dan di sini kita bisa menyimpannya dengan menekan tombol D (Dump), dan kita dapat mengambil nya di file mikrotik. atau lebih jelasnya kita menggunakan ftp untuk mengambilnya di file root mikrotik dengan nama `console-dump.txt` 

![Center](dump.png#width=300px)

Dan hasil mac ini kita bisa gunakan untuk sekedar tujuan ingin mengetahui perangkat yang terhubung ataupun bisa kita gunakan untuk Spoof Mac address pada tutorial selanjutnya.

- - -
