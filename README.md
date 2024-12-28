# ecommerce-documentation

# API Documentation: Jual Beli Barang Bekas

## Pendahuluan
Back-end ini mendukung proses bisnis jual beli barang bekas. 
Sistem mendukung autentikasi JWT.
Semua data yang dibuat akan tersimpan di database MongoDB dan akan mendapatkan ID yang unik.

Bahasa yang digunakan adalah Javascript dengan NodeJS
Framework yang digunakan adalah express.js
Package yang digunakan : 


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
-DELETE /products/:id


## Detail Endpoint

**USERS**


### 1. POST /users/
**Description:** Mendaftarkan pengguna baru.

**Headers:** Tidak ada.

**Request Body:**
JSON:
{
  "name": "<name>"
  "email": "<email>"
  "password": "<password>"
  "phone": "<phone>"
  "address": "<address>"
  "isAdmin": "<boolean>"
}

**Response :**
Created: user data will be saved in MongoDB
Response body:
{
  "name": "<name>"
  "email": "<email>"
  "passwordHash": "<passwordHash>"
  "phone": "<phone>"
  "address": "<address>"
  "isAdmin": "<boolean>"
}


Fail:
  'The user cannot be created'

  
### 2. POST /users/login
**Description:** 
User dapat login dan akan mendapatkan authentication token. Di mana token dapat digunakan untuk:
-Jika isAdmin false, akses terbatas pada method GET
-jika isAdmin true, maka user dapat mengakses semua endpoint

**Headers:** Tidak ada.

**Request Body:**
JSON:
{
  "email": "<email>"
  "password": "<password>"
}

**Response :**
Success: user will receive authentication token
Body:
-JSON
{
  "email": "<email>"
  "token": "<token>"
}

Fail: User will receive error
  'You can't login. Password is wrong'


### 3. GET /users/
**Description:** 
Mengembalikan list semua data user. Hanya dapat diakses user sebagai admin

**Headers:** Authentication token.

**Request Body:**
tidak ada

**Response :**
Success: mengembalikan list produk dalam format JSON
Response Body:
{
  "name": "<name1>"
  "description": "<description1>"
  "price": "<price1>"
  "condition": "<condition1>"
  "quantity": "<quantity1>"
}

...
dst

Fail: mengembalikan pesan gagal
{
  "success": false
}


## 4. GET /users/:id
**Description:** 
Mengembalikan 1 data user berdasarkan ID. Hanya dapat diakses oleh user sebagai admin

**Headers:** Authentication token.

**Request Body:**
tidak ada

**Response :**
Success: mengembalikan list semua data user
Response Body:
{
    "_id": "<id>",
    "name": "<name>",
    "email": "<email>",
    "phone": "<phone>",
    "address": "<address>",
    "isAdmin": <boolean>,
}

Fail: mengembalikan pesan gagal
{
  "success": false,
  "message": "The user with the given ID is not found"
}


## 5. DELETE /users/:id
**Description:** 
Menghapus sebuah user berdasarkan ID. Hanya dapat diakses oleh user sebagai admin

**Headers:** Authentication token.

**Request Body:**
tidak ada

**Response :**
Success: Data user terhapus dari database. Mengembalikan Pesan berhasil
Response Body:
{
    "success": true,
    "message": "the user is deleted!"
}

Fail: mengembalikan pesan gagal
{
  "success": false,
  "message": "The user with the given ID is not found"
}



**PRODUCTs**


## 1. GET /products/
**Description:** 
Mengembalikan list semua produk yang dijual. Dapat diakses tanpa login

**Headers:** tidak ada.

**Request Body:**
tidak ada

**Response :**
Success: Mengembalikan list semua produk yang dijual
Response Body:
{
    "_id": "676e805574ab20e5e6c3cecb",
     "name": "Motorcycle",
     "condition": "Good",
     "quantity": 1,
     "description": "this is a motorcycle",
     "price": 5000
},
... dst


Fail: mengembalikan pesan gagal
{
  "success": false
}


## 2. GET /products/:id
**Description:** 
Mengembalikan data produk yang dijual berdasarkan id. Dapat diakses tanpa login

**Headers:** tidak ada.

**Request Body:**
tidak ada

**Response :**
Success: Mengembalikan data produk yang dijual berdasarkan id
Response Body:
{
    "_id": "676e805574ab20e5e6c3cecb",
     "name": "Motorcycle",
     "condition": "Good",
     "quantity": 1,
     "description": "this is a motorcycle",
     "price": 5000
}

Fail: mengembalikan pesan gagal
{
  "success": false
}


## 3. POST /products/
**Description:** 
Menambahkan produk yang akan dijual. Hanya dapat diakses user sebagai admin

**Headers:** 
authentication token

**Request Body:**
{
     "name": "Motorcycle",
     "condition": "Good",
     "quantity": 1,
     "description": "this is a motorcycle",
     "price": 5000
}

**Response :**
Success: Data produk tersimpan di database. Mengembalikan data produk yang baru ditambahkan
Response Body:
{
    "_id": "676e805574ab20e5e6c3cecb",
     "name": "Motorcycle",
     "condition": "Good",
     "quantity": 1,
     "description": "this is a motorcycle",
     "price": 5000
}

Fail: mengembalikan pesan gagal
  'the prodcut cannot be created'


## 4. PUT /products/:id
**Description:** 
mengubah data produk berdasarkan id. Hanya dapat diakses user sebagai admin

**Headers:** 
authentication token

**Request Body:** Data baru
{
     "name": "<New_name>",
     "condition": "<New_condition",
     "quantity": <new_quantity>,
     "description": "<new_description>",
     "price": <new_price>
}

**Response :**
Success: Data produk akan diubah dengan data baru. Mengembalikan data produk yang baru diubah
Response Body:
{
     "name": "<New_name>",
     "condition": "<New_condition",
     "quantity": <new_quantity>,
     "description": "<new_description>",
     "price": <new_price>
}

Fail: mengembalikan pesan gagal
  'Fail to update the product'


## 5. DELETE /products/:id
**Description:** 
Menghapus produk berdasarkan id. Hanya dapat diakses oleh user sebagai admin

**Headers:** 
authentication token

**Request Body:**

**Response :**
Success: Data produk akan dihapus dari database. Mengembalikan pesan berhasil
Response Body:
{
    "success": true,
    "message": "the product is deleted"
}

Fail: mengembalikan pesan gagal
{
  "success": false,
  "message": "the product is not deleted"
}
