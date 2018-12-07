# Orchestration Menggunakan Docker Compose
---

## Langkah 1 - Mendefinisikan Kontainer Pertama
---

ocker Compose didasarkan pada file docker-compose.yml. File ini mendefinisikan semua kontainer dan pengaturan yang Anda perlukan untuk meluncurkan kumpulan kluster Anda. Properti memetakan ke bagaimana Anda menggunakan perintah menjalankan docker, namun sekarang disimpan dalam kontrol sumber dan dibagikan bersama dengan kode Anda.

Format file didasarkan pada YAML
	
	container_name:
	property: value
	- or options
	
---
Mendefinisikan Kontainer Pertama
---

perintah untuk menentukan container yang disebut web, yang didasarkan pada pembuatan direktori saat ini.
	
	web:
		build: .

---

## Langkah 2 - Menentukan Pengaturan

Docker Compose mendukung semua properti yang dapat ditentukan menggunakan docker run. Untuk menghubungkan dua kontainer bersama-sama untuk menentukan 
properti tautan dan mencantumkan koneksi yang diperlukan. salin code di text editor
	 
	 links:
		- redis

Format yang sama digunakan untuk properti lain seperti port

	ports:
		- "3000"
		- "8000"

Dokumentasi tambahan tentang opsi dapat ditemukan di https://docs.docker.com/compose/compose-file/
		
---

**Tugas**

Perbarui Container web kami untuk mengekspos port 3001 dan membuat tautan ke container Redis kami.

---

## Langkah 3 - Mendefinisikan Container Kedua
---

Pada langkah sebelumnya, kami menggunakan Dockerfile di direktori saat ini sebagai basis untuk container kami. Pada langkah ini, kami ingin menggunakan image 
yang ada dari Docker Hub sebagai kontainer kedua. Untuk menemukan kontainer kedua Anda cukup menggunakan format yang sama seperti sebelumnya pada baris baru. 
Format YAML cukup fleksibel untuk mendefinisikan beberapa kontainer dalam file yang sama.

**Tugas: Tentukan Kontainer Kedua**

Tentukan kontainer kedua dengan nama redis yang menggunakan images redis. Mengikuti format YAML, detail kontainernya adalah:
		
		redis:
		image: redis:alpine
		volumes:
			- /var/redis/data:/data

---

## Langkah 4 - Docker Up
---

Dengan dibuatnya file docker-compose.yml, Anda dapat meluncurkan semua aplikasi dengan satu perintah **up**. Jika Anda ingin memunculkan satu kontainer, maka Anda dapat 
menggunakannya **up <name>**

-d menyatakan untuk menjalankan kontainer di latar belakang, serupa dengan ketika digunakan dengan **docker run**.

---
Tugas
---

Jalankan aplikasi Anda menggunakan 
	docker-compose up -d

   <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i1.jpg" alt="i1"/>

---

## Langkah 5 - Manajemen Docker
---

Tidak hanya Docker Compose dapat mengelola kontainer awal tetapi juga menyediakan cara mengelola semua kontainer menggunakan satu perintah. 
Misalnya, untuk melihat detail wadah yang diluncurkan yang dapat Anda gunakan
	
	docker-compose ps

  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i2.jpg" alt="i2"/>

Untuk mengakses semua log melalui satu aliran yang Anda gunakan
	
	docker-compose logs

  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i3.jpg" alt="i3"/>

Perintah lain mengikuti pola yang sama. Temukan dengan mengetik

	docker-compose

  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i4.jpg" alt="i4"/>

---
## Langkah 6 - Skala Docker
---

Saat Docker Compose memahami cara meluncurkan kontainer aplikasi Anda, ia juga dapat digunakan untuk menskala jumlah kontainer yang berjalan.
Opsi skala memungkinkan Anda menentukan layanan dan kemudian jumlah instance yang Anda inginkan. Jika angkanya lebih besar dari instance 
yang sudah berjalan, maka akan meluncurkan kontainer tambahan. Jika jumlahnya kurang, maka akan menghentikan kontainer yang tidak diinginkan.

---
Tugas
---

Skalakan jumlah kontainer web yang Anda jalankan menggunakan perintah
	
	docker-compose scale web=3
	
  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i5.jpg" alt="i5"/>

Anda dapat menskalakannya kembali menggunakan
	
	docker-compose scale web=1

  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i6.jpg" alt="i6"/>

---
## Langkah 7 - Berhenti Docker
---

Seperti ketika kami meluncurkan aplikasi, untuk menghentikan satu set kontainer Anda dapat menggunakan perintah
	
	docker-compose stop

  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i7.jpg" alt="i7"/>

Untuk menghapus semua kontainer, gunakan perintah

	docker-compose rm

  <img src="https://github.com/lilyastri/tct-docker2-lily/blob/master/i8.jpg" alt="i8"/>

---





		
