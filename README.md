# ecommerce-documentation

# API Documentation: Jual Beli Barang Bekas

## Pendahuluan
- Back-end ini mendukung proses bisnis jual beli barang bekas. 
- Sistem mendukung autentikasi JWT.
- Semua data yang dibuat akan tersimpan di database MongoDB dan akan mendapatkan ID yang unik.
- Bahasa yang digunakan adalah Javascript menggunakan NodeJS dan Framework yang digunakan adalah express.js

## Package yang digunakan : 
- bcryptjs
- dotenv
- express
- express-jwt
- jsonwebtoken
- mongodb
- mongoose
- nodemon

---

## Endpoints
### Users
- POST /users/
- POST /users/login
- GET /users/
- GET /users/:id
- DELETE /users/:id

### Products
- GET /products/
- GET /products/:id
- POST /products/
- PUT /products/:id
- DELETE /products/:id


## Detail Endpoint

## USERS


### 1. POST /users/register
**Description:** Mendaftarkan pengguna baru.

**Headers:** Tidak ada.

**Request Body:** Data user dengan format JSON

**Response :** Data akan disimpan di database MongoDB dan mengembalikan data user dalam format JSON di Response Body

  
### 2. POST /users/login
**Description:** 
User dapat login dan akan mendapatkan authentication token. Di mana token dapat digunakan untuk:
- Jika isAdmin false, akses terbatas pada mengakses produk yang ada
- Jika isAdmin true, maka user dapat mengakses semua endpoint

**Headers:** Tidak ada.

**Request Body:** Data dengan format JSON memuat email dan password user

**Response :** Pada response body: Mengembalikan data JSON berisi authentication token 

### 3. GET /users/
**Description:** 
Mengembalikan list semua data user. Hanya dapat diakses admin

**Headers:** Authentication token.

**Request Body:**
tidak ada

**Response :** Pada response body: mengembalikan array yang berisi semua product dalam format JSON


### 4. GET /users/:id
**Description:** 
Mengembalikan data user berdasarkan ID. Hanya dapat diakses oleh admin

**Headers:** Authentication token.

**Request Body:**
tidak ada

**Response :** Pada response body: Mengembalikan data user dalam format JSON


### 5. DELETE /users/:id
**Description:** 
Menghapus sebuah user berdasarkan ID. Hanya dapat diakses oleh admin

**Headers:** Authentication token.

**Request Body:**
tidak ada

**Response :** Data user terhapus dari database. Pada response body: Mengembalikan pesan berhasil dengan format JSON

## PRODUCTS

### 1. GET /products/
**Description:** 
Mengembalikan list semua produk yang dijual. Dapat diakses tanpa login

**Headers:** tidak ada.

**Request Body:**
tidak ada

**Response :** Pada response body: Mengembalikan array yang berisi semua produk yang dijual


### 2. GET /products/:id
**Description:** 
Mengembalikan data produk yang dijual berdasarkan id. Dapat diakses tanpa login

**Headers:** tidak ada.

**Request Body:**
tidak ada

**Response :** Pada response body: Mengembalikan data produk yang diminta berdasarkan ID


### 3. POST /products/
**Description:** 
Menambahkan produk yang akan dijual. Hanya dapat diakses admin

**Headers:** 
Authentication token

**Request Body:** Product dalam format JSON

**Response :** Product tersimpan di database. Pada response body: Mengembalikan data produk yang baru ditambahkan

### 4. PUT /products/:id
**Description:** 
mengubah data produk berdasarkan id. Hanya dapat diakses admin

**Headers:** 
Authentication token

**Request Body:** Data product baru dalam format JSON

**Response :** Data produk akan diubah dengan data baru. Pada response body: Mengembalikan produk yang baru diubah

### 5. DELETE /products/:id
**Description:** 
Menghapus produk berdasarkan id. Hanya dapat diakses oleh admin

**Headers:** 
Authentication token

**Request Body:** Tidak ada

**Response :** Product akan dihapus dari database. Pada response body: Mengambalikan pesan berhasil dalam format JSON
Success: Data produk akan dihapus dari database. Mengembalikan pesan berhasil
