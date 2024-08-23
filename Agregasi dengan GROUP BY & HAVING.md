 **Ketentuan tabel: tipe data dan constraintnya :**  
- NIP: int & primary key
- NDep: varchar & NOT NULL
- NBlk: varchar
- JK: enum, NOT NULL
- Alamat: text, NOT NULL
- Telp: varchar, NOT NULL
- Jabatan: enum
- Gaji: BIGINT, NOT NULL
- NoCab: Varchar, NOT NULL
### Hasil Struktur tabel Pegawai 

![](asset/1.jpg)
(Hasil di PhpMYAdmin)
![github](asset/3.jpg)

**Analisis Query :**  
- `desc pegawai ;` Kueri ini digunakan untuk menampilkan struktur tabel pegawai, 
termasuk nama kolom, tipe data, batasan null/bukan null, batasan kunci, nilai default, dan
informasi tambahan.
- `NIP` Bidang ini adalah tipe data integer dan bertindak sebagai
kunci utama untuk tabel. Bidang ini tidak boleh null, yang berarti bahwa setiap baris dalam
tabel harus memiliki nilai NIP yang unik.
- `NDep` Ini adalah kolom varchar yang menyimpan nama. Kolom ini tidak boleh null.
- `NBlk`  Ini adalah kolom varchar yang menyimpan nama belakang. Kolom ini tidak
boleh null, yang berarti bahwa setiap karyawan harus dikaitkan dengan belakang.
- `JK`  Ini adalah kolom enum yang menyimpan jenis kelamin karyawan,
dengan kemungkinan nilai 'L' (Laki-laki) atau 'P' (Perempuan). Kolom ini tidak boleh null,
yang berarti bahwa setiap karyawan harus memiliki jenis kelamin yang ditentukan.
- `Alamat` Ini adalah kolom teks yang menyimpan alamat karyawan. Kolom ini tidak boleh
kosong, yang berarti setiap karyawan harus memiliki alamat.
- `Telp (Telepon)` Ini adalah kolom varchar yang menyimpan nomor telepon karyawan.
Kolom ini tidak boleh kosong dan harus unik, yang berarti setiap karyawan harus memiliki
nomor telepon yang unik dan pastinya berbeda-beda.
- `Jabatan` Ini adalah kolom enum yang menyimpan posisi pekerjaan karyawan, dengan kemungkinan nilai 'Manajer', 'Sales', atau 'Staf'. Kolom ini tidak boleh kosong, yang
berarti bahwa setiap karyawan harus memiliki posisi pekerjaan yang ditentukan.
- `Gaji` Ini adalah kolom bigint yang menyimpan gaji karyawan. Kolom ini tidak
boleh null, yang berarti setiap karyawan harus memiliki gaji yang telah ditentukan.
- `NoCab` Ini adalah kolom varchar yang menyimpan nomor cabang. Kolom
ini tidak boleh null dan merupakan bagian dari indeks multikolom, yang berarti bahwa
kombinasi NoCab dan satu atau beberapa kolom lainnya harus unik.

**Kesimpulan Analisis Query:** 
Analisis ini memberikan contoh tentang bagaimana tabel `pegawai` diatur dan bagaimana data di dalamnya akan disimpan dan dikelola, termasuk kendali integritas data melalui penggunaan kunci utama dan indeks unik.
### Hasil data tabel Pegawai 
![github](asset/2.jpg)
(Hasil di PhpMyAdmin)
![github](asset/4.jpg)

**Analisis Query :** 
- **NIP (Nomor Induk Pegawai)**
Tipe Data : `int(10)` `NIP` adalah kunci utama yang unik untuk setiap pegawai. Nilai-nilai `NIP` berbeda untuk setiap pegawai, menunjukkan bahwa data ini berfungsi dengan baik sebagai pengidentifikasi unik.
- **NDep (Nama Depan)**
Tipe Data: `varchar(50)` Kolom ini menyimpan nama depan pegawai. Nama-nama seperti 'Emya', 'Diah', 'Dian', dll., semuanya valid dan konsisten.
- **NBlk (Nama Belakang)**
**Tipe Data**: `varchar(25)` Kolom ini menyimpan nama belakang pegawai. Nama-nama seperti 'Salsalina', 'Wahyuni', 'Anggraini', dll., semuanya valid dan konsisten.
- **JK (Jenis Kelamin)**
**Tipe Data**: `enum('L','P')`  Kolom ini menyimpan jenis kelamin pegawai, dengan 'L' untuk Laki-laki dan 'P' untuk Perempuan. Semua nilai dalam data ini sesuai dengan pilihan yang telah ditentukan.
- **Alamat** 
**Tipe Data**: `text` Kolom ini menyimpan alamat lengkap pegawai. Data alamat seperti 'Jl.Suci 78 Bandung', 'Jl.Maluku 56 Bandung', dll., menunjukkan format teks yang panjang, sesuai dengan kebutuhan penyimpanan informasi alamat.
- **Telp (Telepon)**
**Tipe Data**: `varchar(15)`
Kolom ini menyimpan nomor telepon pegawai. Data di sini adalah unik karena memiliki kunci unik (`UNI`), yang memastikan tidak ada dua pegawai dengan nomor telepon yang sama.
- **Jabatan**
**Tipe Data**: `enum('Manajer','Sales','Staf')`
Kolom ini menyimpan jabatan pegawai. Nilai yang ada seperti 'Manajer', 'Sales', dan 'Staf' semuanya valid sesuai dengan pilihan yang ditetapkan. Ada satu baris dengan nilai kosong, yang bisa menunjukkan bahwa jabatan belum ditentukan untuk pegawai tersebut.
- **Gaji**
**Tipe Data**: `bigint(25)`
 Kolom ini menyimpan gaji pegawai dengan kapasitas yang besar, sesuai dengan nilai-nilai yang ada (misalnya, 5250000, 2500000, dll.). Semua nilai gaji tampaknya valid dan konsisten dengan jenis data `bigint`.
- **NoCab (Nomor Cabang)**
**Tipe Data**: `varchar(10)` Kolom ini menyimpan nomor cabang tempat pegawai bekerja. Nilai seperti 'C101', 'C103', dan 'C104' menunjukkan bahwa pegawai dikelompokkan berdasarkan cabang, dengan beberapa pegawai yang memiliki cabang yang sama.

**Kesimpulan Analisis Query :**
Hasil dari query `SELECT * FROM pegawai` menunjukkan bahwa tabel `pegawai` memiliki struktur yang konsisten dengan informasi lengkap tentang pegawai. Kolom `NIP` bertindak sebagai kunci utama, memastikan bahwa setiap pegawai memiliki identifikasi unik, sementara kolom `Telp` juga memiliki kunci unik, mencegah adanya duplikasi nomor telepon.
### GROUP BY & HAVING

1.  SELECT COUNT
```sql
SELECT COUNT(NIP) AS JumlahPegawai, COUNT(Jabatan) AS JumlahJabatan FROM pegawai;
```
![](asset/5.jpg)
- `SELECT`  sebuah fungsi yang menghitung jumlah baris dalam kolom `NIP`dari tabel `pegawai`.
- `COUNT(NIP)`akan menghitung jumlah baris yang memiliki nilai di kolom `NIP`. Jadi, jika ada 9 baris dengan nilai yang valid di kolom `NIP`, maka hasilnya akan 9.
- `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `JumlahPegawai` merupakan nama ubahan  dari perintah AS yang digunakan, dan nama sementara dari perintah `COUNT(NIP)`
- `COUNT(Jabatan)`akan menghitung jumlah baris yang memiliki nilai di kolom `Jabatan`. Jadi, jika ada 9 baris dengan nilai yang valid di kolom `Jabatan`, maka hasilnya akan 9.
- `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Jumlah Jabatan` merupakan nama sementara dari perintah `COUNT(Jabatan)`  
- `FROM pegawai;`Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai`.

Jadi, query ini akan mengembalikan dua kolom: `JumlahPegawai`yang berisi jumlah baris dengan nilai valid di kolom `NIP`, dan `JumlahJabatan`yang berisi jumlah baris dengan nilai valid di kolom `Jabatan`. Hasil query ini menunjukkan bahwa terdapat 9 pegawai dan 9 jabatan yang berbeda di dalam tabel `pegawai`. 


2. SELECT COUN, FROM, WHERE
```SQL
SELECT COUNT(NIP) AS JumlahPegawai
FROM pegawai
WHERE NoCab = 'C102';
```
![](asset/6.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `COUNT(NIP)` menghitung jumlah baris data yang memiliki nilai isi data dari jolom yang dipilih `NIP` adalah nama kolom yang dipilih untuk dihitung
- `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `JumlahPegawai` merupakan nama ubahan  dari perintah AS yang digunakan, dan nama sementara dari perintah `COUNT(NIP)`
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai`. Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `WHERE` merupakan kondisi yang harus dipenuhi, jadi hanya barisan data ayng memiliki `C102` di kolom `NoCab` yang bisa dihitung
- `NoCab = 'C102` adalah kondisi `WHERE` yang harus dipen-uhi, jadi hanya barisan data yang memiliki nilai `C102` di kolom `NoCab` yang bisa dihitung

Jadi, query ini akan mengembalikan jumlah pegawai yang bekerja di cabang dengan nomor `'C102'`, yang dalam tabel ini adalah 3 orang.

3. SELECT COUNT, FROM, GROUP BY
```sql
SELECT NoCab, COUNT(NIP) AS Jumlah_Pegawai
FROM pegawai
GROUP BY NoCab;
```
![](asset/7.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `COUNT(NIP)` menghitung jumlah baris data yang memiliki nilai isi data dari jolom yang dipilih `NIP` adalah nama kolom yang dipilih untuk dihitung
- `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `JumlahPegawai` merupakan nama ubahan  dari perintah AS yang digunakan, dan nama sementara dari perintah `COUNT(NIP)`
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai`. Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.

Hasil query ini menunjukkan jumlah pegawai untuk masing-masing cabang berdasarkan nilai `NoCab`. Terlihat bahwa:
- Cabang C101 memiliki 2 pegawai
- Cabang C102 memiliki 3 pegawai
- Cabang C103 memiliki 2 pegawai
- Cabang C104 memiliki 2 pegawai

4. SELECT SUM, FROM
```sql
SELECT NoCab, COUNT(NIP) AS Jumlah_Pegawai
FROM pegawai
GROUP BY NoCab HAVING COUNT(NIP) >= 3;
```
![](asset/8.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `COUNT(NIP)` menghitung jumlah baris data yang memiliki nilai isi data dari jolom yang dipilih `NIP` adalah nama kolom yang dipilih untuk dihitung
- `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `JumlahPegawai` merupakan nama ubahan  dari perintah AS yang digunakan, dan nama sementara dari perintah `COUNT(NIP)`
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai`. Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `Having` untuk menentukan kondisi yang harus dipenuhi oleh suatuu kelompok data agar bisa ditampilkan 
- `COUNT (NIP) >= 3` merupakan kondisi yang harus dipenuhi oleh suatu kelompok data

Jadi, query ini akan menghitung total gaji dari semua pegawai yang ada di tabel `pegawai`. Hasil query menunjukkan bahwa total gaji seluruh pegawai adalah Rp 30.575.000.

5. SELECT SUM
```sql
SELECT SUM(Gaji) AS Total_Gaji
FROM pegawai;
```
![](asset/9.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `SUM (Gaji)` untuk menghitung Jumlah data khusus angka pada kolom yang dipilih. Gaji merupakan nama kolom yang dipilih untuk dihitung jumlah isi datanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Total_Gaji` merrupakan nama sementara dari dari perintah AS
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai`.
- Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.

Jadi, kolom gaji yang isi dataya berupa angka-angka, semuanya dijumlahkan menjadi satu seperti ditotalkan. Dan hasilnya adalah 305575000. Adapu nama kolom dari hasil jumlah tersebut diubh dari `SUM(Gaji)` menjadi `Total_Gaji`

6. SELECT SUM, FROM, WHERE
```sql
SELECT SUM(Gaji) AS Gaji_Manajer
FROM pegawai
WHERE Jabatan = 'Manajer';
```
![](asset/10.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `SUM (Gaji)` untuk menghitung Jumlah data khusus angka pada kolom yang dipilih. Gaji merupakan nama kolom yang dipilih untuk dihitung jumlah isi datanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Total_Gaji` merrupakan nama sementara dari dari perintah AS
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `WHERE` kondisi yang harus dipenuhi oleh suatu kolom agar datanya bisa dijumlah
- `Jabatan ='Manajer'` merupakan kondisi dari `WHERE`. Hnaya barisan data yang kolom jabatannya berisi manajer yang kolom gajinya bisa di jumlahkan.

Hasil query ini menunjukkan bahwa total gaji untuk seluruh pegawai yang berjabatan sebagai Manajer adalah Rp 17.250.000.

7. SELECT, FROM, GROUP BY
```SQL
SELECT NoCab, SUM(Gaji) AS TotalGaji
FROM pegawai
GROUP BY NoCab;
```
![](asset/11.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `SUM (Gaji)` untuk menghitung Jumlah data khusus angka pada kolom yang dipilih. Gaji merupakan nama kolom yang dipilih untuk dihitung jumlah isi datanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Total_Gaji` merrupakan nama sementara dari dari perintah AS
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.

Hasil query ini menunjukkan total gaji untuk masing-masing cabang berdasarkan nilai `NoCab`. Terlihat bahwa:
- Cabang C101 memiliki total gaji Rp 7.750.000
- Cabang C102 memiliki total gaji Rp 9.450.000
- Cabang C103 memiliki total gaji Rp 9.000.000
- Cabang C104 memiliki total gaji Rp 4.375.000

8. SELECT, FROM, GROUP BY, HAVING
```sql
SELECT NoCab, SUM(Gaji) AS Total_Gaji
FROM pegawai
GROUP BY NoCab
HAVING SUM(Gaji) >= 8000000;
```
![](asset/12.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `SUM (Gaji)` untuk menghitung Jumlah data khusus angka pada kolom yang dipilih. Gaji merupakan nama kolom yang dipilih untuk dihitung jumlah isi datanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Total_Gaji` merrupakan nama sementara dari dari perintah AS
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `Having` kondisi yang harus dipenuhi oleh suatu kelompok data agar bisa ditampilkan 
- `SUM(Gaji) >= 8.000000` kondisi dari having, Hasil dari penjumlahan Gaji yang hanya bisa ditampilkan adalah hasil yang lebih dari atau sama dengan 8.000000 

Hasil query ini menunjukkan bahwa hanya ada 2 cabang yang memiliki total gaji lebih besar atau sama dengan Rp 8.000.000, yaitu:
- Cabang C102 dengan total gaji Rp 9.450.000
- Cabang C103 dengan total gaji Rp 9.000.000

9. SELECT AVG
```sql
SELECT AVG(Gaji) AS Rata_rata
FROM pegawai;
```
![](asset/13.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `AVG(Gaji)` untuk menghitung rata-rata dari data yang ada pada kolom yang dipilih, Gaji adalah nama kolom yang dipilih untuk dihitung rata-ratanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Rata-rata` nama sementara dari perintah AS
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.

Jadi, query ini akan menghitung rata-rata gaji dari semua pegawai yang ada di tabel `pegawai`.
Hasil query menunjukkan bahwa rata-rata gaji pegawai adalah Rp 3.397.222,22.

10. SELECT, FROM, WHERE
```sql
SELECT AVG(Gaji) AS RataMgr
FROM pegawai
WHERE Jabatan = 'Manajer';
```
![](asset/14.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `AVG(Gaji)` untuk menghitung rata-rata dari data yang ada pada kolom yang dipilih, Gaji adalah nama kolom yang dipilih untuk dihitung rata-ratanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `Rata-rata` nama sementara dari perintah AS
- `GajiRataMGR` nama sementara dari perintah AS
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `WHERE` kondisi yang harus dipenuhi oleh suatu kolom agar datanya bisa dihitung rata-ratanya
- `Jabatan = 'Manajer'` kondisi dari WHERE. Barisan data yang kolom jabatannya manajer akan dihitung rata-rata kolom gajinya 

Jadi, query ini akan menghitung rata-rata gaji dari semua pegawai yang memiliki jabatan sebagai Manajer.
Hasil query menunjukkan bahwa rata-rata gaji pegawai yang berjabatan sebagai Manajer adalah Rp 5.750.000.

11. SELECT AVG, FROM, GROUP BY
```sql
SELECT NoCab, AVG(Gaji) AS RataGaji
FROM pegawai
GROUP BY NoCab;
```
![](asset/15.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `AVG(Gaji)` untuk menghitung rata-rata dari data yang ada pada kolom yang dipilih, Gaji adalah nama kolom yang dipilih untuk dihitung rata-ratanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `RataGaji` adalah nama sementara dari perintah `AS`
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.

Hasil query ini menunjukkan rata-rata gaji pegawai untuk masing-masing cabang:
- Cabang C101: Rp 3.875.000
- Cabang C102: Rp 3.150.000
- Cabang C103: Rp 4.500.000
- Cabang C104: Rp 2.187.500

12. SELECT, FROM, GROUP BY, HAVING
```sql
SELECT NoCab, AVG(Gaji) AS RataGaji
FROM pegawai
GROUP BY NoCab
HAVING NoCab = 'C101' OR NoCab = 'C102';
```
![](asset/16.jjpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `AVG(Gaji)` untuk menghitung rata-rata dari data yang ada pada kolom yang dipilih, Gaji adalah nama kolom yang dipilih untuk dihitung rata-ratanya
-  `AS` untuk mengubah nama dari suatu kolom untuk sementara
- `RataGaji` adalah nama sementara dari perintah `AS`
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `HAVING` kondisi yang harus dipenuhi oleh suatu kelompok data
- `NoCab ='C102' OR NoCab ='C102` merupakan kondisi dari `HAVING`

Hasil query ini menunjukkan rata-rata gaji pegawai hanya untuk cabang C101 dan C102:
- Cabang C101: Rp 3.875.000
- Cabang C102: Rp 3.150.000

13.  SELECT MAX
```sql
SELECT MAX(Gaji) AS GajiTerbesar, MIN(Gaji) AS GajiTerkecil
FROM pegawai;
```
![](asset/17.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `MAX(Gaji)` untuk menampilkan nilai maksimum atau terbesar/tertinggi dari suatu data dalam kolom yang dipilih. `Gaji` adalah nama kolom yang dipilih
- `AS GajiTerbesar` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTerbesar
- `MIN(Gaji)` untuk menampilkan nilai terkecil dari suatu data dalam kolom yang dipilih
- `AS GajiTerkecil` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTekecil
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.

Hasil query ini menunjukkan bahwa:
- Gaji terbesar di antara semua pegawai adalah Rp 6.250.000.
- Gaji terkecil di antara semua pegawai adalah Rp 1.725.000.

14. SELECT MAX
```sql
SELECT MAX(Gaji) AS GajiTerbesar, MIN(Gaji) AS GajiTerkecil
FROM pegawai
WHERE Jabatan = 'Manajer';
```
![](asset/18.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `MAX(Gaji)` untuk menampilkan nilai maksimum atau terbesar/tertinggi dari suatu data dalam kolom yang dipilih. `Gaji` adalah nama kolom yang dipilih
- `AS GajiTerbesar` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTerbesar
- `MIN(Gaji)` untuk menampilkan nilai terkecil dari suatu data dalam kolom yang dipilih
- `AS GajiTerkecil` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTekecil
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `WHERE` kondisi yang harus dipenuhi oleh suatu kolom data agar bisa di tampilkan
- `Jabatan = 'Manajer'` kondisi dari WHERE yang harus dipenuhi, Barisan data yang kolom jabatannya berisi manajer akan ditampilkan kolom gajinya

Hasil query ini menunjukkan bahwa: 
- Gaji terbesar di antara para manajer adalah Rp 6.250.000.
- Gaji terkecil di antara para manajer adalah Rp 5.250.000.

15.  SELECT, FROM, GROUP BY
```sql
SELECT NoCab, MAX(Gaji) AS GajiTerbesar, MIN(Gaji) AS GajiTerkecil
FROM pegawai
GROUP BY NoCab;
```
![](asset/19.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `MAX(Gaji)` untuk menampilkan nilai maksimum atau terbesar/tertinggi dari suatu data dalam kolom yang dipilih. `Gaji` adalah nama kolom yang dipilih
- `AS GajiTerbesar` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTerbesar
- `MIN(Gaji)` untuk menampilkan nilai terkecil dari suatu data dalam kolom yang dipilih
- `AS GajiTerkecil` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTekecil
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.

Hasil query ini menunjukkan:
 Untuk cabang C101:
- Gaji terbesar: Rp 5.250.000
- Gaji terkecil: Rp 2.500.000
 Untuk cabang C102:
- Gaji terbesar: Rp 5.750.000
- Gaji terkecil: Rp 1.750.000
 Untuk cabang C103:
- Gaji terbesar: Rp 6.250.000
- Gaji terkecil: Rp 2.750.000
 Untuk cabang C104:
- Gaji terbesar: Rp 2.650.000
- Gaji terkecil: Rp 1.725.000

16. SELECT, FROM, GROUP BY, HAVING COUNT
```sql
SELECT NoCab, MAX(Gaji) AS GajiTerbesar, MIN(Gaji) AS GajiTerkecil
FROM pegawai
GROUP BY NoCab
HAVING COUNT(NIP) >= 3;
```
![](asset/20.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `MAX(Gaji)` untuk menampilkan nilai maksimum atau terbesar/tertinggi dari suatu data dalam kolom yang dipilih. `Gaji` adalah nama kolom yang dipilih
- `AS GajiTerbesar` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTerbesar
- `MIN(Gaji)` untuk menampilkan nilai terkecil dari suatu data dalam kolom yang dipilih
- `AS GajiTerkecil` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi nama sementaranya yaitu GajiTekecil
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `HAVING` kondisi yang harus dipenuhi oleh suatu kelompok data
- `COUNT(NIP) >= 3` kondisi dari `HAVING`. Hanya hasil hitung kolom NIP yang lebih dari atau sama dengan 3 yang muncul

Hasil query ini menunjukkan bahwa hanya ada satu cabang (C102) yang memiliki jumlah pegawai minimal 3, dengan:
- Gaji terbesar: Rp 5.750.000
- Gaji terkecil: Rp 1.750.000

17.  SELECT COUNT
```sql
SELECT COUNT(NIP) AS JumlahPegawai, 
       SUM(Gaji) AS TotalGaji,
       AVG(Gaji) AS RataGaji,
       MAX(Gaji) AS GajiMaks,
       MIN(Gaji) AS Gajimin
FROM pegawai;
```
![](asset/21.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `COUNT(NIP)` untuk menghitung jumlah barisan data yang ada pada kolam yang dipilih
- `AS JumlahPegawai` untuk mengganti nama kolom hasil `COUNT(NIP)` menjadi jumlah pegawai
- `SUM(Gaji)` untuk menjumlah data yang ada pada kolom yang dipilih. Gaji adalah kolom yang dipilih
- `AS TotalGaji` untuk mengganti nama kolom hasil `SUM(Gaji)` menjadi total gaji
- `AVG(Gaji)` untuk menghitung rata-ratanya suatu data dalam kolom yang dipilih. Gaji adalah nama kolom yang dipilih untuk dihitung
-  `AS RataGaji` untuk mengganti nama kolom hasil `AVG(Gaji)` menjadi rata gaji
- `MAX(Gaji)` untuk menampilkan nilai maksimum atau terbesar/tertinggi dari suatu data dalam kolom yang dipilih. `Gaji` adalah nama kolom yang dipilih
- `AS GajiMaks` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi GajiMaks untuk sementara
- `AS GajiMin` untuk mengganti nama dari kolom hasil `MIN(Gaji)` menjadi GajiMin untuk sementara
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.

Hasil query ini menunjukkan:
- Jumlah pegawai: 9
- Total gaji seluruh pegawai: Rp 30.575.000
- Rata-rata gaji pegawai: Rp 3.397.222,22
- Gaji terbesar: Rp 6.250.000
- Gaji terkecil: Rp 1.725.000

17. SELECT COUNT, FROM, WHERE, GROUP BY, HAVING
```sql
SELECT COUNT(NIP) AS JumlahPegawai, 
       SUM(Gaji) AS TotalGaji,
       AVG(Gaji) AS RataGaji,
       MAX(Gaji) AS GajiMaks,
       MIN(Gaji) AS Gajimin
FROM pegawai
WHERE Jabatan = 'Staf' OR Jabatan = 'Sales'  
GROUP BY NoCab
HAVING SUM(Gaji) <= 2600000;
```
![](asset/22.jpg)
- `SELECT` untuk memilih kolom apa saja yang ingin dipilih
- `COUNT(NIP)` untuk menghitung jumlah barisan data yang ada pada kolam yang dipilih
- `AS JumlahPegawai` untuk mengganti nama kolom hasil `COUNT(NIP)` menjadi jumlah pegawai
- `SUM(Gaji)` untuk menjumlah data yang ada pada kolom yang dipilih. Gaji adalah kolom yang dipilih
- `AS TotalGaji` untuk mengganti nama kolom hasil `SUM(Gaji)` menjadi total gaji
- `AVG(Gaji)` untuk menghitung rata-ratanya suatu data dalam kolom yang dipilih. Gaji adalah nama kolom yang dipilih untuk dihitung
-  `AS RataGaji` untuk mengganti nama kolom hasil `AVG(Gaji)` menjadi rata gaji
- `MAX(Gaji)` untuk menampilkan nilai maksimum atau terbesar/tertinggi dari suatu data dalam kolom yang dipilih. `Gaji` adalah nama kolom yang dipilih
- `AS GajiMaks` untuk mengganti nama dari kolom hasil `MAX(Gaji)` menjadi GajiMaks untuk sementara
- `MIN(Gaji)` untuk menampilkan nilai minimum dari suatu data dalam kolom yang dipilih. Gaji adalah nama kolom yang dipilih
- `AS GajiMin` untuk mengganti nama dari kolom hasil `MIN(Gaji)` menjadi GajiMin untuk sementara
- `FROM pegawai` Ini menunjukkan bahwa query ini yang akan dijalankan pada tabel `pegawai` Ini menunjukkan bahwa query ini akan dijalankan pada tabel `pegawai`.
- `WHERE` kondisi yang harus dipenuhi oleh suatu kolom data agar bisa di tampilkan
- `Jabatan = 'Staf' OR Jabatan = 'Sales'` kondisi dari `WHERE` Jadi hanya jabatan staf atau jabatan sales, hanya salah satunya saja yang harus dipenuhi agar bisa tampil. `OR` hanya salah satu kondis yang harus dipenuhi
- `GROUP BY` untuk ngelompokkan data berdasarkan nilai data yang telah di tentukan pada kolom yang dipilih 
- `NoCab`adalah nama kolom yang ingin ditampilkan.
- `HAVING` kondisi yang harus dipenuhi oleh suatu kelompok data
- `SUM(Gaji) <= 2.600000` kondisi dari `HAVING` Hanya data yang yang hasil jumlahan gajinya kurang dari atau sama dengan 2.600000 yang bisa tampil.

Hasil query ini menunjukkan bahwa ada 2 cabang (NoCab) yang memiliki total gaji pegawai 'Staf' atau 'Sales' kurang dari atau sama dengan Rp 2.600.000, dengan rincian:
 Cabang 1:
- Jumlah pegawai: 1
- Total gaji: Rp 2.500.000
- Gaji rata-rata: Rp 2.500.000
- Gaji terbesar: Rp 2.500.000
- Gaji terkecil: Rp 2.500.000
 Cabang 2:
- Jumlah pegawai: 1
- Total gaji: Rp 1.725.000
- Gaji rata-rata: Rp 1.725.000
- Gaji terbesar: Rp 1.725.000
- Gaji terkecil: Rp 1.725.000

