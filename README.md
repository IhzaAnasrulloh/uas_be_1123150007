# UAS Backend 1123150007

Backend API menggunakan Golang dengan Firebase Authentication, MySQL, Redis, dan JWT Authentication.

## Tech Stack

- Go SDK
- Firebase Project
- Firebase Authentication
- Firebase Service Account
- MySQL
- Redis
- Gmail SMTP
- Google Authenticator

## Struktur Folder

```bash
uas_be_1123150007/
│
├── cmd/
│   └── main.go
│
├── config/
│   ├── database.go
│   ├── firebase.go
│   ├── redis.go
│   └── smtp.go
│
├── controllers/
│   ├── auth_controller.go
│   ├── user_controller.go
│   └── otp_controller.go
│
├── middleware/
│   ├── auth_middleware.go
│   └── role_middleware.go
│
├── models/
│   ├── user.go
│   └── response.go
│
├── repositories/
│   └── user_repository.go
│
├── routes/
│   └── routes.go
│
├── services/
│   ├── auth_service.go
│   ├── firebase_service.go
│   ├── otp_service.go
│   ├── email_service.go
│   └── redis_service.go
│
├── utils/
│   ├── jwt.go
│   ├── helper.go
│   └── validator.go
│
├── firebase_service_account.json
├── .env
├── go.mod
├── go.sum
└── README.md
```

## Fitur

- Login & Register
- Firebase Authentication
- JWT Authentication
- OTP Verification
- Email Verification SMTP Gmail
- Two Factor Authentication (Google Authenticator)
- Redis Cache
- MySQL Database


## Persiapan

### 1. Firebase

- Buat Firebase Project
- Aktifkan Firebase Authentication
- Download Firebase Service Account Key
- Simpan pada folder:

```bash
/firebase_service_account.json
```

### 2. MySQL

// MySQL

-- Buat database untuk project
```bash
CREATE DATABASE emoney CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```
-- Buat user khusus (jangan pakai root untuk aplikasi)
```bash
CREATE USER 'useremoney'@'%' IDENTIFIED BY 'Password#123';
```

-- Berikan akses ke database
```bash
GRANT ALL PRIVILEGES ON emoney.* TO 'useremoney'@'%';
FLUSH PRIVILEGES;
```

-- Verifikasi:
```bash
SHOW DATABASES;
USE emoney;
SELECT USER();
```

### 3. Redis

Install Redis
Install Redis via Docker (Recommended)
Kalau sudah install Docker Desktop di Windows:

Pull image Redis:
```bash
docker pull redis
```

Jalankan Redis container:
```bash
docker run --name redis-server -p 6379:6379 -d redis
```

Test Redis:
```bash
docker exec -it redis-server redis-cli
```


### 4. Gmail SMTP

Aktifkan:

- 2-Step Verification
- App Password

Gunakan App Password pada konfigurasi SMTP.

### 5. Google Authenticator

Install aplikasi:

- Google Authenticator Android/iOS

Digunakan untuk Two Factor Authentication (2FA).

## Environment

```env
APP_PORT=8080

DB_HOST=localhost
DB_PORT=3306
DB_USER=useremoney
DB_PASSWORD='Password#123'
DB_NAME=emoney


REDIS_HOST=localhost
REDIS_PORT=6379

JWT_SECRET=your-secret-key

FIREBASE_CREDENTIALS=firebase/serviceAccountKey.json

SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_EMAIL=your_email@gmail.com
SMTP_PASSWORD=your_app_password
```

## Menjalankan Project

Install dependency:

```bash
go mod tidy
```

Jalankan aplikasi:

```bash
go run main.go
```

