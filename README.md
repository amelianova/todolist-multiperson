# todolist-multiperson

| Name           | NRP        | 
| ---            | ---        | 
| Amelia Nova Safitri | 5025231041 | 
| Tarisha Falah Basuki | 5025231043 |
| Putriani Pirma A. Sagala | 5025231045 | 

## 1. Ringkasan Singkat

- Final Project untuk mata kuliah “Pemrograman Website” adalah mengimplementasikan ilmu yang didapat dari mata kuliah ini untuk membuat sebuah web. Dari beberapa topik yang diusung, kelompok kami memilih topik “Multiperson To Do List”. 

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

- Main page
  ![Screenshot 2024-12-16 222339](https://github.com/user-attachments/assets/6064a0c9-f219-40bd-aff6-1ed26c5fbb5a)

- User dapat membuat Group terlebih dahulu
  ![Screenshot 2024-12-16 222429](https://github.com/user-attachments/assets/89767113-b33b-4bac-8749-7ab72d05bedb)

- Pengguna dapat memilih Group terlebih dahulu sebelum menambahkan Person
  ![Screenshot 2024-12-16 222527](https://github.com/user-attachments/assets/a9a40882-bc82-4f8f-b25c-8b1ff97be9dc)

- Tersedia fitur “Edit Group Name” dan “Delete Group”. Fungsi sudah berjalan sebagaimana mestinya

- Tersedia fitur “Add Person”, berfungsi menginputkan nama Person pada Group yang telah dibuat sebelumnya. Group harus dipilih terlebih dahulu pada fitur “Select Group” agar nama Person dapat ditambahkan.
  ![Screenshot 2024-12-16 223102](https://github.com/user-attachments/assets/bbeb288b-166c-4ba5-8a1d-1e7cf820e57a)

- Tersedia fitur “Edit” dan “Delete” pada setiap container Person
  ![Screenshot 2024-12-16 223923](https://github.com/user-attachments/assets/337205a6-098c-450f-9279-dad5c109897e)

- Pada Person tersedia fitur “Add a Task”, dapat menginputkan nama Task dan tanggal batas pengerjaan (due date). Jika due date sudah lewat, maka font Task akan berwarna merah. Setiap Task memiliki fitur checklist (kiri) yang berfungsi sebagai penanda bahwa Task tersebut telah selesai,  favorite (kanan) berfungsi sebagai penanda bahwa Task tersebut penting dan akan berada di baris teratas, dan tong sampah (kanan) berfungsi untuk menghapus Task tersebut. Task yang telah selesai dapat ditandai sebagai selesai atau dihapus.
  ![Screenshot 2024-12-16 223230](https://github.com/user-attachments/assets/aaf8d7c9-da2e-483f-bcbf-7557baebf673)
  ![Screenshot 2024-12-16 223636](https://github.com/user-attachments/assets/6fbebfbf-8864-49c0-87dd-5f4b740d043d)
  ![Screenshot 2024-12-16 223718](https://github.com/user-attachments/assets/79a90f30-f58c-4883-b795-fa53491756c2)


- Pada “Add a Task” terdapat fitur “Add task to all persons in the group”, berfungsi untuk menambahkan task dengan nama dan due date yang sama ke semua Person pada Group yang sama.
  ![Screenshot 2024-12-16 224447](https://github.com/user-attachments/assets/4f84f9e6-9cce-4c06-8b1d-60032d0e9e7a)

- Fitur terakhir yaitu “Logout” untuk keluar dari halaman todo list dan kembali ke halaman utama

### Database

- Database yang digunakan untuk menyimpan/mencatat semua riwayat activity pada website todo list adalah mongodb. Kode pada VSCode dihubungkan dengan mongodb Compass dan Atlas
  ![Screenshot 2024-12-16 225406](https://github.com/user-attachments/assets/f88df684-8dbc-4caf-8c33-674699efc249)
  ![Screenshot 2024-12-16 225531](https://github.com/user-attachments/assets/8409e89d-0c79-405c-8b63-24b2e625d097)


### Antarmuka Responsif

- Aplikasi dirancang responsif sehingga dapat digunakan dengan nyaman di berbagai perangkat, termasuk desktop, tablet, dan smartphone.

## Instalasi

1. Clone source code pada direktori anda
2. Jika ingin menjalankan website pada localhost, buka terminal root direktori
3. Ketik `node index.js`
4. Tunggu hingga muncul tulisan
   `Server running on port 3000` dan `mongodb connected`
6. Buka `localhost:3000` pada browser Anda
7. Anda sudah terhubung pada website lokal
8. Apabila anda ingin melihat aktivitas yang tercatat dalam database, Anda bisa membuka link pada `mongodb.js` bagian mongoose.connect

## Deploy Website

1. Kali ini kami akan menggunakan https://vercel.com untuk membantu deployment website
2. Sign Up/Login pada akun vercel terlebih dahulu
3. Add new project
4. Import Git Repo (apabila Anda ingin menggunakan Repo ini, maka bisa fork dulu)
5. Tekan `Import` pada repository yang ingin dideploy
6. Beri Install Command dengan `npm install`
   ![image](https://github.com/user-attachments/assets/6bdb5d20-eda0-43d3-a830-a3153ef4b545)
7. Tekan `Deploy`

## Source Code dan Dokumentasi Postman

- https://github.com/amelianova/todolist-multiperson.git
- https://documenter.getpostman.com/view/40475331/2sAYJ1jhEu
