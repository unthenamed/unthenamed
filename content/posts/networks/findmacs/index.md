+++
	title = "Discover alamat MAC dengan Findmacs"
	date = 2022-04-15T06:21:11Z
#	description = "" # Used by description meta tag, summary will be used instead if not set or empty.
	robotsdisallow = false
	featured = false
	draft = false
	comment = true
	toc = true
	reward = true
	pinned = false

		categories = [
			"Networks"
		]

		tags = [
			"Mac",
			"FindMacs",
			"MacClone"
		]

		series = [
			"Artikel"
		]

		images = ["/images/mac.png"]

		aliases = [
			"/Findmacs"
		]
+++
Temukan alamat MAC untuk rentang IP menggunakan ARP

Alat ini akan menanyakan setiap IP dalam rentang tertentu dan mencetak alamat MAC yang diterima ke keluaran standar. Ini menggunakan protokol ARP. Perangkat yang terhubung ke jaringan yang tidak menggunakan protokol IP tidak akan ditemukan.

Opsional Anda dapat memberikan daftar alamat MAC untuk menyaring output. Filter dapat diatur untuk menampilkan alamat dalam daftar atau tidak dalam daftar.


<!--more-->
- - -
{{< adstex >}}
- - -


Compile
=======

Alat ini dikompilasi di Linux

    $ gcc findmacs.c -o findmacs

Penggunaan
=====

    Usage: findmacs [-apxvhV] [-t time] [-r IP/CIDR] [-l filename [-i]] interface
    
      -r IP/CIDR      Scan this IP range. If not given <localIP>/24 is used
      -l filename     Load MAC addresses listed in <filename> and use them as allowed.
                      Only addresses found in network and not in list will be reported.
      -t time         Set wait-for-reply timeout to <time> milliseconds. Default is 950 ms
      -i              Report MAC addresses found in list (invert report)
      -a              Accept ANY reply, even if it wasn't triggered by us
      -p              Print IP address being queried
      -x              Don't check root privileges
      -v              Increase verbosity level
      -h              Print this help
      -V              Print version and copyright information
 


Contoh keluaran
=============

    $ sudo ./findmacs -vr 192.168.0.1/28 eth0
    Interface eth0
    Local IP 192.168.0.49
    Local MAC 94:fg:80:b8:f5:45
    Scan range 192.168.0.1/28
    
    00:22:54:e3:c9:91       192.168.0.1     ->      94:de:86:a8:f5:45       192.168.0.19
    00:19:93:88:5b:54       192.168.0.4     ->      94:de:86:a8:f5:45       192.168.0.19
    00:22:15:4b:b7:88       192.168.0.6     ->      94:de:86:a8:f5:45       192.168.0.19
    00:22:4d:38:04:05       192.168.0.7     ->      94:de:86:a8:f5:45       192.168.0.19
    00:22:13:28:2c:2d       192.168.0.10    ->      94:de:86:a8:f5:45       192.168.0.19
    00:19:99:33:53:1b       192.168.0.12    ->      94:de:86:a8:f5:45       192.168.0.19
    00:19:99:83:21:7e       192.168.0.15    ->      94:de:86:a8:f5:45       192.168.0.19


*Source [drkblog](https://github.com/drkblog/findmacs)*



