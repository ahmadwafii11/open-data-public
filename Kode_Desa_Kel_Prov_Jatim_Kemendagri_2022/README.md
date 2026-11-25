# Dataset Kode Wilayah Administrasi Desa & Kelurahan - Provinsi Jawa Timur (Kepmendagri No. 100.1.1-6117 Tahun 2022)

Kumpulan data (*dataset*) referensi kode dan nama wilayah administrasi pemerintahan dari tingkat Provinsi hingga Desa/Kelurahan di **Provinsi Jawa Timur**, merujuk pada **Keputusan Menteri Dalam Negeri Nomor 100.1.1-6117 Tahun 2022**.

---

## 📊 Ringkasan Statistik Wilayah (Jawa Timur)

Cakupan wilayah Provinsi Jawa Timur (Kode Provinsi: `35`) berdasarkan regulasi tersebut meliputi:
* **Kabupaten:** 29
* **Kota:** 9
* **Kecamatan:** 666
* **Kelurahan:** 773
* **Desa:** 7.721
* **Total Desa & Kelurahan:** 8.494
* **Luas Wilayah & Pulau:** 48.036,840 km² dengan 512 pulau.

---

### Format Kode Wilayah Kemendagri
* `35` : Provinsi Jawa Timur
* `35.XX` : Kabupaten/Kota
* `35.XX.XX` : Kecamatan
* `35.XX.XX.1XXX` : Kelurahan (diawali angka `1`)
* `35.XX.XX.2XXX` : Desa (diawali angka `2`)

*Kolom utama dalam dataset meliputi:* `kode_wilayah`, `kode_wilayah_raw`, `kode_provinsi` (`35`), `nama_provinsi` (JAWA TIMUR), `kode_kabkota`, `nama_kabkota`, `kode_kecamatan`, `nama_kecamatan`, `jenis_wilayah` (Desa/Kelurahan), dan `nama_desakel`.

---

## 💡 Contoh Penggunaan

### Python (Pandas)
```python
import pandas as pd

# Membaca file JSON dengan memastikan kolom kode_kabkota tetap dibaca sebagai string
df = pd.read_json("jatim_wilayah.json", dtype={"kode_kabkota": str})

# Memfilter data khusus untuk Kabupaten Pacitan (35.01)
pacitan = df[df["kode_kabkota"] == "35.01"]

print(pacitan.head())
```

### SQL
```sql
SELECT kode_wilayah, nama_desakel, nama_kecamatan, nama_kabkota
FROM jatim_desa_kelurahan
WHERE jenis_wilayah = 'Desa' AND nama_kabkota = 'KAB. PACITAN';
```

---

## 📜 Sumber Hukum & Lisensi
* **Regulasi:** Keputusan Menteri Dalam Negeri No. 100.1.1-6117 Tahun 2022, dapat diakses melalui portal [Dinas PMD Jatim](https://sibermatadesa.dpmd.jatimprov.go.id/uploads/regulasi/242-Kepmendagri%20100.1.1-6117%20Tahun%202022_Kode%20Desa%20Kel%20JATIM_9%20November%202022.pdf) dan [Open Data Jatim](https://opendata.jatimprov.go.id/dataset/jumlah-desakelurahan-yang-melakukan-entryupdate-profil-desakelurahan-menurut-kabupatenkota-di-jawa-timur).
* **Catatan:** Simpan kolom kode sebagai `string`/`VARCHAR` agar angka nol di depan tidak hilang.
* **Lisensi:** Dirilis menggunakan lisensi [CC BY 1.0](https://github.com/ahmadwafii11/open-data-public/blob/main/LICENSE).