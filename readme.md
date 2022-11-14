# Writing & Presentation Test Week 7
##### Muh Zaki Choiruddin 
##### Backend Web Development Track | Skilvul Tech4Impact

Assalamu'alaikum Wr. Wb. Di markdown ini saya akan menjelaskan berbagai materi yang telah saya pelajari selama mengikuti kegiatan `Kampus Merdeka Skilvul Tech4Impact pada track Backend Web Development`.

- [Database MySQL Lanjutan]
- [Authentication & Authorization]
- [Sequelize]

## Database MySQL Lanjutan
### Pengertian
Database adalah kumpulan informasi yang disimpan didalam komputer secara sistematik dan saling berelasi. Database merupakan sekumpulan tabel yang berisikan informasi untuk diolah yang kemudian data tersebut bisa digunakan di dalam sebuah sistem. 

### Relasi di MySQL
#### One to Many
Paling Sering Digunakan dan Satu baris dalam tabel dapat memiliki beberapa baris di table relasinya

#### Many to Many
Digunakan ketika kedua tabel yang berelasi dapat memiliki beberapa baris di tabel relasinya.

#### One to One
Diimplementasikan dengan cara yang sama seperti One to Many tetapi dengan kondisi tambahan (foreign key merupakan primary key)

### Database Normalization
Database Normalization merupakan teknik analisis data yang mengorganisasikan atribut-atribut data dengan cara mengelompokkan sehingga terbentuk entitas yang non-redundant, stabil, dan fleksible. Tujuannya adalah:
- Menghilangkan redundan data pada database.
- Memudahkan juka ada perubahan struktur table database.
- Memperkecil pengaruh jika ada perubahan dari struktur table database.

### Macam - Macam Key
- Candidate Key
Kumpulan satu atau lebih fields/columns yang dapat mengidentifikasi record secara unik dalam tabel. Setiap Candidate Key bisa digunakan sebagai Primary Key. Bisa jadi ada beberapa Candidate Keys di dalam satu tabel.

- Primary Key
Kumpulan satu atau lebih fields/columns dari sebuah tabel yang secara unik mengidentifikasi sebuah record dalam tabel database. Valuenya tidak boleh berupa null ataupun duplicate value. Hanya boleh salah satu Candidate Key yang bisa menjadi Primary Key.

- Alternate Key
key yang bisa digunakan menjadi primary key. Pada dasarnya, Key ini merupakan candidate key yang tidak dijadikan  primary key.

- Unique Key
Kumpulan dari satu atau lebih fields/columns di sebuah table database yang secara unik mengidentifikasi sebuah record dalam table database tersebut. Hampir sama dengan Primary key, namun value dari Unique Key bisa berupa satu buah null value di dalam sebuah table database, dan Unique Key tidak bisa memiliki duplicate values

- Foreign Key
Field di sebuah table database yang menjadi Primary Key di table database lain. Value dari Foreign key bisa menerima multiple null dan duplicate values.


## Authentication & Authorization
### Authentication
Authentication digunakan untuk memverifikasi siapa Anda. Misalnya, katakanlah Anda pergi ke konser. Di pintu depan, penjaga keamanan meminta untuk melihat tiket dan ID Anda untuk memverifikasi bahwa nama di ID Anda cocok dengan nama di tiket Anda.

#### Faktor
- Sesuatu yang Anda ketahui, seperti nama pengguna dan kata sandi.
- Kepemilikan, seperti kartu keamanan atau perangkat seluler
- Inheren adalah sesuatu tentang Anda, yang umumnya mengacu pada data biometrik seperti sidik jari.

### Authorization
Authorization adalah verifikasi atas apa yang boleh Anda lakukan. Kembali ke contoh konser, setelah penjaga keamanan mengautentikasi Anda, Anda kemudian memberikan tiket Anda ke penjaga keamanan lain yang kemudian hanya mengizinkan Anda masuk ke Penerimaan Umum (bukan bagian VIP). Authorization sangat penting untuk keamanan web, dan bertanggung jawab atas segala hal mulai dari mencegah pengguna memodifikasi akun satu sama lain, melindungi aset back-end dari penyerang, hingga memberikan akses terbatas ke layanan eksternal.

### Token Based Authentication using JWT
JSON Web Token, yang berarti token ini menggunakan JSON (Javascript Object Notation) berbentuk string panjang yang sangat random, lalu token ini memungkinkan kita untuk mengirimkan data yang dapat diverifikasi oleh dua pihak atau lebih.

#### Cara Kerja
Ketika users berhasil melakukan Login maka server akan memberikan sebuah Token. Nanti Token tersebut akan disimpan oleh users pada Local Storage atau Cookies Browser dan bila users ingin mengakses halaman halaman tertentu maka harus menyertakan token tersebut. Untuk itu users akan mengirim balik token yang dikasih diawal tadi sebagai bukti bila user ini, sudah melakukan login. Sekarang kita akan lihat struktur dasarnya Tokennya dimana terdiri dari tiga bagian yaitu yang pertama header lalu kedua bagian payloadnya atau datanya dan yang ketiga adalah bagian verify signature.

#### Komponen
- Header
Header biasanya terdiri dari dua bagian: jenis token, yaitu JWT, dan algoritma penandatanganan yang digunakan, seperti HMAC SHA256 atau RSA.
```sh
{
  "alg": "HS256",
  "typ": "JWT"
}
```

- Payload
Infomasi atau data yang ingin kita kirimkan. Dalam penerapannya di otentikasi atau pun otorisasi, biasanya data ini berupa data yang sifatnya unik bagi user, seperti: email, id.
```sh
{
  "id": "4",
  "name": "Zaki",
  "address": "Klaten"
}
```

- Signature
Signature adalah hasil dari Hash atau gabungan dari isi encode Header dan Payloadnya lalu ditambahkan kode secretnya. Signature ini berguna untuk memverifikasi bahwa header maupun payload yang ada dalam token. Signature-nya sendiri tidak mungkin dapat diakali, karena sudah dalam berbentuk hash satu arah.

Dan hasil ketiga bagian tersebut akan digabung dan otomatis di encode menjadi Token string random panjang seperti berikut:
```sh
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

## Sequelize
### Pengertian
Sequelize adalah ORM (Object Relational Mapping) Node JS yang berbasis promise. Sequelize mendukung sebagian besar relational Database seperti MySQL, PostgresQL, MariaDB, SQLite dan Miscrosoft SQL Server. Dengan fitur fitur di Sequelize, kita bisa mengelola dan mengatur data di database kita dengan cepat, dan efisien.

### ORM
ORM adalah suatu metode/teknik pemrograman yang digunakan untuk mengkonversi data dari lingkungan bahasa pemrograman berorientasi objek (OOP) dengan lingkungan database relational.

### Penggunaan
1. Install sequelize cli
```sh
npm i -g sequelize-cli
```

2. Install sequelize dan driver mysql
```sh
npm i sequelize
npm i mysql2
```

3. Inisialisasi sequelize
```sh
npx sequelize-cli init
```

4. Masuk ke config/config.js, setting database
```sh
    "username": DB_USER,
    "password": DB_PASS,
    "database": DB_NAME,
    "host": DB_HOST,
    "dialect": "mysql"
```

5. Membuat model
```sh
npx sequelize-cli model:generate --name User --attributes name:string,address:text,age:integer
```

6. Migrate ke database
```sh
npx sequelize-cli db:migrate
```




