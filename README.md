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

## Database

- MongoDB: Digunakan untuk menyimpan data pengguna, daftar tugas, dan pengaturan kolaborasi.

## Framework

- Bootstrap: Untuk mempercantik dan mempermudah desain antarmuka yang responsif.
- Express js
- Node js

## Fitur-fitur dan Penjelasan Detail Fitur Aplikasi

- Halaman Utama
  ![Screenshot 2024-12-16 221856](https://github.com/user-attachments/assets/c0c78132-931d-4d4e-bde2-91e1589e1418)

### Manajemen Akun:
- Sign Up: Pengguna baru dapat mendaftar dengan memasukkan nama, email, dan password.
  ![Screenshot 2024-12-16 222009](https://github.com/user-attachments/assets/c8ad76e4-5dfa-408b-94dc-c401a57c6409)

- Login: Akses ke aplikasi menggunakan akun terdaftar
  ![Screenshot 2024-12-16 222048](https://github.com/user-attachments/assets/64ce4cbc-2898-464f-8b3d-76c4b14c2563)

### Pembuatan dan Pengelolaan Tugas:

- User dapat membuat Group terlebih dahulu
- Pengguna dapat memilih Group terlebih dahulu sebelum menambahkan Person
- Tersedia fitur “Edit Group Name” dan “Delete Group”. Fungsi sudah berjalan sebagaimana mestinya
- Tersedia fitur “Add Person”, berfungsi menginputkan nama Person pada Group yang telah dibuat sebelumnya. Group harus dipilih terlebih dahulu pada fitur “Select Group” agar nama Person dapat ditambahkan.
- Tersedia fitur “Edit” dan “Delete” pada setiap container Person
- Pada Person tersedia fitur “Add a Task”, dapat menginputkan nama Task dan tanggal batas pengerjaan (due date). Jika due date sudah lewat, maka font Task akan berwarna merah. Setiap Task memiliki fitur checklist (kiri) yang berfungsi sebagai penanda bahwa Task tersebut telah selesai,  favorite (kanan) berfungsi sebagai penanda bahwa Task tersebut penting dan akan berada di baris teratas, dan tong sampah (kanan) berfungsi untuk menghapus Task tersebut. Task yang telah selesai dapat ditandai sebagai selesai atau dihapus.
- Pada “Add a Task” terdapat fitur “Add task to all persons in the group”, berfungsi untuk menambahkan task dengan nama dan due date yang sama ke semua Person pada Group yang sama.
- Fitur terakhir yaitu “Logout” untuk keluar dari halaman todo list dan kembali ke halaman utama

### Database

- Database yang digunakan untuk menyimpan/mencatat semua riwayat activity pada website todo list adalah mongodb. Kode pada VSCode dihubungkan dengan mongodb Compass dan Atlas

### Antarmuka Responsif

- Aplikasi dirancang responsif sehingga dapat digunakan dengan nyaman di berbagai perangkat, termasuk desktop, tablet, dan smartphone.

## Instalasi

## Source Code dan Dokumentasi Postman

- https://github.com/amelianova/todolist-multiperson.git
- https://documenter.getpostman.com/view/40475331/2sAYJ1jhEu


