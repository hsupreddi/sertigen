# CERTIFICATE GENERATOR, by BKPSDM Kabupaten Dairi

Aplikasi web satu file (`index.html`) untuk membuat sertifikat dalam jumlah banyak: ambil data peserta dari Google Sheet atau CSV, atur desain dan penomoran, lalu unduh hasilnya sebagai PDF. Semua proses berjalan di peramban (browser) pengguna; tidak ada server dan tidak ada data peserta yang diunggah ke mana pun.

**Alamat aplikasi** (setelah GitHub Pages diaktifkan): https://hsupreddi.github.io/sertigen/

## Fitur

- **Data peserta** dari tiga sumber: tautan Google Sheet, unggah file CSV, atau tempel langsung dari Google Sheet / Excel.
- **Pilih peserta** yang akan dicetak lewat kotak centang, dengan kolom pencarian nama.
- **Desain sertifikat**: beberapa tema bingkai, isian teks (instansi, nama kegiatan, jam pelajaran, tanggal, penyelenggara, penandatangan), dan unggahan logo, tanda tangan, serta stempel.
- **Nomor surat otomatis** dengan format yang bisa diatur (lihat bagian di bawah).
- **Mode TTE** (tanda tangan elektronik): tanda tangan basah dan stempel tidak dicetak, diganti blok "Ditandatangani secara elektronik oleh : ...".
- **Pratinjau langsung** per peserta; nama dan NIP bisa dikoreksi di pratinjau tanpa mengubah data sumber.
- **Ekspor PDF**: ZIP berisi satu PDF per peserta, atau satu PDF gabungan.

## Cara memakai

1. **Data Peserta**
   - *Google Sheet*: tempel tautan Sheet, lalu klik **Ambil data**. Atur berbagi Sheet ke "Siapa saja yang memiliki link - Pelihat".
   - *CSV*: klik **Unggah file CSV**.
   - *Tempel*: salin tabel dari Google Sheet / Excel (baris pertama berisi judul kolom), tempel ke kotak, lalu klik **Muat tempelan**.
   - Pilih kolom yang berisi nama dan kolom NIP, lalu centang peserta yang akan dicetak.
2. **Desain Sertifikat**: pilih tema, isi data kegiatan dan penandatangan, atur format nomor, dan aktifkan Mode TTE bila perlu.
3. **Generate**: periksa pratinjau tiap peserta, lalu klik **Unduh ZIP** atau **Unduh 1 PDF gabungan**.

## Penomoran otomatis

Tulis format nomor dengan `XXXX` di bagian nomor urut, lalu isi **Nomor urut pertama**.

| Isian | Contoh |
|---|---|
| Format nomor surat | `800.1.12.8/XXXX/BKPSDM/XI/2026` |
| Nomor urut pertama | `1024` |

Hasil untuk 100 peserta terpilih:

```
NOMOR : 800.1.12.8/1024/BKPSDM/XI/2026
NOMOR : 800.1.12.8/1025/BKPSDM/XI/2026
...
NOMOR : 800.1.12.8/1123/BKPSDM/XI/2026
```

Catatan:
- Jumlah sertifikat mengikuti jumlah peserta yang dicentang.
- Nomor dihitung berurutan hanya untuk peserta yang dipilih, jadi tidak ada nomor yang terlewat.
- Angka tidak diberi nol di depan (nomor 1 ditulis `1`, bukan `0001`).
- Awalan "NOMOR :" ditambahkan otomatis; tidak perlu ditulis di format.

## Mode TTE

Centang **Mode TTE** di menu Desain Sertifikat. Blok penandatangan berubah menjadi:

```
Sidikalang, 6 November 2026
Ditandatangani secara elektronik oleh :
KEPALA BADAN KEPEGAWAIAN DAN
PENGEMBANGAN SUMBER DAYA MANUSIA
KABUPATEN DAIRI

YON HENRIK, AP, M.Si
Pembina Utama Muda
NIP. 197310191993111001
```

> Tulisan ini hanya keterangan teks pada sertifikat, **bukan** tanda tangan elektronik yang sah. Jika instansi memakai TTE resmi (misalnya BSrE), PDF hasil generate tetap perlu ditandatangani melalui aplikasi atau layanan TTE tersebut.

## Persyaratan

- Peramban modern (Chrome, Edge, atau Firefox versi terbaru).
- **Koneksi internet**: font (Google Fonts) dan library PDF/ZIP (html2canvas, jsPDF, JSZip) dimuat dari internet.
- Mengambil data langsung dari Google Sheet hanya berjalan bila aplikasi dibuka dari alamat web (misalnya GitHub Pages) atau server sendiri, bukan dari file yang dibuka langsung di komputer. Unggah CSV dan tempel data tetap bisa dipakai kapan saja.

## Penyimpanan pengaturan

Isian desain, format nomor, nomor awal, dan pilihan Mode TTE disimpan di peramban masing-masing pengguna (localStorage). Pengaturan tidak berpindah antar komputer atau peramban, dan bisa hilang bila data peramban dihapus.

## Memasang di GitHub Pages

1. Pastikan file aplikasi bernama `index.html` di akar repository.
2. Repository harus **Public** (paket gratis GitHub hanya mendukung Pages untuk repository publik).
3. Buka **Settings > Pages**, pada **Build and deployment** pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu **Save**.
4. Tunggu 1-2 menit; alamat situs muncul di halaman yang sama.

Untuk memperbarui aplikasi, unggah ulang `index.html` dengan nama yang sama.

## Privasi

Repository publik dapat dilihat siapa saja. Data peserta tidak disimpan di repository ini karena dibaca dari Google Sheet atau CSV di peramban pengguna. Sebelum dipublikasikan, pastikan isian bawaan di dalam file (misalnya nama dan NIP penandatangan) memang boleh dilihat umum.

## Pengembang

BKPSDM Kabupaten Dairi.
