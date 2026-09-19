# Sistem Manajemen Ruang Meeting

## 👤 Identitas Mahasiswa

- **Nama** : Syavira Firnanda Prawiro
- **NIM**  : *2509116072*

---

## 📌 Penjelasan Studi Kasus

Program ini adalah **Sistem Manajemen Ruang Meeting** yang dibuat menggunakan bahasa Java di NetBeans. Program ini digunakan untuk mengelola data ruang meeting beserta jadwal penggunaannya dalam sebuah perusahaan/organisasi, agar tidak terjadi bentrok penggunaan ruangan pada waktu yang sama.

Fitur utama program:

1. **Kelola Ruang Meeting** — tambah, lihat, dan hapus data ruang (nama, kapasitas, fasilitas).
2. **Kelola Pengguna** — tambah, lihat, dan hapus data pengguna (nama, departemen) yang akan memakai ruang.
3. **Kelola Booking** — mencatat penggunaan ruang oleh pengguna tertentu pada tanggal dan jam tertentu.
4. **Tampilkan Jadwal Meeting** — menampilkan seluruh jadwal booking yang sudah dibuat.

5. ## Struktur Class

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

Poin pentingnya:

- `extends` → menandakan `RuangKecil`/`RuangBesar` adalah turunan dari `Ruangan`
- `super(...)` → memanggil constructor milik superclass
- `jenisRuang()` → method abstract yang diisi berbeda di tiap subclass

Saat pengguna menambah ruang baru, program otomatis memilih subclass yang tepat berdasarkan kapasitas yang diinput.

## Cara Menjalankan

1. Buka project di NetBeans
2. Klik kanan file `ManajemenRuangMeeting.java` → **Run File**
3. Ikuti menu yang muncul di layar

## Screenshot Program

Tempatkan gambar di sini:

![Tampilan program](screenshots/tampilan-program.png)

**Cara memasangnya:**

1. Buat folder bernama `screenshots` di root repository (sejajar dengan folder `src`)
2. Simpan screenshot hasil running program ke folder itu dengan nama `tampilan-program.png`
3. Nama file di langkah 2 harus sama persis dengan nama file pada baris gambar di atas

Kalau mau menambah screenshot lain (misalnya per-menu), tinggal tambah baris baru dengan pola yang sama:

```markdown
![Menu Kelola Ruang](screenshots/menu-ruang.png)
![Menu Kelola Booking](screenshots/menu-booking.png)
```
