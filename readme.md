# Rest Server Menggunakan Codeigniter 

* Cara Menggunakan Rest Server Codeigniter
1. Import Database 
```
$ mysql -u root -p
$ create database wpu-rest
$ use wpu-rest

```
2. Masukan Table mahasiswa.
	2.1 Buka file mahasiswa.sql
	2.2 import sql
3. Buat file bernama .htaccess untuk menghilangkan index.php
```
    RewriteEngine on
    RewriteBase /your-project-directory-name/
    RewriteCond $1 !^(index.php|resources|robots.txt)
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^(.*)$ index.php/$1 [L,QSA]
```
4. Buka file di folder config -> database.php, perhatikan pada bagian hostname, username, password, database samakan dengan komputer masing - masing anda
```
'hostname' => 'localhost',
'username' => 'admin',
'password' => '123456',
'database' => 'wpu_rest',

```
5. Buka file di folder config -> config.php
```
$config['base_url'] = 'http://127.0.0.1/rest_server_new/';

$config['index_page'] = '';
```

6. Buka file di folder config -> autoload.php
tambahkan
```
$autoload['libraries'] = array('database');
$autoload['helper'] = array('url');
```
7. Jangan lupa aktifkan web server anda
8. Untuk test-Nya gunakan POSTMAN
```
post get delete put
http://127.0.0.1/rest_server_new/index.php/api/mahasiswa
```
