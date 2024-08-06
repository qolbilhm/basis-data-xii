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

![github](asset/1.JPG)
(Hasil di PhpMYAdmin)
![github](asset/3.JPG)

**Analisis Query :**  
- `desc pegawai ;` Kueri ini digunakan untuk menampilkan struktur tabel pegawai, 
termasuk nama kolom, tipe data, batasan null/bukan null, batasan kunci, nilai default, dan
informasi tambahan.
- `NIP` Bidang ini adalah tipe data integer dan bertindak sebagai
kunci utama untuk tabel. Bidang ini tidak boleh null, yang berarti bahwa setiap baris dalam
tabel harus memiliki nilai NIP yang unik.
- `NDep` Ini adalah kolom varchar yang menyimpan nama departemen.
Kolom ini tidak boleh null, yang berarti bahwa setiap karyawan harus dikaitkan dengan
suatu departemen.
- `NBlk`  Ini adalah kolom varchar yang menyimpan nama blok. Kolom ini tidak
boleh null, yang berarti bahwa setiap karyawan harus dikaitkan dengan blok.
- `JK`  Ini adalah kolom enum yang menyimpan jenis kelamin karyawan,
dengan kemungkinan nilai 'L' (Laki-laki) atau 'P' (Perempuan). Kolom ini tidak boleh null,
yang berarti bahwa setiap karyawan harus memiliki jenis kelamin yang ditentukan.
- `Alamat` Ini adalah kolom teks yang menyimpan alamat karyawan. Kolom ini tidak boleh
kosong, yang berarti setiap karyawan harus memiliki alamat.
- `Telp (Telepon)` Ini adalah kolom varchar yang menyimpan nomor telepon karyawan.
Kolom ini tidak boleh kosong dan harus unik, yang berarti setiap karyawan harus memiliki
nomor telepon yang unik.
- `Jabatan` Ini adalah kolom enum yang menyimpan posisi pekerjaan karyawan, dengan kemungkinan nilai 'Manajer', 'Penjualan', atau 'Staf'. Kolom ini tidak boleh kosong, yang
berarti bahwa setiap karyawan harus memiliki posisi pekerjaan yang ditentukan.
- `Gaji` Ini adalah kolom bigint yang menyimpan gaji karyawan. Kolom ini tidak
boleh null, yang berarti setiap karyawan harus memiliki gaji yang ditentukan.
- `NoCab` Ini adalah kolom varchar yang menyimpan nomor cabang. Kolom
ini tidak boleh null dan merupakan bagian dari indeks multikolom, yang berarti bahwa
kombinasi NoCab dan satu atau beberapa kolom lainnya harus unik.

**Kesimpulan Analisis Query:** 
Analisis ini memberikan contoh tentang bagaimana tabel `pegawai` diatur dan bagaimana data di dalamnya akan disimpan dan dikelola, termasuk kendali integritas data melalui penggunaan kunci utama dan indeks unik.
### Hasil data tabel Pegawai 
![github](asset/2.JPG)
(Hasil di PhpMyAdmin)
![github](asset/4.JPG)

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