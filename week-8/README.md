<div align="center">
  <h2 style="text-align: center;font-weight: bold">LAPORAN PRAKTIKUM <br/> WORKSHOP ADMINISTRASI JARINGAN</br></h2>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : </h3>
  <p style="text-align: center;">
    <strong>Danur Isa Prabutama (3123500023)</strong><br>
  </p>

<h3 style="text-align: center;line-height: 1.5; text-transform: uppercase">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2025/2026</h3>
  <hr>
</div>

<h3 style="text-align: center;line-height: 1.5">Praktikum Minggu 8</h3>

#### Migrasi NTP, DNS, SAMBA ke Jaringan Lab (Kelompok 1)

Praktikum ini bertujuan untuk memindahkan konfigurasi NTP (Network Time Protocol), DNS (Domain Name System), dan SAMBA (file sharing server) dari jaringan internal network ke jaringan lab sesuai dengan kelompk masing-masing. Berikut langkah-langkah konfigurasinya.

#### Konfigurasi NTP (NTPSec) Pada VM 1 (Server)

1. Instalai paket `ntpsec`

   ![alt text](assets/ntp-install.png)

2. Konfigurasi server NTP

   ![alt text](assets/ntp-conf.png)

   Berikan modifikasi server dengan mengganti server NTP

3. Restart service ntpsec
   Jalankan perintah `systemctl restart ntpsec`

4. Validasi NTP Server
   ![alt text](assets/ntp-q.png)

#### Instalasi dan Konfigurasi Samba

Samba adalah perangkat lunak open-source yang memungkinkan berbagi file dan printer antara sistem operasi Windows dan Unix-like (seperti Linux, macOS, dan lainnya). Samba mengimplementasikan protokol SMB/CIFS (Server Message Block/Common Internet File System), yang merupakan protokol berbagi file dan printer yang digunakan secara luas di jaringan Windows. Berikut langkah konfigurasinya.

#### Instalasi package Samba

 <img src="assets/samba-install.png" alt="asset">

#### Percobaan Akes FIle Samba

1. Konfigurasi pada samba

![alt text](assets/samba-conf.png)

2. Membuat sebuah file di direktori /home/share

![alt text](assets/samba-fully-mkdir.png)

3. Percobaan akses dari jaringan kelompok

![alt text](assets/samba-access-kelompok.png)

4. Percobaan akses dari host jaringan kelompok lain

![alt text](assets/samba-access-kelompok-lain.jpeg)

### Konfigurasi Bind9

DNS Server: 192.168.1.247

#### Konfigurasi DNS Server (Bind9) Pada Server

1. Instalasi paket dengan menjalankan perintah `apt -y install bind9 bind9utils`
2. Modifikasi file `/etc/bind/named.conf`

   ![alt text](assets/namedconf.png)

3. Modifikasi file `vi /etc/bind/named.conf.options`

   ![alt text](assets/named-conf-options.png)

4. Konfigurasi internal zone pada file `/etc/bind/named.conf.internal-zones`

   ![alt text](assets/internal-zones.png)

5. Konfigurasi file `/etc/default/named`

   ![alt text](assets/named.png)

6. Buat file sesuai dengan domain lokal

   ![alt text](assets/kelompok1.home.png)

7. Buat file sesuai dengan IP Address

   ![alt text](assets/1.168.192.db.png)

#### Tes DNS Server 1

1. Tes DNS Server dari jaringan dalam kelompok

![alt text](assets/percobaan-dns-internal.png)
