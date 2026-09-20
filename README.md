# Sistem Manajemen Ruang Meeting

- **Nama** : Syavira Firnanda Prawiro
- **NIM**  : 2509116072

---

## Penjelasan Studi Kasus

Program ini adalah **Sistem Manajemen Ruang Meeting** yang digunakan untuk mengelola data ruang meeting beserta jadwal penggunaannya dalam sebuah perusahaan/organisasi, agar tidak terjadi bentrok penggunaan ruangan pada waktu yang sama.

Fitur utama program:

1. **Kelola Ruang Meeting** — tambah, lihat, dan hapus data ruang yaitu nama, kapasitas, dan fasilitas.
2. **Kelola Pengguna** — tambah, lihat, dan hapus data pengguna yaitu nama dan departemen yang akan memakai ruang.
3. **Kelola Booking** — mencatat penggunaan ruang oleh pengguna tertentu pada tanggal dan jam tertentu.
4. **Tampilkan Jadwal Meeting** — menampilkan seluruh jadwal booking yang sudah dibuat.
<br>

## Struktur Class

```
Ruangan  (abstract)
 ├── RuangKecil   → dipakai jika kapasitas ≤ 15 orang
 └── RuangBesar   → dipakai jika kapasitas  > 15 orang

Pengguna

Booking
 ├── berisi 1 objek Ruangan
 └── berisi 1 objek Pengguna

ManajemenRuangMeeting   → class utama, tempat method main() dan menu program
```

| Class | Fungsi |
|---|---|
| `Ruangan` | Superclass, menyimpan data umum ruang: nama, kapasitas, fasilitas |
| `RuangKecil` / `RuangBesar` | Subclass dari `Ruangan`, membedakan kategori ruang |
| `Pengguna` | Menyimpan data orang yang melakukan booking |
| `Booking` | Menghubungkan `Ruangan` dan `Pengguna` beserta jadwalnya |
| `ManajemenRuangMeeting` | Menjalankan menu dan alur program |
<br>

## Penerapan Inheritance

`RuangKecil` dan `RuangBesar` merupakan turunan (subclass) dari `Ruangan` (superclass). Keduanya otomatis mendapat atribut `namaRuang`, `kapasitas`, dan `fasilitas` tanpa perlu menuliskannya ulang.

```java
// Superclass
abstract class Ruangan {
    String namaRuang;
    int kapasitas;
    String fasilitas;

    Ruangan(String namaRuang, int kapasitas, String fasilitas) {
        this.namaRuang = namaRuang;
        this.kapasitas = kapasitas;
        this.fasilitas = fasilitas;
    }

    abstract String jenisRuang(); // wajib diisi ulang oleh subclass
}

// Subclass
class RuangKecil extends Ruangan {
    RuangKecil(String namaRuang, int kapasitas, String fasilitas) {
        super(namaRuang, kapasitas, fasilitas); // panggil constructor superclass
    }

    String jenisRuang() {
        return "Ruang Kecil";
    }
}

class RuangBesar extends Ruangan {
    RuangBesar(String namaRuang, int kapasitas, String fasilitas) {
        super(namaRuang, kapasitas, fasilitas);
    }

    String jenisRuang() {
        return "Ruang Besar";
    }
}
```

Penjelasan kode:

- `extends` berfungsi untuk menandakan `RuangKecil`/`RuangBesar` adalah turunan dari `Ruangan`
- `super` berfungsi untuk memanggil constructor milik superclass
- `jenisRuang()` adalah method abstract yang diisi berbeda di tiap subclass

Saat pengguna menambah ruang baru, program otomatis memilih subclass yang tepat berdasarkan kapasitas yang diinput.

## Alur Program

### 1. Kelola Ruang Meeting
<img width="500" alt="Screenshot 2026-09-20 181452" src="https://github.com/user-attachments/assets/18656a73-4edc-4b2a-a316-6fefd58324fd" />
<br>
<img width="700" alt="Screenshot 2026-09-20 181642" src="https://github.com/user-attachments/assets/a08b016e-0ac2-4e4c-a20a-12ea8e62789a" />
<br>
Pada tahap awal, pengguna memilih menu Kelola Ruang Meeting lalu memilih opsi untuk menambah ruangan baru. Pengguna diminta menginput nama ruang, kapasitas, dan fasilitas. Sistem kemudian memproses kapasitas yang diinput; jika kapasitasnya lebih dari 15 orang, sistem secara otomatis mengategorikan ruangan tersebut sebagai Ruang Besar dan menyimpannya ke daftar ruangan.

### 2. Kelola Pengguna 
<img width="500" alt="Screenshot 2026-09-20 181759" src="https://github.com/user-attachments/assets/1da1591e-db4d-4cec-ab1f-9153ad8eff2d" />
<br>
<img width="400" alt="Screenshot 2026-09-20 181902" src="https://github.com/user-attachments/assets/9392a83e-8d6f-4073-81df-adb322eb41ef" />
<br>
Selanjutnya, pengguna masuk ke menu Kelola Pengguna untuk mendaftarkan identitas orang yang akan melakukan pemesanan. Pengguna menginputkan nama lengkap serta nama departemennya. Data ini kemudian disimpan oleh sistem sebagai objek pengguna baru yang siap dipilih saat proses booking ruangan nanti.

### 3. Kelola Booking
<img width="600" alt="Screenshot 2026-09-20 182059" src="https://github.com/user-attachments/assets/b82d45ac-4079-4b8f-9f52-1b2552d9d87b" />
<br>
<img width="600" alt="Screenshot 2026-09-20 182125" src="https://github.com/user-attachments/assets/c6e3a729-8389-4929-a846-f2fe24a5b045" />
<br>
Setelah data ruangan dan pengguna tersedia, pengguna memilih menu Kelola Booking untuk membuat jadwal meeting baru. Sistem akan menampilkan daftar ruangan dan daftar pengguna yang sudah diinput sebelumnya agar pengguna bisa memilih nomornya. Setelah memilih ruangan dan pemesan, pengguna menginputkan tanggal, jam pelaksanaan, serta keperluan meeting, lalu sistem akan menggabungkan seluruh informasi tersebut menjadi satu data booking.

### 4. Menampilkan Jadwal Meeting
<img width="700" alt="Screenshot 2026-09-20 182215" src="https://github.com/user-attachments/assets/edfaa08e-7275-451e-a82c-36b68f7ce8b8" />
<br>
Pengguna dapat memilih menu Tampilkan Jadwal Meeting untuk melihat seluruh transaksi pemesanan yang telah berhasil dibuat. Sistem akan mencetak daftar jadwal secara rapi dengan format gabungan yang menampilkan nama ruangan, tanggal, jam, nama pemesan, dan keperluan meeting.

### 5. Mengakhiri Program
<img width="500" alt="Screenshot 2026-09-20 182352" src="https://github.com/user-attachments/assets/69601e38-3c57-4216-bba8-16a266372593" />
<br>
Setelah seluruh aktivitas pengelolaan selesai, pengguna memilih opsi menu Keluar. Sistem kemudian menampilkan pesan penutup "Terima kasih!" dan secara otomatis menghentikan pengulangan menu utama program.

