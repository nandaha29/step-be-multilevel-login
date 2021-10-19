# step-be-multilevel-login

### Step By Step Node-multilevel-login

- siapkan folder project "node-multilevel-auth"

- inisiasi npm -> $ npm init --y

- install "nodemon" --> $ npm install nodemon

- config nodemon --> di file package.json
	+ "start": "nodemon server.js" (dalam script)

### Install library "sequelize"

- install global sequelize-cli -> $ npm install -g sequelize-cli

- install sequelize, mysql2, express, multer (lokal) -> $ npm install sequelize mysql2 express express-jwt multer cors

- install jsonwebtoken tuk proses auth -> $ npm install jsonwebtoken

- install library MD5 tuk (hashing) tuk password spy aman -> npm install md5

-  `allow permission di git bash (jika perlu) -> $ Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted`

- inisiasi sequelize -> $ sequelize init

- buat folder "router" dan file dengan nama "server.js"

- buat database "node-multilevel-auth" di PhpMyAdmin

- set configurasi database -> config\config.js
	+ "database": "node-multilevel-auth",

### Mulai membuat table database

- kita buat migration "user"-> $ sequelize model:create --name user --attributes username:string,email:string,password:string,role:string

- perbaiki nama table, primary key, dan relasinya pada file folder "migrations"

- kita eksekusi migrate untuk create struktur tabel -> $ sequelize db:migrate

- `jika mengalami error "mysql2 install manuall" run command -> $ npm install -g mysql2`

### Setting file on folder "api"

- buat folder "api" -> buat tempat folder per table yg didalamnya terdapat logic MVC tuk node

- alur edit migrate -> models -> folder api -> folder tabel yg -> router -> controller 

- buat script relation pada file folder "models"

subjek bab @produktif "Bab Kardinalitas"
```
     static associate(models) {
      // ini adalah blok untuk menghubungkan antar model/table
      /** one to one -> hasOne(), belongsTo()
       *  one to many-> hasMany(), belongsToMany()
       * 
       * has -> itu dipakai ketika menghubungkan parent ke child
       * belong -> itu dipakai ketika menghubungkan child ke parent
       */
	
	//Example relation'_'
       //menghubungkan transaksi -> customer
       this.belongsTo(models.customer,{
         foreignKey: "customer_id",
         as: "customer"
       })

       // menghubungkan transaksi -> detail_transaksi
       this.hasMany(models.detail_transaksi, {
         foreignKey: "transaksi_id", 
         as: "detail_transaksi"
       })
    }
```

- lanjutkan dengan menyusun endpoint di file "router"

- lanjutkan dengan menyusun logic case di file "controller"
 
- untuk menjalankan program ketik -> $ npm start 

- lakukan CRUD pada setiap Endpoint di setiap file memakai "postman"
  + Get -> menampilkan data 
  + Post -> masukkan data
  + Put -> update data 
  + Delete -> hapus data 

- jika berhasil selamat 

### NB: 
- desclimer ->  susunan Node versi bu Whyna:D
  + sequelize = sebuah library,  
  + migratory = folder membuat struktur tabel, 
  + models = folder tempat mengganti query, 
  + router = folder untuk tempat setting endpoint per tabel,
  + controller = file server tuk kumpulan logic case per tabel, 
  + express = 
  + cors = 
  + bodyparser = 



https://www.markdownguide.org/cheat-sheet/ -> mark readme
