<div align="center">
  <h2 style="text-align: center;font-weight: bold">LAPORAN PRAKTIKUM 1 SISTEM OPERASI</br></h2>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>
<br />
<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS">
  <h3 style="text-align: center;">Disusun Oleh : <br>Kelompok 7</h3>
  <p style="text-align: center;">
    <strong>Achmad Risel Araby (3123500025)</strong><br>
    <strong>Danur Isa Prabutama (3123500023)</strong><br>
    <strong>Fikri Athanabil Efendi (3123500012)</strong>

  </p>

<h3 style="text-align: center;line-height: 1.5">Politeknik Elektronika Negeri Surabaya<br>Departemen Teknik Informatika Dan Komputer<br>Program Studi Teknik Informatika<br>2024/2025</h3>
  <hr><hr>
</div>

### Pengertian Sistem Operasi?

Sistem operasi adalah salah satu perangkat lunak paling kompleks, didalamnya terdapat Kernel yang mengabstraksi fitur-fitur yang disediakan oleh perangkat keras komputer.Peran Sistem Operasi menjadikan fitur-fitur tersebut lebih aman dan nyaman untuk digunakan.

istilah "sistem operasi" biasanya mengacu pada perangkat lunak yang menyediakan antarmuka antara pengguna dan perangkat keras sistem komputer.Sebagai antarmuka antara pengguna dan perangkat keras, sistem operasi harus dirancang dengan mempertimbangkan kebutuhan pengguna serta kendala dan peluang teknologi.

### Soal

#### Sebutkan dan jelaskan proses booting Komputer!

## Apa itu Proses Booting?

Apa itu booting di OS? Di bagian ini, kita akan mendefinisikan booting di sistem operasi. Saat kita menyalakan komputer, perangkat menerima daya dan diinisialisasi. Pada tahap ini, memori utama, atau RAM, kosong. Untuk memulai sistem, sekumpulan kecil instruksi yang disimpan dalam memori read-only (ROM) dikirim ke unit pemrosesan pusat (CPU) untuk dieksekusi. Petunjuk ini membantu memeriksa komponen perangkat keras dan mengidentifikasi potensi masalah. Jika ada masalah perangkat keras, bunyi bip atau notifikasi di layar mengingatkan kita.

Setelah pemeriksaan perangkat keras selesai, proses booting sistem operasi dimulai. Sistem operasi dimuat, memungkinkan komputer berfungsi dengan baik dan menerima perintah pengguna.Proses booting di OS sangat penting untuk pengoperasian komputer yang memadai dan pelaksanaan berbagai aplikasi perangkat lunak.
booting pada komputer

## Jenis Proses Booting

### 1. Cold Booting

<img src="./media/cold.jpg"
style="width:300px; object-fit: cover;"/>

Menyalakan komputer untuk pertama kalinya atau setelah komputer dimatikan sepenuhnya. Saat kita menekan tombol daya untuk memulai cold boot, komputer membaca instruksi Basic Input/Output System (BIOS) yang disimpan di ROM. Instruksi ini memandu sistem dalam memuat sistem operasi ke dalam memori utama. Dibandingkan dengan Warm booting, booting dingin membutuhkan waktu lebih lama karena melibatkan startup sistem yang lengkap.

### 2. Warm Booting

<img src="./media/warm.png"
style="width:200px; object-fit: cover; padding: 50px; background-color: white;"/>

Warm boot, atau reboot, terjadi saat komputer dihidupkan ulang saat dihidupkan. Jenis booting ini biasanya dilakukan ketika sistem hang atau menjadi tidak responsif. Warm booting dapat dimulai melalui perangkat keras, seperti menekan tombol reset, atau perintah perangkat lunak, seperti Ctrl+Alt+Del. Seringkali perlu melakukan boot hangat setelah menginstal perangkat lunak atau perangkat keras baru untuk menerapkan perubahan konfigurasi dan memastikan fungsionalitas sistem yang tepat.

#### \* Untuk langkah langkah dari proses booting sistem operasi bisa di lihat di bawah ini:

### 1. Memuat BIOS

<img src="./media/step1.png"
style="width:5.48945in;height:2.54825in"/>
<img src="./media/step1.2.png"
style="width:5.48945in;height:2.54825in"/>

Saat kita menyalakan power, langkah pertama dalam proses booting adalah memuat BIOS. Power supply menyediakan listrik ke komponen penting, termasuk prosesor dan BIOS.

### 2. Power-On Self Test (POST)

<img src="./media/step2.png"
style="width:5.48945in;height:2.54825in"/>

Setelah memuat BIOS, ia melakukan Power on Self-Test (POST). Tes ini memeriksa memori utama komputer, drive disk, perangkat input/output, dan komponen perangkat keras lainnya. Jika kesalahan terdeteksi selama pengujian, sistem akan mengeluarkan bunyi bip atau menampilkan notifikasi di layar untuk mengingatkan pengguna.

### 3. Memuat Sistem Operasi

<img src="./media/step3.png"
style="width:5.48945in;height:2.54825in"/>

Setelah POST berhasil diselesaikan, BIOS membaca urutan bootable yang disimpan dalam CMOS (Common Metal Oxide Semiconductor). Berdasarkan urutan bootable, BIOS mencari Master Boot Record (MBR) pada perangkat yang dapat di-boot seperti floppy disk, CD-ROM, dan hard disk.
Jika MBR tidak ditemukan pada perangkat yang dapat di-boot, sistem akan menampilkan pesan yang mengatakan "Tidak Ada Perangkat Booting Ditemukan" dan crash. Namun, jika MBR ditemukan, BIOS meluncurkan boot loader, perangkat lunak aplikasi khusus yang memuat sistem operasi.

### 4. Konfigurasi Sistem

<img src="./media/step4.png"
style="width:5.48945in;height:2.54825in"/>

Setelah sistem operasi dimuat, driver perangkat dimuat ke dalam memori untuk memastikan pengoperasian komponen perangkat keras komputer dengan benar. Driver perangkat ini bertindak sebagai perantara antara sistem operasi dan perangkat keras, memungkinkan keduanya berkomunikasi secara efektif.

### 5. Memuat Utilitas Sistem

<img src="./media/step5.jpg"
style="width:5.48945in;height:2.54825in"/>

Pada langkah ini, proses booting dalam sistem operasi melibatkan pemuatan utilitas sistem ke dalam memori. Utilitas sistem, seperti perangkat lunak antivirus dan kontrol volume, merupakan alat penting yang meningkatkan fungsionalitas dan keamanan sistem operasi.

### 6. Autentikasi Pengguna

<img src="./media/step6.png"
style="width:5.48945in;height:2.54825in"/>

Jika ada otentikasi pengguna yang dikonfigurasi, sistem akan meminta pengguna untuk memasukkan kredensial mereka. Setelah sistem menerima kredensial yang valid, sistem biasanya meluncurkan shell antarmuka pengguna grafis (GUI) atau shell antarmuka baris perintah (CLI), yang memberikan akses pengguna ke sumber daya dan aplikasi sistem.

Enam langkah ini memastikan sistem operasi komputer dimuat dengan benar dan siap digunakan. Dengan memahami proses booting, kita mendapatkan wawasan tentang rangkaian kejadian rumit di balik layar saat kita menghidupkan komputer.

### Referensi

    - Richard R. Muntz. 1974 June, Operating Systems. https://ieeexplore.ieee.org/document/6323579

    - James Mickens. 2021, Operating Systems. https://read.seas.harvard.edu/cs161/2021/

    - Vibha Gupta. 2003 September 6, Booting in Operating  System (OS): Types, Steps and Process.
      https://www.almabetter.com/bytes/articles/booting-in-operating-system

### Bagaimana cara install Linux Debian di Virtual Box?

#### 1. Download Virtual Box di <https://www.virtualbox.org/wiki/Downloads>, pilih sesuai system operasi yang kalian gunakan.

<img src="./media/image2.png"
style="width:5.48945in;height:2.54825in" />

#### 2. Download Debian di <https://www.debian.org/download>

<img src="./media/image3.png"
style="width:5.56877in;height:2.57496in" />

#### 3. Buka Virtual Box, lalu klik tombol New

<img src="./media/image4.png"
style="width:5.27318in;height:2.75884in" />

#### 4. Masukkan nama virtual machine, tentukan folder penyimpanan untuk virtual machine, dan pilih file iso Debian yang telah kita download. Kemudian klik tombol next.

<img src="./media/image5.jpeg"
style="width:5.26956in;height:2.77609in" />

#### 5. Tentukan base memory (RAM) dan jumlah core CPU yang ingin andagunakan, dan centang tulisan _Enable EFI,_ lalu klik tombol next.

<img src="./media/image6.jpeg"
style="width:5.27826in;height:2.85906in" />

#### 6. Tentukan Virtual Hard Disk yang akan digunakan, lalu klik tombol next.

<img src="./media/image7.jpeg"
style="width:5.29565in;height:2.88545in" />

#### 7. Lalu akan moncul gambar seperti berikut, lalu klik tombol finish.

<img src="./media/image8.jpeg"
style="width:5.25629in;height:2.81739in" />

#### 8. Pilih virtual machine yang telah kita buat tadi, lalu klik tombol start di kanan atas.

<img src="./media/image9.png"
style="width:5.30778in;height:2.80133in" />

#### 9. Pilih Graphical Install, lalu klik enter.

<img src="./media/image10.jpeg"
style="width:5.05172in;height:4.34783in" />

#### 10. Pilih Bahasa yang ingin kita gunakan, lalu klik tombol continue.

<img src="./media/image11.jpeg" style="width:4.57595in;height:4.2in" />

#### 11. Pilih lokasi kalian, sebagai contoh saya pilih other, kemudian Asia, dan pilih Indonesia. Lalu klik continue.

<img src="./media/image12.jpeg"
style="width:4.60129in;height:4.1913in" />

#### 12. Pilih konfigurasi lokasi, lalu klik continue.

<img src="./media/image13.jpeg"
style="width:4.70435in;height:4.26608in" />

<img src="./media/image14.jpeg"
style="width:4.72174in;height:4.35298in" />

#### 13. Pilih konfigurasi keyboard, lalu klik continue.

<img src="./media/image15.jpeg"
style="width:4.8278in;height:4.25217in" />

#### 14. Tunggu proses loading hingga selesai.

<img src="./media/image16.jpeg"
style="width:4.48696in;height:4.21563in" />

#### 15. Berikan nama Hostname seperti dibawah ini

<img src="./media/image17.png"
style="width:4.87968in;height:2.59259in" />

#### 16. Pilih lokasi other untuk mencari Indonesia

<img src="./media/image18.png"
    style="width:4.96682in;height:2.63889in" />

#### 17. Selanjutnya pilih Asia

<img src="./media/image19.png"
style="width:4.93197in;height:2.62037in" />

#### 18. Dan pilih Indoneisa

<img src="./media/image20.png"
style="width:5.0191in;height:2.66667in" />

#### 19. Untuk nama domain di kosongi dulu

<img src="./media/image21.png"
style="width:5.07139in;height:2.69444in" />

#### 20. Buatlah pasword untuk root (Super User)

<img src="./media/image22.png"
style="width:5.07083in;height:2.69415in" />

#### 21. Masukan nama lengkap pengguna

<img src="./media/image23.png"
style="width:4.8884in;height:2.59722in" />

#### 22. Konfigurasi username dan password

<img src="./media/image24.png"
    style="width:4.93056in;height:2.61962in" />

#### 23. Gunakan password yang aman

<img src="./media/image25.png"
style="width:4.9064in;height:2.60417in" />

#### 24. Konfigurasi pengaturan waktu

<img src="./media/image26.png"
style="width:4.73917in;height:2.51389in" />

#### 25. Dibagian partion disk pilih manual

<img src="./media/image27.png"
style="width:4.79154in;height:2.54167in" />

#### 26. Pilih yang ada size nya

<img src="./media/image28.png"
style="width:4.84391in;height:2.56944in" />

#### 27. Pilih **Yes**

<img src="./media/image29.png"
style="width:4.80556in;height:2.54653in" />

#### 28. Pilih FREE SPACE

<img src="./media/image30.png"
style="width:4.80556in;height:2.54653in" />

#### 29. Pilih opsi create a new partion

<img src="./media/image31.png"
style="width:4.79637in;height:2.54167in" />

#### 30. Berikan size 20GB

<img src="./media/image32.png"
style="width:4.83333in;height:2.56125in" />

#### 31. Pilih primary

<img src="./media/image33.png"
style="width:4.90278in;height:2.59805in" />

#### 32. Pilih Benginning

<img src="./media/image34.png"
    style="width:4.90278in;height:2.59805in" />

#### 33. Pastikan Use as Ext4 dan bootable flag dalam keadaan ON dan dengan

    mount point / karena akan menjadi root

<img src="./media/image35.png"
    style="width:4.91431in;height:2.60417in" />

#### 34. Setelah semua selesai pilih done

    setting

<img src="./media/image36.png"
    style="width:4.89466in;height:2.59375in" />

#### 35. Pilih Free Space lagi untuk partisi yang

    kedua

<img src="./media/image37.png"
    style="width:4.91432in;height:2.60417in" />

#### 36. Pilih opsi create a new partion

<img src="./media/image38.png"
style="width:5.03226in;height:2.66667in" />

#### 37. Berikan size 5GB

<img src="./media/image39.png"
    style="width:5.08468in;height:2.69444in" />

#### 38. Pilih primary

<img src="./media/image40.png"
style="width:5.08468in;height:2.69444in" />

#### 39. Pilih Benginning

<img src="./media/image41.png"
    style="width:5.04167in;height:2.67165in" />

#### 40. Ubah mount pointny dengan cara klik mount point

<img src="./media/image42.png"
    style="width:5.04167in;height:2.67165in" />

#### 41. Pilih enter manually

<img src="./media/image43.png"
    style="width:4.95833in;height:2.62749in" />

#### 42. Ubah menjadi /storage

<img src="./media/image44.png"
    style="width:5.06944in;height:2.68637in" />

#### 43. Setelah selesai pilih done partition

<img src="./media/image45.png"
    style="width:5.06944in;height:2.68637in" />

#### 44. Pilih Free Space untuk partisi yang

    ketiga

<img src="./media/image46.png"
    style="width:5.06944in;height:2.68637in" />

#### 45. Pilih opsi create a new partion

<img src="./media/image38.png"
style="width:5.03226in;height:2.66667in" />

#### 46. Berikan size 1.5GB

<img src="./media/image47.png"
    style="width:5.1371in;height:2.72222in" />

#### 47. Pilih primary

<img src="./media/image40.png"
style="width:5.08468in;height:2.69444in" />

#### 48. Pilih Benginning

<img src="./media/image41.png"
    style="width:5.04167in;height:2.67165in" />

#### 49. Ubah Use as nya menjadi Swap Area

<img src="./media/image48.png"
    style="width:5.03226in;height:2.66667in" />

#### 50. Setelah selesai pilih done partition

<img src="./media/image45.png"
    style="width:5.06944in;height:2.68637in" />

#### 51. Setelah semua partisi sudah di buat pilih finish

    partitioning

<img src="./media/image49.png"
    style="width:4.90121in;height:2.59722in" />

#### 52. Pilih **Yes,** pastikan semua partisi sudah benar

<img src="./media/image50.png" style="width:4.875in;height:2.58333in" />

#### 53. Tunggu proses sampai selesai

<img src="./media/image51.png"
    style="width:4.90121in;height:2.59722in" />

#### 54. Pada menu extra installation media, pilih No

<img src="./media/image52.png"
    style="width:5.02778in;height:2.66429in" />

#### 55. Pada bagian archive mirror country pilih

    Indonesia

<img src="./media/image53.png"
    style="width:5.02778in;height:2.66429in" />

#### 56. Pilih kebo.pens.ac.id

<img src="./media/image54.png"
    style="width:5.08468in;height:2.69444in" />

#### 57. Untuk bagian proxy dikosongi saja

<img src="./media/image55.png"
    style="width:5.11111in;height:2.70845in" />

#### 58. Tunggu proses hingga selesai

<img src="./media/image56.png"
    style="width:5.11111in;height:2.70845in" />

#### 59. Pilih Yes di bagian configure popularity contest

<img src="./media/image57.png"
    style="width:5.11111in;height:2.70845in" />

#### 60. Dibagin software selection dibiarkan defaultnya saja

<img src="./media/image58.png"
    style="width:4.80556in;height:2.54653in" />

#### 61. Tunggu proses hingga selesai

<img src="./media/image59.png"
    style="width:4.80556in;height:2.54653in" />

#### 62. Setelah selesai sistem akan reboot dan debian sudah berhasil diinstal

<img src="./media/image60.png"
    style="width:4.80556in;height:2.54653in" />
