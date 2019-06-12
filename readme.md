# Rest Server Menggunakan Codeigniter 

Tutorial Lengkapnya https://www.bewoksatukosong.com/2019/06/cara-membuat-rest-api-server-codeigniter-mysql-2019.html

1. Membuat dan Import Database Melalui Terminal atau cmd
```
$ mysql -u root -p
$ create database wpu_rest;
$ use wpu_rest;
$ CREATE TABLE `mahasiswa` (
  `id` int(11) NOT NULL,
  `nrp` char(9) NOT NULL,
  `nama` varchar(250) NOT NULL,
  `email` varchar(250) DEFAULT NULL,
  `jurusan` varchar(64) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

INSERT INTO `mahasiswa` (`id`, `nrp`, `nama`, `email`, `jurusan`) VALUES
(1, '135520103', 'maya septha', 'maya95@gmail.com', 'software enginer'),
(3, '135520103', 'pradina', 'pradina94@gmail.com', 'Robotic'),
(5, '135520103', 'gerald', 'gerald94@gmail.com', 'Teknik Informatika'),
(6, '135520103', 'Diani', 'Diani@gmail.com', 'akutansi');
```
2. Membuat database dan import menggunakan phpmyadmin
- Buat database baru wpu_rest
- import sql (klik sql)
```
CREATE TABLE `mahasiswa` (
  `id` int(11) NOT NULL,
  `nrp` char(9) NOT NULL,
  `nama` varchar(250) NOT NULL,
  `email` varchar(250) DEFAULT NULL,
  `jurusan` varchar(64) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

INSERT INTO `mahasiswa` (`id`, `nrp`, `nama`, `email`, `jurusan`) VALUES
(1, '135520103', 'maya septha', 'maya95@gmail.com', 'software enginer'),
(3, '135520103', 'pradina', 'pradina94@gmail.com', 'Robotic'),
(5, '135520103', 'gerald', 'gerald94@gmail.com', 'Teknik Informatika'),
(6, '135520103', 'Diani', 'Diani@gmail.com', 'akutansi');
```
- Done

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
$config['base_url']   = 'http://127.0.0.1/rest_server_new/';

$config['index_page'] = '';
```

6. Buka file di folder config -> autoload.php
tambahkan
```
$autoload['libraries'] = array('database');
$autoload['helper']    = array('url');
```
7. Jangan lupa aktifkan web server anda
8. Untuk test-Nya gunakan POSTMAN
```
post get delete put
http://127.0.0.1/rest_server_new/index.php/api/mahasiswa
```
