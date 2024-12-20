# todolist-multiperson

| Name           | NRP        | 
| ---            | ---        | 
| Amelia Nova Safitri | 5025231041 | 
| Tarisha Falah Basuki | 5025231043 |
| Putriani Pirma A. Sagala | 5025231045 | 

## 1. Ringkasan Singkat

- Final Project untuk mata kuliah “Pemrograman Website” adalah mengimplementasikan ilmu yang didapat dari mata kuliah ini untuk membuat sebuah web. Dari beberapa topik yang diusung, kelompok kami memilih topik “Multi Person To Do List”. 

- Sesuai dengan nama topik, web ini bertujuan untuk memungkinkan beberapa pengguna mengelola daftar tugas (to-do list) secara bersamaan. Fitur utama yang ditawarkan mencakup:  

  1. Manajemen Pengguna: Setiap pengguna dapat mendaftar, login, dan memiliki akun untuk mengakses to-do list mereka.  
  2. Pembuatan dan Pengelolaan Tugas: Pengguna dapat menambahkan, menandai sebagai selesai, dan menghapus tugas.  
  3. Menambahkan grup: Pengguna dapat menambahkan beberapa grup dalam satu akun.
  4. Menambahkan person: Pengguna dapat menambahkan person dalam satu grup satu daftar tugas dan berkolaborasi dalam penyelesaiannya.  
  5. Prioritas: Pengguna dapat mengatur tugas berdasarkan favorit (tingkat prioritas).

- Web ini dirancang menggunakan HTML, CSS, JavaScript (Frontend) dan didukung oleh MongoDB (Backend) untuk pengelolaan data. Framework seperti Bootstrap juga digunakan untuk mempercantik tampilan.

- Tujuan utama dari project ini adalah untuk menciptakan sebuah aplikasi berbasis web yang fungsional dan user-friendly, sehingga dapat mendukung kolaborasi dalam menyelesaikan berbagai tugas secara efisien.


## Tujuan Utama dan Manfaat dari Website

- Tujuan utama dari website "Multi Person To Do List" adalah untuk membantu pengguna dalam mengelola tugas-tugas secara efisien dan mendukung kolaborasi antar pengguna. Berikut adalah manfaatnya:
  1. Manajemen Tugas yang Terorganisir: Pengguna dapat menyusun dan memprioritaskan tugas dengan mudah.
  2. Aksesibilitas: Sistem berbasis web memungkinkan akses dari berbagai perangkat selama terhubung dengan internet.


<br>

## Soal 1

> Topologi terdiri dari node Wortel yang berupa DNS Master*. Selain itu, terdapat pula node Pokcoy sebagai DNS Slave*, yang bertugas sebagai cadangan dari node Wortel.
> <br> </br>
> Selanjutnya terdapat node Tomat dan Taoge yang bekerja sebagai Client*, tiga buah Web Server* yaitu Bayam, Buncis, dan Brokoli, serta Mayur sebagai Router*. Buatlah topologi sesuai dengan pembagian topologi [di sini](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) dan konfigurasi topologi [di sini](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Pastikan bahwa setiap node dapat terhubung ke Internet.

> _The topology consists of a Wortel node which is a DNS Master*. In addition, there is also a Pokcoy node as a DNS Slave*, which serves as a backup for the Wortel node._
> <br> </br>
> _Furthermore, there are Tomat and Taoge nodes that work as Client*, three Web Servers*, namely Bayam, Buncis, and Brokoli, then finally Mayur as Router*. Make a topology according to the topology division [here](https://docs.google.com/spreadsheets/d/1QKEZjixTStNbdXznOalJoJS0UQ6ed23o51pP8t8eAIM/edit?usp=sharing) and the topology configuration [here](https://drive.google.com/drive/folders/1ECQD6-cQkg0DzyflG-jSxJZaGaxg0KSU?usp=sharing). Make sure that each node can connect to the Internet._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/0c447f94-a3b5-419d-94b9-5ee933f20211)


- Explanation

  ### Membuat konfigurasi IP agar dapat terhubung ke internet
  - MayurRouter
    ```
    auto eth0
    iface eth0 inet dhcp=

    auto eth1
    iface eth1 inet static
    	address 10.83.1.1
    	netmask 255.255.255.0

    auto eth2
    iface eth2 inet static
	address 10.83.2.1
	netmask 255.255.255.0

    auto eth3
    iface eth3 inet static
	address 10.83.3.1
	netmask 255.255.255.0

    auto eth4
    iface eth4 inet static
	address 10.83.4.1
	netmask 255.255.255.0

    up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.83.0.0/16

    ```
  - TomatClient
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.1.2
	netmask 255.255.255.0
	gateway 10.83.1.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
	```
  - TaugeClient
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.1.3
	netmask 255.255.255.0
	gateway 10.83.1.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - PokcoyDNSSlave
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.2.2
	netmask 255.255.255.0
	gateway 10.83.2.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - WortelDNSMaster
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.2.3
	netmask 255.255.255.0
	gateway 10.83.2.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - BayamWebServer
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.3.2
	netmask 255.255.255.0
	gateway 10.83.3.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - BrokoliWebServer
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.4.2
	netmask 255.255.255.0
	gateway 10.83.4.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - BuncisWebServer
    ```
    auto eth0
    iface eth0 inet static
	address 10.83.4.3
	netmask 255.255.255.0
	gateway 10.83.4.1
    up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```

  

<br>

## Soal 2

> Tambahkan konfigurasi untuk domain bayam.yyy.com yang mengarah ke IP node Bayam di DNS Master. Dengan cara yang sama, buat konfigurasi domain brokoli.yyy.com yang mengarah ke IP node Brokoli dan domain buncis.yyy.com yang mengarah ke IP node Buncis. Simpan semua konfigurasi dalam folder Jarkom. Selama pengerjaan soal, ubah yyy menjadi kode kelompok masing-masing (contoh: A02).
> <br> </br>
> Jangan lupa update konfigurasi kedua client agar dapat berkomunikasi dengan semua domain tersebut.


> _Add a configuration for bayam.yyy.com domain that points to the Bayam node IP in the DNS Master. In the same way, create a brokoli.yyy.com domain configuration that points to the Brokoli node IP and a buncis.yyy.com domain that points to the Buncis node IP. Save all configurations in a folder called Jarkom. For this practicum, substitute yyy with the code of each group (ex: A02).
> <br> </br> 
> Don't forget to update the configuration of both clients so that they can communicate with the domains._

**Answer:**

- Screenshot
  ### ping bayam.F33.com
  ![image](https://github.com/user-attachments/assets/43f585a7-4430-48ad-88b7-64bc928770ce)

  ### ping brokoli.F33.com
  ![image](https://github.com/user-attachments/assets/abe2ccfb-ceca-46dd-8531-30e9f7a5bb61)

  ### ping buncis.F33.com
  ![image](https://github.com/user-attachments/assets/ebc8a8f9-eef2-43ee-8b4c-8622c27c975d)


- Explanation

  - Buka WortelDNSMaster dan lakukan:
     ```
     apt-get update
     ```
     ```
     apt-get install bind9 -y
     ```
  - Lakukan perintah pada WortelDNSMaster
     ```
     nano /etc/bind/named.conf.local
     ```
  - Isikan configurasi domain
     ```
     zone "bayam.F33.com" {
        type master;
        file "/etc/bind/jarkom/bayam.F33.com";
     };

     zone "brokoli.F33.com" {
        type master;
        file "/etc/bind/jarkom/brokoli.F33.com";
     };

     zone "buncis.F33.com" {
        type master;
        file "/etc/bind/jarkom/buncis.F33.com";
     };

     ```
  - Buat folder jarkom di dalam /etc/bind
     ```
     mkdir /etc/bind/jarkom
     ```
  - Copy file db.local pada path /etc/bind ke dalam folder jarkom dan ubah namanya menjadi:
     ```
     cp /etc/bind/db.local /etc/bind/jarkom/bayam.F33.com
     cp /etc/bind/db.local /etc/bind/jarkom/brokoli.F33.com
     cp /etc/bind/db.local /etc/bind/jarkom/buncis.F33.com
     ```
  - Buka masing-masing file dan edit dengan IP WortelDNSMaster masing-masing kelompok:
    - #### bayam.F33.com
     ```
     nano /etc/bind/jarkom/bayam.F33.com
     ```
     ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     bayam.F33.com. root.bayam.F33.com. (
                        2024100201      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      bayam.F33.com.
	@       IN      A       10.83.3.2
	@       IN      AAAA    ::1
     ```
     ![image](https://github.com/user-attachments/assets/65baab7e-a30c-4420-8ea4-2530579a73ab)
 
     - #### brokoli.F33.com
     ```
     nano /etc/bind/jarkom/brokoli.F33.com
     ```
     ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     brokoli.F33.com. root.brokoli.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      brokoli.F33.com.
	@       IN      A       10.83.4.2
	@       IN      AAAA    ::1
     ```
     ![image](https://github.com/user-attachments/assets/4487d1d2-4106-4cfa-869b-93efa2420c70)
 
     - #### buncis.F33.com
     ```
     nano /etc/bind/jarkom/buncis.F33.com
     ```
     ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     buncis.F33.com. root.buncis.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      buncis.F33.com.
	@       IN      A       10.83.4.3
	@       IN      AAAA    ::1
     ```
     ![image](https://github.com/user-attachments/assets/595433c4-a1a5-4a33-bfa9-5db2d86ce15d)
     
  - Lakukan
     ```
     service bind9 restart
     ```
  - Kemudian
     ```
     nano /etc/resolv.conf (di setiap client yang ingin menguji)
     ```
     ```
     #nameserver 192.168.122.1
     nameserver 10.83.2.3 // IP WortelDNSMaster
     ```
  - Cek apakah sudah terhubung dengan melakukan ping
    ```
    ping -4 bayam.F33.com -c 5
    ping -4 brokoli.F33.com -c 5
    ping -4 buncis.F33.com -c 5
    ```

    

<br>

## Soal 3

> Tambahkan domain alias berupa www.bayam.yyy.com pada alamat bayam.yyy.com dan www.brokoli.yyy.com pada alamat brokoli.yyy.com.

> _Add a domain alias in the form of www.bayam.yyy.com to the bayam.yyy.com address and www.brokoli.yyy.com to the brokoli.yyy.com address._

**Answer:**

- Screenshot
  ### ping www.bayam.F33.com
  ![image](https://github.com/user-attachments/assets/e4536672-80f9-4a56-b8c3-079096421cad)

  ### ping www.brokoli.F33.com
  ![image](https://github.com/user-attachments/assets/a3c4d338-5a96-41e8-a58b-ed443af5f838)


- Explanation

  Record CNAME adalah sebuah record yang membuat alias name dan mengarahkan domain ke alamat/domain yang lain.

  #### Langkah-langkah membuat record CNAME pada bayam.F33.com:
  - Buka file bayam.F33.com pada server WortelDNSMaster dan tambahkan konfigurasi seperti pada gambar berikut:
    ```
    nano /etc/bind/jarkom/bayam.F33.com
    ```
    ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     bayam.F33.com. root.bayam.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      bayam.F33.com.
	@       IN      A       10.83.3.2
	www     IN      CNAME   bayam.F33.com.
	@       IN      AAAA    ::1
    ```
    ![image](https://github.com/user-attachments/assets/0d4a3423-a95e-4405-8730-dfad4ce6c034)

  - Restart bind9
    ```
    service bind9 restart
    ```
  - Cek dengan melakukan ping www.bayam.F33.com -c 5.

  #### Langkah-langkah membuat record CNAME pada brokoli.F33.com:
  - Buka file brokoli.F33.com pada server WortelDNSMaster dan tambahkan konfigurasi seperti pada gambar berikut:
    ```
    nano /etc/bind/jarkom/brokoli.F33.com
    ```
    ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     brokoli.F33.com. root.brokoli.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      brokoli.F33.com.
	@       IN      A       10.83.4.2
	www     IN      CNAME   brokoli.F33.com.
	@       IN      AAAA    ::1
    ```
    ![image](https://github.com/user-attachments/assets/7012bd83-1660-4800-a2bf-e0435b0dfb08)

  - Restart bind9
    ```
    service bind9 restart
    ```
  - Cek dengan melakukan ping www.brokoli.F33.com -c 5.

    

    

<br>

## Soal 4

> Tambahkan record reverse domain untuk domain brokoli.yyy.com dan buncis.yyy.com.

> _Add a reverse domain record for brokoli.yyy.com and buncis.yyy.com domains._

**Answer:**

- Screenshot
  ### domain alias brokoli.F33.com
  ![image](https://github.com/user-attachments/assets/a7eb5d2d-9063-4b0a-9e45-056b87157efc)




  ### domain alias buncis.F33.com
  ![image](https://github.com/user-attachments/assets/85db7eb1-2da8-4a61-9ed0-3d0e7e19d4a1)



- Explanation
  - Edit file /etc/bind/named.conf.local pada WortelDNSMaster
    ```
    nano /etc/bind/named.conf.local
    ```
  - Lalu tambahkan konfigurasi berikut ke dalam file named.conf.local. Tambahkan reverse dari 3 byte awal dari IP yang ingin dilakukan Reverse DNS. Gunakan IP 10.83.2 untuk IP dari records, maka reversenya adalah 2.83.10
    ```
    zone "4.83.10.in-addr.arpa" {
    	type master;
    	file "/etc/bind/jarkom/4.83.10.in-addr.arpa";
    };
    ```
  - Copykan file db.local pada path /etc/bind ke dalam folder jarkom yang baru saja dibuat dan ubah namanya menjadi 4.83.10.in-addr.arpa
    ```
    cp /etc/bind/db.local /etc/bind/jarkom/4.83.10.in-addr.arpa
    ```
  - Edit file 4.83.10.in-addr.arpa menjadi seperti gambar di bawah ini
    ```
    nano /etc/bind/jarkom/4.83.10.in-addr.arpa
    ```
  - IP brokoli adalah 10.83.4.2
    ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     brokoli.F33.com. root.brokoli.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	4.83.10.in-addr.arpa.   IN      NS      brokoli.F33.com.
	2                       IN      PTR     brokoli.F33.com.
    ```
  - brokoli.F33.com
      ![image](https://github.com/user-attachments/assets/ec8c785f-3641-4b35-b90c-c33e3fb69fbe)
  - Edit file 4.83.10.in-addr.arpa menjadi seperti gambar di bawah ini
    ```
    nano /etc/bind/jarkom/4.83.10.in-addr.arpa
    ```
  - IP buncis adalah 10.83.4.3
    ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     buncis.F33.com. root.buncis.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	4.83.10.in-addr.arpa.   IN      NS      buncis.F33.com.
	3                       IN      PTR     buncis.F33.com.
    ```
  - buncis.F33.com
      ![image](https://github.com/user-attachments/assets/6f4029ba-cf4b-46cc-bd69-c15c87661693)



  - Kemudian restart bind9 dengan perintah
    ```
    service bind9 restart
    ```
  - Untuk mengecek apakah konfigurasi sudah benar atau belum, lakukan perintah berikut pada client TomatClient
    ```
    // Pastikan nameserver di /etc/resolv.conf telah dikembalikan sama dengan nameserver dari MayurRouter
    apt-get update
    apt-get install dnsutils

    //Kembalikan nameserver agar tersambung dengan WortelDNSMaster
    host -t PTR 10.83.4.2 // brokoli
    host -t PTR 10.83.4.3 //buncis
    ```




<br>

## Soal 5

> Ubah record SOA dari domain bayam.yyy.com sesuai dengan ketentuan berikut:
> - Lama waktu server slave menunggu untuk mengecek salinan baru server master adalah sebesar 2 jam.
> - Field yang mengatur revisi file zona ini diubah menjadi tanggal awal praktikum (format YYYYMMDD) kemudian diikuti dengan nomor kelompok (contoh untuk kelompok A02 maka nomornya 02).
> - Lamanya waktu server harus menunggu untuk meminta pembaruan lagi dari nameserver master yang tidak responsif sebesar 30 menit.
> - Lama waktu nama domain di-cache secara lokal sebelum kadaluarsa dan kembali ke nameserver otoritatif untuk informasi terbaru sebesar 12 jam.
> - Jika server slave tidak mendapatkan respons dari server master dalam waktu 2 minggu, server tersebut harus berhenti merespons kueri untuk zona tersebut.

> _Change the SOA record of the bayam.yyy.com domain according to the following conditions:_
> - The length of time the slave server waits to check for a new revision of the master server is 2 hours.
> - The field that regulates the revision of this zone file is changed to the start date of the practicum (YYYYMMDD format) then followed by the group number (ex: for A02 the group number would be 02).
> - The length of time the server has to wait to request another update from an unresponsive master nameserver is 30 minutes.
> - The length of time a domain name is cached locally before it expires and returns to an authoritative nameserver for up-to-date information is 12 hours.
> - If the slave server does not get a response from the master server within 2 weeks, it must stop responding to queries for that zone.

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/f7cc65da-49d2-4441-bb1e-52b66c12ebb5)


- Explanation
  - edit record
    ```
    nano /etc/bind/jarkom/bayam.F33.com
    ```
    ``` 
	;
	; BIND data file for local loopback interface
	;
	$TTL    43200   ; 12 jam
	@       IN      SOA     bayam.F33.com. root.bayam.F33.com. (
	                        2024100133      ; Serial
	                        7200            ; Refresh (2 jam)
	                        1800            ; Retry (30 menit)
	                        1209600         ; Expire (2 minggu)
	                        43200    )      ; Negative Cache TTL (12 jam)
	;
	@       IN      NS      bayam.F33.com.
	@       IN      A       10.83.3.2
	www     IN      CNAME   bayam.F33.com.
	@       IN      AAAA    ::1
    ```
  - $TTL: Diubah menjadi 43200 detik (12 jam).
  - Serial: Menggunakan format tanggal 2024100133 (nomor kelompok 33)
  - Refresh: Diubah menjadi 7200 detik (2 jam).
  - Retry: Diubah menjadi 1800 detik (30 menit).
  - Expire: Diubah menjadi 1209600 detik (2 minggu).
  - Negative Cache TTL: Diubah menjadi 43200 detik (12 jam).

<br>

## Soal 6

> Untuk menangani request yang berlebih dari client ke ketiga alamat yang tadi dibuat, konfigurasikan node Pokcoy sebagai DNS Slave yang bekerja untuk DNS Master Wortel.

> _To handle excess requests from the client to the three addresses created, configure the Pokcoy node as the DNS Slave that works for Wortel DNS Master._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/85f7892c-9365-4217-9de2-ac2c62055ea2)


- Explanation

  - Edit file /etc/bind/named.conf.local dan sesuaikan dengan syntax berikut
    ```
    nano /etc/bind/named.conf.local
    ```
    ```
    zone "bayam.F33.com" {
        type master;
        notify yes;
        also-notify { 10.83.2.2; };     //masukkan IP PokcoyDNSSlave
        allow-transfer { 10.83.2.2; };   //masukkan IP PokcoyDNSSlave
        file "/etc/bind/jarkom/bayam.F33.com";
    };
    
    zone "brokoli.F33.com" {
        type master;
        notify yes;
        also-notify { 10.83.2.2; }; // Masukan IP PokcoyDNSSlave
        allow-transfer { 10.83.2.2; }; // Masukan IP PokcoyDNSSlave
        file "/etc/bind/jarkom/brokoli.F33.com";
    };

    zone "buncis.F33.com" {
        type master;
        notify yes;
        also-notify { 10.83.2.2; }; // Masukan IP PokcoyDNSSlave
        allow-transfer { 10.83.2.2; }; // Masukan IP PokcoyDNSSlave
        file "/etc/bind/jarkom/buncis.F33.com";
    };

    zone "4.83.10.in-addr.arpa" {
    	type master;
    	file "/etc/bind/jarkom/4.83.10.in-addr.arpa";
    };
    ```
  - Lakukan restart bind9
    ```
    service bind9 restart
    ```

    
  #### Konfigurasi pada server PokcoyDNSSlave
  - Buka pokcoy dan update package lists dengan menjalankan command:
    ```
    apt-get update
    ```
  - Setelah melakukan update silahkan install aplikasi bind9 pada pokcoy dengan perintah:
    ```
    apt-get install bind9 -y
    ```
  - Kemudian buka file /etc/bind/named.conf.local pada pokcoy dan tambahkan syntax berikut:
    ```
    nano /etc/bind/named.conf.local
    ```
    ```
    zone "bayam.F33.com" {
        type slave;
        masters { 10.83.2.3; };
        file "/var/lib/bind/bayam.F33.com";
    };

    zone "brokoli.F33.com" {
        type slave;
        masters { 10.83.2.3; };
        file "/var/lib/bind/brokoli.F33.com";
    };

    zone "buncis.F33.com" {
        type slave;
        masters { 10.83.2.3; };
        file "/var/lib/bind/buncis.F33.com";
    };
    ```
  - Lakukan restart bind9
    ```
    service bind9 restart
    ```


  #### Testing
  - Pada server wortel silahkan matikan service bind9
    ```
    service bind9 stop
    ```
  - Pada client tomat pastikan pengaturan nameserver mengarah ke IP wortel dan IP pokcoy
    ```
    #nameserver 192.168.122.1
    nameserver 10.83.2.3
    nameserver 10.83.2.2
    ```
  - Lakukan ping ke bayam.com pada client tomat. Jika ping berhasil maka konfigurasi DNS slave telah berhasil
    ```
    ping -4 bayam.F33.com -c 5
    ```

<br>

## Soal 7

> Karena membutuhkan tempat untuk menyimpan resep brokoli, buatlah subdomain berupa vitamin.brokoli.yyy.com dengan alias www.vitamin.brokoli.yyy.com dengan mendelegasikannya dari Wortel ke Pokcoy dengan alamat IP menuju Brokoli yang diatur di folder Vitamin.

> _Since we need a place to store Brokoli recipes, create a subdomain in the form of vitamin.brokoli.yyy.com with an alias of www.vitamin.brokoli.yyy.com by delegating it from Wortel to Pokcoy with an ip to the Brokoli node in a folder called Vitamin._

**Answer:**

- Screenshot
  ![image](https://github.com/user-attachments/assets/45f3f3b3-225f-4ffe-9d96-72a22fa2d859)


- Explanation

#### Konfigurasi Pada Server Wortel
Pada server Wortel, Membuat Subdomain dan Delegasikan ke Server Pakcoy
    
- Mengedit file /etc/bind/jarkom/brokoli.F33.com. dan mendelegasikan subdomain vitamin.brokoli.F33.com ke ns1 (Pokcoy) dengan alamat IP 10.83.2.2.
    ```
    nano /etc/bind/jarkom/brokoli.F33.com
    ```
- Konfigurasi pada file /etc/bind/jarkom/brokoli.F33.com
    ```
    	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     brokoli.F33.com. root.brokoli.F33.com. (
	                      2024100201        ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@               IN      NS      brokoli.F33.com.
	@               IN      A       10.83.4.2             ; IP brokoli
	www             IN      CNAME   brokoli.F33.com.
	//vitamin       IN      A       10.83.2.2             ; subdomain ke IP pokcoy
	//www.vitamin   IN      CNAME   vitamin.brokoli.F33.com.; alias domain
	ns1             IN      A       10.83.2.2             ; IP pokcoy
	vitamin         IN      A       ns1
    ```
- edit file `nano /etc/bind/named.conf.options`
  ```
  – dnssec-validation auto; jadikan comment
  – tambahkan allow-query{any;};
  ```
- ```
  service bind9 restart
  ```

#### Konfigurasi Zona di Server Pakcoy 
Di server Pokcoy, membuat file zona untuk subdomain vitamin.brokoli.F33.com dan mendefinisikan alamat IP tujuan untuk subdomain dan mengatur CNAME untuk aliasnya
- ```
  nano /etc/bind/named.conf.options
  ```
- ```
  – dnssec-validation auto; jadikan comment
  – tambahkan allow-query{any;};
  ```
- Mengedit file /etc/bind/named.conf.local
  ```
  nano /etc/bind/named.conf.local
  ```
- Konfigurasi file zona pada file named.conf.local
  ```
  zone "vitamin.brokoli.F33.com" {
        type master;
        file "/etc/bind/vitamin/vitamin.brokoli.F33.com";
	};
  ```
- Membuat folder vitamin untuk menyimpan file zona
  ```
  mkdir /etc/bind/vitamin
  ```
 - copy db local ke vitamin.brokoli.F33.com
   ```
   cp /etc/bind/db.local /etc/bind/vitamin/vitamin.brokoli.F33.com
   ```

 - Mengedit file /etc/bind/vitamin/vitamin.brokoli.F33.com
   ```
   nano /etc/bind/vitamin/vitamin.brokoli.F33.com
   ```
   ```
    	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     vitamin.brokoli.F33.com. root.vitamin.brokoli.F33.com. (
	                        2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      vitamin.brokoli.F33.com.
	www     IN      CNAME   vitamin.brokoli.F33.com. ; alias domain
	@       IN      A       10.83.4.2             ; IP brokoli
    ```

  - Setelah melakukan perubahan di folder bind, restart bind9
    ```
    service bind9 restart
    ```

#### Testing
 
  - Pada client tomat pastikan pengaturan nameserver mengarah ke IP wortel dan IP pokcoy `nano /etc/resolv.conf`
    ```
    #nameserver 192.168.122.1
    nameserver 10.83.2.3
    nameserver 10.83.2.2
    ```
  - Lakukan ping ke vitamin.brokoli.F33.com dan www.vitamin.brokoli.F33.com pada client. Jika ping berhasil maka konfigurasi DNS slave telah berhasil
    ```
    ping -4 vitamin.brokoli.F33.com -c 2
    ```
    ```
    ping -4 www.vitamin.brokoli.F33.com -c 2
    ```
    
<br>

## Soal 8

> Buatlah subdomain khusus untuk kandungan brokoli dengan akses k1.vitamin.brokoli.yyy.com dengan alias www.k1.vitamin.brokoli.yyy.com yang mengarah ke IP brokoli dan diatur di folder k1.  

> _Create a special subdomain for Brokoli content called k1.vitamin.brokoli.yyy.com with an alias called www.k1.vitamin.brokoli.yyy.com that point to Brokoli node and are organized in a folder called k1._

**Answer:**

- Screenshot
  #### ping k1.vitamin.brokoli.F33.com
  ![image](https://github.com/user-attachments/assets/623e03cb-953e-40b2-8b8a-5345a2926837)

  ### ping www.k1.vitamin.brokoli.F33.com
  ![image](https://github.com/user-attachments/assets/e9fb77bc-e18d-464b-a586-1ab238f20bc7)



- Explanation

  - Membuat folder k1
    ```
    mkdir /etc/bind/k1
    ```
  - Edit file vitamin.brokoli.F33.com dalam folder vitamin
    nano /etc/bind/vitamin/vitamin.brokoli.F33.com
    ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     vitamin.brokoli.F33.com. root.vitamin.brokoli.com. (
    				2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      vitamin.brokoli.F33.com.
	@       IN      A       10.83.4.2
	www     IN      CNAME   vitamin.brokoli.F33.com.
	ns2	IN	A	10.83.2.2	; IP pokcoy
	k1	IN	NS	ns1
	@       IN      AAAA    ::1
    ```
  - Tambahkan zone pada named.conf.local
    ```
    nano /etc/bind/named.conf.local
    ```
    ```
	zone "k1.vitamin.brokoli.F33.com" {
		type master;
		file "/etc/bind/k1/k1.vitamin.brokoli.F33.com";
	};
	```
  - copy file db.local ke k1.vitamin.brokoli.F33.com di folder k1
    ```
    cp /etc/bind/db.local /etc/bind/k1/k1.vitamin.brokoli.F33.com
    ```
  - Edit file k1.vitamin.brokoli.F33.com
    ```
    nano /etc/bind/k1/k1.vitamin.brokoli.F33.com
    ```
    ```
	;
	; BIND data file for local loopback interface
	;
	$TTL    604800
	@       IN      SOA     k1.vitamin.brokoli.F33.com. root.k1.vitamin.brokoli.com. (
    				2024100201      ; Serial
	                         604800         ; Refresh
	                          86400         ; Retry
	                        2419200         ; Expire
	                         604800 )       ; Negative Cache TTL
	;
	@       IN      NS      k1.vitamin.brokoli.F33.com.
	@       IN      A       10.83.4.2	; IP brokoli
	www     IN      CNAME   k1.vitamin.brokoli.F33.com.
	@       IN      AAAA    ::1

	```

  - Lakukan restart bind9
    ```
    service bind9 restart
    ```
  - #### Test ping
    ```
    ping -4 k1.vitamin.brokoli.F33.com -c 2
    ping -4 www.k1.vitamin.brokoli.F33.com -c 2
    ```

<br>

## Soal 9

> Bayam, Brokoli, dan Buncis masing-masing berfungsi sebagai web server nginx yang menyajikan resep khusus untuk jenis sayuran yang mereka tangani. Untuk mengaktifkan web server pada masing-masing worker, lakukan deployment website menggunakan sumber yang tersedia di sayur_webserver_nginx. Tambahkan konfigurasi untuk log error ke file /var/log/nginx/error.log dan log access ke file /var/log/nginx/access.log.

> _Bayam, Brokoli, and Buncis each function as nginx web servers that serve special recipes for the type of vegetables they handle. To activate the web server on each worker, do the deployment using the resources available in sayur_webserver_nginx. Add configuration for error log to the file /var/log/nginx/error.log and access log to the file /var/log/nginx/access.log._

**Answer:**

- Screenshot
- ##### bayam
  ![image](https://github.com/user-attachments/assets/f411c90c-6bf7-42ad-8a15-f6e574439658)

  
- ##### brokoli
  ![image](https://github.com/user-attachments/assets/a7bef577-72e6-4e9f-897c-2cd38ea0693a)

  
- ##### buncis
  ![image](https://github.com/user-attachments/assets/3438254b-72f6-4bb2-93cd-1eb8bd4a6bdd)



- Explanation
  - lakukan instalasi dan update pada *masing masing web server nginx*
    ```
    apt-get update && apt-get install nginx && apt install nginx php php-fpm -y && apt-get install unzip && service nginx start && service php7.2-fpm start
	```
    ![image](https://github.com/user-attachments/assets/d75a0e24-0b68-426a-94f4-9735ead8424f)

  - Masuk ke `cd var/www/`
  - copy file sayur.zip ke bayam di direktori var/www
    ```
    wget -O sayur.zip "https://docs.google.com/uc?export=download&id=1tFDk7pKRQLd3BMUcyvfAfEL-drvIxdSl"
    ```
  - pastikan sayur.zip sudah ter-download (gunakan `ls`)
  - jangan lupa unzip filenya
    ```
    unzip sayur.zip
    ```
    ![image](https://github.com/user-attachments/assets/e40c641d-bcf8-4788-b53a-1ff11ce0fe51)

  - `nano /etc/nginx/sites-available/sayur_webserver_nginx`
    ```
    server {

		listen 80;
    		listen [::]:80;

		root /var/www/sayur_webserver_nginx;

		index index.php index.html index.htm;
		server_name _;

		location / {
			try_files $uri $uri/ /index.php?$query_string;
		}

		# pass PHP scripts to FastCGI server
		location ~ \.php$ {
			include snippets/fastcgi-php.conf;
			fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
	}

    location ~ /\.ht {
		deny all;
	}

	error_log /var/log/nginx/error.log;
	access_log /var/log/nginx/access.log;
    }
    ```
  - membuat symlink dari file konfigurasi NGINX yang ada di `/etc/nginx/sites-available/sayur_webserver_nginx` ke direktori `/etc/nginx/sites-enabled` untuk mengaktifkan virtual host
    ```
    ln -s /etc/nginx/sites-available/sayur_webserver_nginx /etc/nginx/sites-enabled
    ```
  - hapus default pada direktori `sites-enabled` untuk mengindari tabrakan konfigurasi
    ```
    rm -r /etc/nginx/sites-enabled/default
    ```
  - jangan lupa restart nginx
    ```
    service nginx restart
    ```

    #### Pada TomatClient:
    ```
	apt-get update
	apt-get install lynx
	lynx 10.83.3.2 ; untuk mengakses resep bayam
	lynx 10.83.4.2 ; untuk mengakses resep brokoli
	lynx 10.83.4.3 ; untuk mengakses resep buncis
    ```

<br>

## Soal 10

> Pada masing masing worker nginx, akan terdapat beberapa hal yang perlu diperbaiki pada resource yang diberikan untuk bisa menampilkan resep saat halaman dimuat. Analisis kesalahan yang ada di resource melalui file /var/log/nginx/error.log dan perbaiki hingga halaman bisa menampilkan resep sesuai dengan worker nya.

> _On each nginx worker, there will be several things that need to be fixed in the resources provided to be able to display recipes when the page is loaded. Analyze the errors in the resource through the /var/log/nginx/error.log file and fix it until the page can display recipes according to its worker._

**Answer:**

- Screenshot
- ##### BayamWebServer
  ![image](https://github.com/user-attachments/assets/760f6882-e1a1-4b23-a0a5-78e471d7c0b8)

  
- ##### BrokoliWebServer
  ![image](https://github.com/user-attachments/assets/9651c795-c0f6-46b8-b770-0653f79be326)

  
- ##### BuncisWebServer
  ![image](https://github.com/user-attachments/assets/623f7888-bf63-49cc-bc69-4155a11d696a)



- Explanation

#### Konfigurasi pada masing masing WebServer

  - Masuk folder /var/www/
  ```
  cd /var/www/
  ```
  - Mengedit file sayur_webserver_nginx/index.php
  ```
  nano sayur_webserver_nginx/index.php
  ```
  - Konfigurasi file index.php
  ```
  <?php
  $hostname = gethostname();
  $date = date('l, d F Y H:i:s');
  $php_version = phpversion();
  $visitor_ip = $_SERVER['REMOTE_ADDR'];
 
  echo "<h1>Selamat Datang di Situs Resep Sayuran!</h1>";
  echo "<p>Pengunjung dari IP: <strong>$visitor_ip</strong></p>";
  echo "<p>Versi PHP: <strong>$php_version</strong></p>";
  echo "<p>Waktu: <strong>$date</strong></p>";
  echo "<hr>";
  echo "<p>Saat ini Anda sedang mengakses resep dari sayur: <strong>$hostname</strong></p>";
 
  switch ($hostname) {
      case 'BayamWebServer':
          if (!@include 'resep1.php') {
              echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
              error_log("File resep_1.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
          }
          break;
      case 'BuncisWebServer':
          if (!@include 'resep2.php') {
              echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
              error_log("File resep_2.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
          } 
          break;
      case 'BrokoliWebServer':
          if (!@include 'resep3.php') {
              echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
              error_log("File resep_3.php tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
          }
          break;
      default:
          echo "<p>Gagal Memuat Resep! Cek Error Log untuk info lebih lanjut.</p>";
          error_log("Hostname tidak ditemukan!\n", 3, "/var/log/nginx/error.log");
          break;
  }
  ?>

  ```
  - Restart nginx
  ```
  service nginx restart
  ```

#### Testing
Lakukan testing pada Client

  - Untuk mengakses resep bayam
  ```
  lynx 10.83.3.2
  ```
  - Untuk mengakses resep brokoli
  ```
  lynx 10.83.4.2
  ```
  - Untuk mengakses resep buncis
  ```
  lynx 10.83.4.3
  ```

<br>

## Soal 11

> Setelah website berhasil dideploy pada masing-masing worker (Bayam, Brokoli, dan Buncis) dan halaman dapat menampilkan resep sayuran yang sesuai,  buatlah custom access log ke file /var/log/nginx/access.log di masing-masing web server worker menggunakan format log tertentu seperti di bawah:
> - Tanggal dan waktu akses dalam format standar log.
Nama worker yang sedang dilayani (misalnya: Bayam, Brokoli, atau Buncis).
> - Alamat IP klien yang mengakses website.
> - Metode HTTP dan URI yang diakses oleh klien.
> - Status respons HTTP yang diberikan oleh server.
> - Jumlah byte yang dikirimkan dalam respons.
> - Waktu yang dihabiskan oleh server untuk menangani permintaan.
> <br> </br>
> Contoh format log yang sesuai: 
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned stat


> _After successfully deploying the website on each worker (Bayam, Brokoli, and Buncis) and ensuring the pages display the appropriate vegetable recipes, create a custom access log file at /var/log/nginx/access.log on each web server worker using a specific log format as described below:_
> - _Access date and time in standard log format._
> - _Name of the worker serving the request (e.g., Bayam, Brokoli, or Buncis)._
> - _Client IP address accessing the website._
> - _HTTP method and URI accessed by the client._
> - _HTTP response status provided by the server.__
> - _Number of bytes sent in the response.
> - _Time taken by the server to handle the request._
> <br> </br>
> _Example of the appropriate log format:
[01/Oct/2024:11:30:45 +0000] Jarkom Node Bayam Access from 192.168.1.15 using method "GET /resep/bayam HTTP/1.1" returned status 200 with 2567 bytes sent in 0.038 seconds_


**Answer:**

- Screenshot
- ##### bayamwebserver
  ![image](https://github.com/user-attachments/assets/bb2690af-cccb-4862-8d36-d5188f483fbd)


- ##### brokoliwebserver
  ![image](https://github.com/user-attachments/assets/f3850df1-5355-4bab-b3f9-5aa4fc4a83e5)


- ##### bunciswebserver
  ![image](https://github.com/user-attachments/assets/e09aea74-682b-499c-9e7b-31ced94265e7)
  

- Explanation
- #### Konfigurasi pada masing masing WebServer
- Mengedit file etc/nginx/nginx.conf
  ```
  nano etc/nginx/nginx.conf
  ```
- Tambahkan konfigurasi seperti dibawah 
  ```
  log_format custom_log '[$time_local] Jarkom Node $hostname Access from $remote_addr using method "$request" returned status $status with $body_bytes_sent bytes sent in $request_time seconds';
  ```
- Ubah bagian access_log /var/log/nginx/access.log menjadi seperti dibawah
  ```
  access_log /var/log/nginx/access.log custom_log
  ```
- ##### Konfigurasi pada etc/nginx/nginx.conf pada masing-masing WebServer bisa dilihat sepeti dibawah
  ![image](https://github.com/user-attachments/assets/a813a210-080a-4ccb-bc81-f30c0d1d5665)
  ![image](https://github.com/user-attachments/assets/10d8c96f-4d01-4278-87c0-3e25d81b18fa)
  ![image](https://github.com/user-attachments/assets/71f2a3fc-d488-4659-8979-e642cdc1e6e7)
  
- Mengedit file /etc/nginx/sites-available/sayur_webserver_nginx
  ```
  nano /etc/nginx/sites-available/sayur_webserver_nginx
  ```
- Ubah pada bagian access_log /var/log/nginx/access.log seperti dibawah
  ```
  access_log /var/log/nginx/access.log custom_log;
  ```
- ```
  service nginx restart
  ```
#### Konfigurasi pada /etc/nginx/sites-available/sayur_webserver_nginx di masing-masing WebServer bisa diliat seperti dibawah
  ![image](https://github.com/user-attachments/assets/d6b6fb24-548c-4b3b-b6a0-9b11b45d21e0)

 #### Testing
 - Lakukan pemeriksaan log pada masing-masing WebServer
   ```
   tail -f /var/log/nginx/access.log
   ```

<br>

## Soal 12

> Informasi vitamin pada sayur brokoli akan ditampilkan pada subdomain vitamin.brokoli.yyy.com di node brokoli, buatlah DocumentRoot yang disimpan pada /var/www/vitamin.brokoli.yyy. Konfigurasikan webserver dengan nama server vitamin.brokoli.yyy.com dan server alias www.vitamin.brokoli.yyy.com. Lakukan konfigurasi Apache Web Server pada Brokoli dengan menggunakan sumber yang tersedia di [sini](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2).

> _For information on vitamins in brokoli will be displayed on the vitamin.brokoli.yyy.com subdomain on the brokoli node, create a DocumentRoot stored in /var/www/vitamin.brokoli.yyy. Configure the web server with the server name vitamin.brokoli.yyy.com and server alias www.vitamin.brokoli.yyy.com. Configure the Apache Web Server on Brokoli using [this resource](https://docs.google.com/uc?export=download&id=1QbGkKXo3jt4c68AdVAkl1hD4LolTUPg2)._

**Answer:**

- Screenshot

#### nutrisi
- Halaman depan nutrisi
  ![image](https://github.com/user-attachments/assets/1777ecc2-530e-4189-a59d-d56a13ff327f)
- Isi Parent Directory
  ![image](https://github.com/user-attachments/assets/aa731c95-6192-419a-bd8f-983b13e478e0)
- Isi file-file yang ada di nutrisi
  ![image](https://github.com/user-attachments/assets/f0c8a948-9f99-4b6a-b0e0-75e2a39ad86e)
  ![image](https://github.com/user-attachments/assets/17657493-673a-4631-adc9-3131e4b29292)
  ![image](https://github.com/user-attachments/assets/b3dd3ce7-bd25-4895-9858-0c74ac0caea8)

#### publik
 - Halaman depan publik
 ![image](https://github.com/user-attachments/assets/32146982-9146-4973-9dc4-a2ac8406ca0d)
  - Isi Parent Directory
  ![image](https://github.com/user-attachments/assets/d8253d11-2901-4b95-805f-99ee7fa0a0de)
  - Isi file-file yang ada di publik
  ![image](https://github.com/user-attachments/assets/a987cd9e-d879-4368-8156-1a2419093b27)
  ![image](https://github.com/user-attachments/assets/f17483e4-fbbc-4aeb-960d-59881e888ee5)
  ![image](https://github.com/user-attachments/assets/7e8e1950-0255-4769-99d7-364f5a96cc68)
  ![image](https://github.com/user-attachments/assets/efc0d861-7efb-4d53-9bb5-39b299923081)
  
- #### secret
- Halaman depan secret
  ![image](https://github.com/user-attachments/assets/b53cf075-14de-41f8-a97b-770363087f25)
- Parent Diirectory secret
  ![image](https://github.com/user-attachments/assets/db9fbb24-6606-406f-912f-2cbd490a3cd0)
- Isi dari file yang ada di secret
  ![image](https://github.com/user-attachments/assets/e809b8a7-64c9-4087-9b90-d0acf7f4d0e5)

- Explanation
#### Buka BrokoliWebServer
- Jalankan perintah
  ```
  service nginx stop
  apt-get install apache2 -y
  service apache2 start
  apt-get install wget -y
  apt-get install unzip -y
  ```
- Ganti apache ke port 8080
  ```
  nano /etc/apache2/ports.conf
  ```
- Sesuaikan konfigurasi seperti dibawah
  ```
  Listen 8080
  <IfModule ssl_module>
        Listen 443
  </IfModule>

  <IfModule mod_gnutls.c>
        Listen 443
  </IfModule>
  ```
- Edit file 000-default.conf
  ```
  nano /etc/apache2/sites-available/000-default.conf
  ```
- Ganti menjadi 8080
  ```
  <VirtualHost *:8080>
  ```
- Membuat folder vitamin.brokoli.F33
  ```
  mkdir /var/www/vitamin.brokoli.F33
  ```
  ```
  cd /var/www/vitamin.brokoli.F33
  ```
- Mendownload file zip
  ```
  wget -O vitamin.brokoli.F33.com.zip "https://docs.google.com/uc?export=download&id=1NhsaTLD4Zk06BZJCqdN_oqoxB3uIg2C7"
  ```
- Lakukan Unzip file zip tersebut
  ```
  unzip vitamin.brokoli.F33.com.zip
  ```
- Ubah nama file zip yang sudah diunzip
  ```
  mv vitamin.brokoli.yyy.com vitamin.brokoli.F33.com
  ```
- Pindahkan isi file ke direktori sekarang berada
  ```
  mv vitamin.brokoli.F33.com/* .
  ```
- Kembali ke direktori /
  ```
  cd /
  ```
- Copy file 000-default.conf ke direktori sites-available dengan nama  vitamin.brokoli.F33.conf
  ```
  cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/vitamin.brokoli.F33.conf
  ```
- Mengedit file
  ```
  nano /etc/apache2/sites-available/vitamin.brokoli.F33.conf
  ```
- Isi konfigurasi pada file vitamin.brokoli.F33.conf
  ```
  <VirtualHost *:8080>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/vitamin.brokoli.F33
    ServerName vitamin.brokoli.F33.com
    ServerAlias www.vitamin.brokoli.F33.com

   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
  </VirtualHost>
  ```
- Mengaktifkan virtual host tersebut dengan menggunakan perintah:
  ```
  a2ensite vitamin.brokoli.F33.conf
  ```
- hapus default
  rm /etc/apache2/sites-available/000-default.conf
- Lakukan restart apache2
  ```
  service apache2 restart
  ```

#### Testing
  - Lakukan testing pada client yang nameservernya wortel dan pokcoy
  ```
  lynx vitamin.brokoli.F33.com:8080/nutrisi
  lynx vitamin.brokoli.F33.com:8080/public
  lynx www.vitamin.brokoli.F33.com:8080/secret
  ```

<br>

## Soal 13

> Pada subdomain vitamin.brokoli.yyy.com, terdapat subfolder /nutrisi yang menyediakan informasi tentang berbagai vitamin dalam brokoli, seperti Vitamin A, C, dan K. Aktifkan directory listing untuk folder /nutrisi, dan buatlah rewrite rule di Apache untuk memperbaiki URL agar halaman seperti www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php dapat diakses hanya dengan www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Pastikan setiap halaman vitamin dapat diakses langsung melalui url yang telah disederhanakan.

> _On the vitamin.brokoli.yyy.com subdomain, there is a /nutrisi subfolder that provides information about various vitamins in brokoli, such as Vitamin A, C, and K. Activate directory listing for the /nutrisi folder, and create a rewrite rule in Apache to fix the URL so that pages like www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a.php can be accessed only with www.vitamin.brokoli.yyy.com/nutrisi/vitamin_a. Make sure each vitamin page can be accessed directly through the simplified url._

**Answer:**

- Screenshot

- Vitamin A dalam brokoli
  ![image](https://github.com/user-attachments/assets/2adb5d59-d496-44c8-b38c-672f1d091de0)
- Vitamin C dalam brokoli
  ![image](https://github.com/user-attachments/assets/1061f219-7e41-4298-a7f2-2741e7d2678d)
- Vitamin K dalam brokoli
  ![image](https://github.com/user-attachments/assets/d1fa2940-bfcc-4c25-9c30-496c8ace12a6)

- Explanation

#### Brokoli WebServer

- Menambahkan option +Indexes agar bisa generate listing pada file vitamin.brokoli.F33.conf
  ```
  nano /etc/apache2/sites-available/vitamin.brokoli.F33.conf
  ``` 
- Isi konfigurasi pada vitamin.brokoli.F33.conf seperti dibawah ini
  ```
	 <VirtualHost *:8080>
	        
	          ServerAdmin webmaster@localhost
	          DocumentRoot /var/www/vitamin.brokoli.F33
	          ServerName vitamin.brokoli.F33.com
	          ServerAlias www.vitamin.brokoli.F33.com
	
	<Directory /var/www/vitamin.brokoli.F33/nutrisi>
	Options Indexes FollowSymLinks
	AllowOverride All
	</Directory>
	         
	          ErrorLog ${APACHE_LOG_DIR}/error.log
	          CustomLog ${APACHE_LOG_DIR}/access.log combined
	</VirtualHost>
  ```
- Agar URL seperti www.vitamin.brokoli.F33.com/nutrisi/vitamin_a.php bisa diakses melalui www.vitamin.brokoli.F33.com/nutrisi/vitamin_a, kita akan menggunakan modul mod_rewrite di Apache. Lakuka perintah
  ```
  a2enmod rewrite
  ```
- Membuat file .htaccess 
  ```
  nano /var/www/vitamin.brokoli.F33/nutrisi/.htaccess
  ```
- Isi seperti dibawah
  - RewriteEngine On = untuk flag bahwa menggunakan module rewrite
  - RewriteRule adalah parameter input yang akan dicari oleh webserver
  ```
  RewriteEngine On
  RewriteRule ^vitamin_a$ vitamin_a.php [L]
  RewriteRule ^vitamin_c$ vitamin_c.php [L]
  RewriteRule ^vitamin_k$ vitamin_k.php [L]
  ```
- Lakukan restart apache2
  ```
  service apache2 restart
  ```

#### Testing
- Lakukan Testing pada client
  ```
  lynx www.vitamin.brokoli.F33.com:8080/nutrisi/vitamin_a
  lynx www.vitamin.brokoli.F33.com:8080/nutrisi/vitamin_c
  lynx www.vitamin.brokoli.F33.com:8080/nutrisi/vitamin_k
  ```
  
<br>

## Soal 14

> Tambahkan alias untuk folder /public/images/ pada subdomain www.vitamin.brokoli.yyy.com agar folder tersebut dapat diakses langsung melalui url www.vitamin.brokoli.yyy.com/img.

> _Add an alias for the /public/images/ folder on the www.vitamin.brokoli.yyy.com subdomain so that the folder can be accessed directly through the url www.vitamin.brokoli.yyy.com/img._

**Answer:**

- Screenshot

  ![Screenshot 2024-10-08 155219](https://github.com/user-attachments/assets/2000eaea-cd4b-413e-ad20-196daa4ee88a)


- Explanation

  #### Buka BrokoliWebServer
  - Buka file /etc/apache2/sites-available/vitamin.brokoli.F33.conf
    ```
    nano /etc/apache2/sites-available/vitamin.brokoli.F33.conf
    ```
  - Tambahkan konfigurasi seperti dibawah ini pada file vitamin.brokoli.F33.conf 
    ```
    <Directory /var/www/vitamin.brokoli.F33/public/images>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
    </Directory>
    Alias "/img" "/var/www/vitamin.brokoli.F33/public/images"
    ```
  - Alias untuk folder images
    Alias /img /var/www/vitamin.brokoli.yyy.com/public/images
  - Lakukan restart apache
    ```
    service apache2 restart
    ```
  #### Testing
  - Lakukan testing pada client untuk mengakses
    ```
    lynx www.vitamin.brokoli.F33.com:8080/img
    ```

<br>

## Soal 15

> Karena terdapat resep rahasia di file /secret/recipe_secret.txt pada subdomain www.vitamin.brokoli.yyy.com, konfigurasikan folder /secret agar tidak dapat diakses oleh pengguna (dengan menampilkan 403 Forbidden).

> _Because there is a secret recipe in the /secret/recipe_secret.txt file on the www.vitamin.brokoli.yyy.com subdomain, configure the /secret folder so that it cannot be accessed by users (by displaying 403 Forbidden)._

**Answer:**

- Screenshot

  ![Screenshot 2024-10-08 160454](https://github.com/user-attachments/assets/dd4f2c45-cc45-4b5f-a9cf-bb144b75f0dc)


- Explanation

  #### Buka BrokoliWebServer
  - Buka file /etc/apache2/sites-enabled/vitamin.brokoli.F33.conf
    ```
    nano /etc/apache2/sites-enabled/vitamin.brokoli.F33.conf
    ```
  - Tambahkan Konfigurasi seperti dibawah ini pada file vitamin.brokoli.F33
    ```
    <Directory /var/www/vitamin.brokoli.F33/secret>
        Options -Indexes
    </Directory>
    Alias "/secret/recipe_secret.txt" "/var/www/vitamin.brokoli.F33/secret"
    ```
  - Lakukan restart apache
    ```
    service apache2 restart
    ```

  #### Testing
  - Lakukan testing pada client untuk mengakses
    ```
    lynx www.vitamin.brokoli.F33.com:8080/secret/recipe_secret.txt
    ```

<br>

## Soal 16

> Karena dinilai terlalu panjang coba ubah konfigurasi www.vitamin.brokoli.yyy.com/public/js menjadi www.vitamin.brokoli.yyy.com/js

> _Since it is considered too long, change the configuration from www.vitamin.brokoli.yyy.com/public/js to www.vitamin.brokoli.yyy.com/js._

**Answer:**

- Screenshot

  ![Screenshot 2024-10-08 161517](https://github.com/user-attachments/assets/b1f33e9c-cf2c-449a-908f-2a63dc86e8b6)


- Explanation

  #### Buka BrokoliWebServer
  - Buka file /etc/apache2/sites-enabled/vitamin.brokoli.F33.conf
    ```
    nano /etc/apache2/sites-enabled/vitamin.brokoli.F33.conf
    ```
  - Tambahkann konfigurasi seperti dibawah ini pada file vitamin.brokoli.F33.conf
    ```
    <Directory /var/www/vitamin.brokoli.F33/public/js>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
    </Directory>
    Alias "/js" "/var/www/vitamin.brokoli.F33/public/js"
    ```
  - Lakukan restart apache
    ```
    service apache2 restart
    ```

  #### Testing
  - Lakukan testing pada client untuk mengakses
    ```
    lynx www.vitamin.brokoli.F33.com:8080/js
    ```

<br>

## Soal 17

> Supaya Web kita aman terkendali maka ubah konfigurasi www.k1.vitamin.brokoli.yyy.com menjadi hanya bisa di akses oleh port 9696 dan 8888

> _To keep our web secure, configure www.k1.vitamin.brokoli.yyy.com to only be accessible through ports 9696 and 8888._

**Answer:**

- Screenshot

- Isi ketika lynx www.k1.vitamin.brokoli.F33.com pada ports 9696 
![Screenshot 2024-10-08 163956](https://github.com/user-attachments/assets/8383903d-aa5d-46c1-bad8-8640d9a9dc17)

- Isi ketika lynx www.k1.vitamin.brokoli.F33.com pada ports 8888
![Screenshot 2024-10-08 164051](https://github.com/user-attachments/assets/763f8e30-82be-401b-9802-0619512872aa)

- Isi ketika lynx www.k1.vitamin.brokoli.F33.com pada ports 8080
![Screenshot 2024-10-08 164140](https://github.com/user-attachments/assets/c4c72c0e-1bd5-49d0-b77c-011cb81de04a)

- Explanation

  - Download folder zip yang bernama k1.vitamin.brokoli.yyy.com
    ```
    wget -O /var/www/k1.vitamin.brokoli.yyy.com.zip "https://docs.google.com/uc?export=download&id=1SRnelY4XrtmhJg_Ly1nUJo1Jf91SnmtB"
    ```
  - masuk ke direktori `/var/www`
  - unzip file yang terunduh
    ```
    unzip -o k1.vitamin.brokoli.yyy.com.zip
    ```
  - ganti nama file yang telah diunzip, ubah menjadi nama dari document root
    ```
    mv k1.vitamin.brokoli.yyy.com k1.vitamin.brokoli.F33
    ```
  - Buat file conf untuk k1.vitamin.brokoli.F33.com
    ```
    nano /etc/apache2/sites-available/k1.vitamin.brokoli.F33.com.conf
    ```
  - Isi konfigurasi seperti dibawah ini pada file k1.vitamin.brokoli.F33.com.conf
    ```
    <VirtualHost *:9696 *:8888>
     ServerAdmin webmaster@localhost
     DocumentRoot /var/www/k1.vitamin.brokoli.F33
     ServerName k1.vitamin.brokoli.F33.com
     ServerAlias www.k1.vitamin.brokoli.F33.com

    <Directory /var/www/k1.vitamin.F33>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
    ```
  - Buka file /etc/apache2/ports.conf
    ```
    nano /etc/apache2/ports.conf
    ```
  - Tambahkan konfigurasi seperti dibawah ini pada file ports.conf dibawah Listen 8080
    ```
    Listen 9696
    Listen 8888
    ```
  - Setelah mengisi konfigurasi pada file ports.conf dan menyimpannya, maka lakukan seperti dibawah ini pada BrokoliWebServer
    ```
    a2dissite vitamin.brokoli.F33.conf
    ```
    ```
    a2ensite k1.vitamin.brokoli.F33.com.conf
    ```
  - Lakukan restart apache
    ```
    service apache2 restart
    ```

  #### Testing
  - Lakukan testing pada client untuk mengakses
    ```
    lynx www.k1.vitamin.brokoli.F33.com:9696
    ```
    ```
    lynx www.k1.vitamin.brokoli.F33.com:8888
    ```
  - Untuk membuktikan hanya bisa lynx pada ports 9696 dan 8888, lakukan lynx pada port yang lain seperti port 8080
    ```
    lynx www.k1.vitamin.brokoli.F33.com:8080
    ```

<br>

## Soal 18

> Lanjutkan dari nomor sebelumnya buatlah autentikasi dengan username “Seblak” dan password “sehatyyy” dengan yyy adalah kode kelompok. Letakkan Document Root pada /var/www/k1.vitamin.brokoli.yyy.

> _Continuing from the previous point, create authentication with the username “Seblak” and the password “sehatyyy” where yyy is the group code. Set the Document Root to /var/www/k1.vitamin.brokoli.yyy._

**Answer:**

- Screenshot

  ![Screenshot 2024-10-08 171004](https://github.com/user-attachments/assets/0faeec9d-ce85-439a-8aa1-8f33171c73a2)


- Explanation

  #### Buka BrokoliWebServer
  - Buka file /etc/apache2/sites-available/k1.vitamin.brokoli.F33.com.conf
    ```
    nano /etc/apache2/sites-available/k1.vitamin.brokoli.F33.com.conf
    ```
  - Tambahkan konfigurasi seperti dibawah pada file k1.vitamin.brokoli.F33.com.conf
    ```
    <Directory /var/www/k1.vitamin.F33>
          AuthType Basic
          AuthName "Restricted Content"
          AuthUserFile /etc/apache2/.htpasswd
          Require valid-user
    </Directory>
    ```
  - Kembali ke bash
    ```
    cd /
    ```
  - Di bash, ketik seperti dibawah ini untuk menambahkan password pada username "Seblak"
    ```
    htpasswd -c /etc/apache2/.htpasswd Seblak
    ```
  - Passwordnya adalah
    ```
    sehatF33
    ```
  - ```
    service apache2 restart
    ```

  #### Testing
  - Lakukan testing pada client untuk mengakses 
    ```
    lynx www.k1.vitamin.brokoli.F33.com:8888
    ```

<br>

## Soal 19

> Konfigurasikan agar setiap kali IP Brokoli diakses dengan lynx, secara otomatis akan dialihkan ke www.brokoli.yyy.com (alias).

> _Configure it so that every time Brokoli's IP is accessed using lynx, it is automatically redirected to www.brokoli.yyy.com (alias)._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/9714a1fa-50d2-4405-967b-a9fa7da49f96)


- Explanation

  #### Buka BrokoliWebServer
  - ```
    service apache2 stop
    ```
  - ```
    service nginx start
    ```
  - Buka file /etc/nginx/sites-available/sayur_webserver_nginx
    ```
    nano /etc/nginx/sites-available/sayur_webserver_nginx
    ```
  - Isi konfigurasi pada file sayur_webserver_nginx seperti dibawah
    ```
	server {
	    listen 80;
	    server_name 10.83.4.2; # IP brokoli
	
	    #redirect semua permintaan ke www.brokoli.yyy.com
	    location / {
	    return 301 http://www.brokoli.F33.com$request_uri;
	    }
	}

	server {
	        listen 80;
	        server_name www.brokoli.F33.com;
	
	        root /var/www/sayur_webserver_nginx;
	
	        index index.php index.html index.htm;
	
	        location / {
	                try_files $uri $uri/ /index.php?$query_string;
        	}

        	# pass PHP scripts to FastCGI server
    		location ~ \.php$ {
                	include snippets/fastcgi-php.conf;
                	fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
		}
		
  		location ~ /\.ht {
        		deny all;
		}

		error_log /var/log/nginx/error.log;
		access_log /var/log/nginx/access.log custom_log;
	}
    ```
  - ```
    service nginx restart
    ```
  - testing di tomat client
    ```
    lynx 10.83.4.2
    ```

<br>

## Soal 20

> Karena jumlah pengunjung website www.vitamin.brokoli.yyy.com semakin meningkat dan terdapat banyak gambar random, ubah permintaan gambar yang mengandung substring "vitamin" agar diarahkan ke file vitamin.png.

> _Since the number of visitors to www.vitamin.brokoli.yyy.com is increasing and there are many random images, redirect image requests that contain the substring "vitamin" to the file vitamin.png._

**Answer:**

- Screenshot

  ![image](https://github.com/user-attachments/assets/6c20c36c-a555-4988-a470-3b5d13dadc3e)


- Explanation

   #### Buka BrokoliWebServer
  - ```
    service nginx stop
    ```
  - ```
    service apache2 start
    ```
  - Buka file /etc/apache2/sites-available/vitamin.brokoli.F33.conf
    ```
    nano /etc/apache2/sites-available/vitamin.brokoli.F33.conf
    ```
  - Pada file vitamin.brokoli.F33.conf tambahkan:
    ```
	<Directory /var/www/vitamin.brokoli.F33>
	    RewriteEngine On
	    RewriteCond %{REQUEST_URI} \.(jpg|png)$ [NC]
	    RewriteCond %{REQUEST_URI} vitamin [NC]
	    RewriteCond %{REQUEST_URI} !^/public/images/vitamin\.png [NC]
	    RewriteRule ^(.*)$ http://www.vitamin.brokoli.F33.com/public/images/vitamin.png [L,R=301]
	</Directory>
    ```
  - Lakukan
    ```
    a2dissite 000-default.conf
    ```
    ```
    a2ensite vitamin.brokoli.F33.conf
    ```
    ```
    a2enmod rewrite
    ```
  - Lakukan restart apache
    ```
    service apache2 restart
    ```

  #### Testing
  - Lakukan testing pada client. Cara akses, lynx dengan string apapun yang ada kata vitaminnya
    ```
    lynx vitamin.brokoli.F33.com/vitamin.png
    ```
  - tidak akan muncul apa apa, karena tidak ada file bernama vitamin.png
<br>
  
## Problems
- kurangnya durasi praktikum
- banyaknya tugas matkul lain
- yang membuat stuck di salah satu soal adalah karena tidak tahu errornya dimana
- mohon maaf karena lupa meng-export project file dan lupa upload di github sebelum tenggat

## Revisions (if any)
- revisi laporan selesai hari kamis, 10 oktober 2024
