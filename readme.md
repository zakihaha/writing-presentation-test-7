# Writing & Presentation Test Week 7
##### Muh Zaki Choiruddin 
##### Backend Web Development Track | Skilvul Tech4Impact

Assalamu'alaikum Wr. Wb. Di markdown ini saya akan menjelaskan berbagai materi yang telah saya pelajari selama mengikuti kegiatan `Kampus Merdeka Skilvul Tech4Impact pada track Backend Web Development`.

  - [Sequelize](#sequelize)
    - [Pengertian](#pengertian)
    - [ORM](#orm)
    - [Penggunaan](#penggunaan)
  - [MongoDB](#mongodb)
    - [Pengertian](#pengertian-1)
    - [NoSQL](#nosql)
    - [Kelebihan](#kelebihan)
    - [Kekurangan](#kekurangan)
    - [Komponen MongoDB](#komponen-mongodb)
  - [Mongoose](#mongoose)
    - [Pengertian](#pengertian-2)
    - [Penggunaan](#penggunaan-1)
  - [Docker](#docker)
    - [Pengertian](#pengertian-3)
    - [Alasan Menggunakan Docker](#alasan-menggunakan-docker)
    - [Fungsi](#fungsi)

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


## MongoDB
### Pengertian
MongoDB adalah open-source database yang menggunakan document-oriented data model dan non-structured query language. Database ini cukup canggih. Bahkan, ia dikatakan sebagai salah satu sistem dan database NoSQL (Not only SQL) yang paling mutakhir saat ini. Karena kapasitasnya, MongoDB dapat digunakan untuk menyimpan volume data yang besar. MongoDB sering dipakai untuk aplikasi berbasis Cloud, Big Data maupun Grid Computing.

### NoSQL
NoSQL adalah singkatan dari Not Only SQL. Database management system ini bersifat tanpa relasi (non-relational). Artinya, NoSQL bisa mengelola database dengan skema yang fleksibel dan tidak membutuhkan query yang kompleks. Dengan pendekatan ini, NoSQL mempunyai skalabilitas tinggi untuk dapat berkembang sesuai dengan kebutuhan data yang ada. Tak heran, database management ini dianggap paling cocok untuk mengolah big data yang selalu berubah-ubah sekalipun.

### Kelebihan
- Sistem tidak membutuhkan Tabel
- Tidak perlu menggunakan Tabel yang terstruktur
- By Default sudah menggunakan JSON(JavaScript Object Notation), sehingga memudahkan integrasi dengan JavaScript
- Performa lebih cepat dengan kemampuan menampung banyak data yang bervariasi

### Kekurangan
- Tidak mendukung transaksi
- Masalah konsistensi data
- Menggunakan banyak memory
- Hanya bisa menampung maksimal 16MB disetiap document

### Komponen MongoDB
#### Database
Database adalah wadah untuk menyimpan berbagai macam Collection

#### Collection
Collection adalah tempat kumpulan dari berbagai macam document, sehingga collection sering disamakan dengan tabel pada SQL

#### Document
Document adalah unit terkecil yang berada pada MongoDB.


## Mongoose
### Pengertian
Mongoose adalah library Object Modelling MongoDB untuk NodeJS. Mongoose bisa digunakan untuk mengelola hubungan antara data, menyediakan validasi dan juga digunakan untuk menerjemahkan antara objek dalam kode dan representasi Objek tersebut di MongoDB.

### Penggunaan
- Install dengan npm
```sh
npm install mongoose
```

- Membuat koneksi
```sh
const mongoose = require('mongoose');

main().catch(err => console.log(err));

async function main() {
  await mongoose.connect('mongodb://localhost:27017/test');
  
  // use `await mongoose.connect('mongodb://user:password@localhost:27017/test');` if your database has auth enabled
}
```

- Mendefinisikan schema untuk model
```sh
const mongoose = require('mongoose')
const { Schema, model } = mongoose

const userSchema = new Schema(
    {
        name: String,
        age: Number,
        email: String,
        password: String
    },
    { timestamps: true }
)

const User = mongoose.model('User', userSchema)
```

## Docker
### Pengertian
Docker adalah aplikasi untuk menyatukan berbagai file software dan pendukungnya dalam sebuah wadah (container) agar memudahkan proses pengembangan software.

### Alasan Menggunakan Docker
Dalam pengembangan aplikasi, developer memerlukan virtualisasi di server agar aplikasi bisa berjalan di berbagai platform dengan konfigurasi hardware yang berbeda-beda. Sayangnya, ketika menggunakan virtualisasi, Anda harus menyiapkan satu sistem operasi secara penuh. Jika membutuhkan beberapa virtualisasi, server perlu resource yang besar. Nah, container bisa digunakan sebagai alternatif virtualisasi sehingga tidak perlu menyiapkan sistem operasi secara penuh. Dengan container, ukuran file menjadi lebih kecil dibandingkan virtualisasi yang biasa digunakan.

### Fungsi
- Mempermudah Pengembangan Aplikasi
Docker bisa mempermudah pekerjaan developer ketika mengembangkan aplikasi. Alasannya, Docker lebih hemat resource dan mampu menyediakan environment yang stabil untuk dijalankan di perangkat apapun
- Menyederhanakan Konfigurasi
Docker tidak memiliki overhead sehingga developer bisa menjalankan aplikasi yang diuji tanpa konfigurasi tambahan.
- Memudahkan Pengembangan Kode Pipeline
Developer bisa memanfaatkan Docker container sebagai tempat pengujian kode Pipeline beserta tools yang diperlukan dengan lebih mudah.
- Bisa Digunakan untuk Debugging
Adanya fitur debug bisa membantu developer untuk mengatasi masalah pada aplikasi tanpa perlu bersusah payah meninggalkan environment di Docker.
- Mendukung Multitenancy
Docker cocok digunakan untuk membuat aplikasi berstruktur multitenance seperti Software as a Service (SaaS). Dcoker bisa membuat lebih dari satu environment yang terisolasi dan menjalankan objek aplikasi untuk setiap tenant.
- Meningkatkan Sumber Daya dengan Cepat
Dengan Docker, peningkatan sumber daya perangkat dapat dilakukan dengan cepat sehingga durasi pengembangan software  lebih singkat.

