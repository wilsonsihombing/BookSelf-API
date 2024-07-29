# Bookshelf API

Bookshelf API is the final project from Dicoding, which involves creating a backend API to manage book data. This API allows you to store, display, update, and delete books through various endpoints.

## Key Criteria

### 1. Port Aplikasi

Aplikasi ini harus dijalankan pada port 9000. Jika komputer Anda tidak dapat menggunakan port 9000, silakan gunakan port lain selama pengembangan dan ubah ke port 9000 sebelum mengirimkan submission.

### 2. Menjalankan Aplikasi

Aplikasi ini dijalankan menggunakan perintah `npm run start`. Berikut adalah konfigurasi `scripts` pada file `package.json`:

```json
{
  "name": "submission",
  "version": "1.0.0",
  "description": "",
  "main": "src/server.js",
  "scripts": {
    "start": "node src/server.js",
    "start-dev": "nodemon src/server.js"
  },
  "dependencies": {
    "@hapi/hapi": "^20.1.2",
    "nanoid": "^3.1.30"
  },
  "devDependencies": {
    "nodemon": "^2.0.15"
  }
}
```

### 3. Menyimpan Buku

**Endpoint:**

- **Method:** POST
- **URL:** `/books`
- **Body Request:**

```json
{
  "name": "string",
  "year": "number",
  "author": "string",
  "summary": "string",
  "publisher": "string",
  "pageCount": "number",
  "readPage": "number",
  "reading": "boolean"
}
```

**Respons Sukses:**

- **Status Code:** 201
- **Response Body:**

```json
{
  "status": "success",
  "message": "Buku berhasil ditambahkan",
  "data": {
    "bookId": "unique-id"
  }
}
```

**Respons Gagal:**

- **Status Code:** 400
- **Response Body:**

```json
{
  "status": "fail",
  "message": "Gagal menambahkan buku. Mohon isi nama buku"
}
```

atau

```json
{
  "status": "fail",
  "message": "Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount"
}
```

### 4. Menampilkan Seluruh Buku

**Endpoint:**

- **Method:** GET
- **URL:** `/books`

**Respons Sukses:**

- **Status Code:** 200
- **Response Body:**

```json
{
  "status": "success",
  "data": {
    "books": [
      {
        "id": "unique-id",
        "name": "Buku A",
        "publisher": "Dicoding Indonesia"
      }
    ]
  }
}
```

Jika belum ada buku yang disimpan:

```json
{
  "status": "success",
  "data": {
    "books": []
  }
}
```

### 5. Menampilkan Detail Buku

**Endpoint:**

- **Method:** GET
- **URL:** `/books/{bookId}`

**Respons Sukses:**

- **Status Code:** 200
- **Response Body:**

```json
{
  "status": "success",
  "data": {
    "book": {
      "id": "unique-id",
      "name": "Buku A",
      "year": 2021,
      "author": "John Doe",
      "summary": "Lorem ipsum",
      "publisher": "Dicoding Indonesia",
      "pageCount": 100,
      "readPage": 50,
      "finished": false,
      "reading": false,
      "insertedAt": "2021-07-29T06:14:28.930Z",
      "updatedAt": "2021-07-29T06:14:28.930Z"
    }
  }
}
```

**Respons Gagal:**

- **Status Code:** 404
- **Response Body:**

```json
{
  "status": "fail",
  "message": "Buku tidak ditemukan"
}
```

### 6. Mengubah Data Buku

**Endpoint:**

- **Method:** PUT
- **URL:** `/books/{bookId}`
- **Body Request:**

```json
{
  "name": "string",
  "year": "number",
  "author": "string",
  "summary": "string",
  "publisher": "string",
  "pageCount": "number",
  "readPage": "number",
  "reading": "boolean"
}
```

**Respons Sukses:**

- **Status Code:** 200
- **Response Body:**

```json
{
  "status": "success",
  "message": "Buku berhasil diperbarui"
}
```

**Respons Gagal:**

- **Status Code:** 400
- **Response Body:**

```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. Mohon isi nama buku"
}
```

atau

```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount"
}
```

atau

- **Status Code:** 404
- **Response Body:**

```json
{
  "status": "fail",
  "message": "Gagal memperbarui buku. Id tidak ditemukan"
}
```

### 7. Menghapus Buku

**Endpoint:**

- **Method:** DELETE
- **URL:** `/books/{bookId}`

**Respons Sukses:**

- **Status Code:** 200
- **Response Body:**

```json
{
  "status": "success",
  "message": "Buku berhasil dihapus"
}
```

**Respons Gagal:**

- **Status Code:** 404
- **Response Body:**

```json
{
  "status": "fail",
  "message": "Buku gagal dihapus. Id tidak ditemukan"
}
```

---
