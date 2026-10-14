# KAMUS DATA & CHEATSHEET MASTER DATA (ERP_BENETO)
## PT Bento Kreasi Nusantara

Gunakan lembar ringkasan ini sebagai referensi cepat saat input data manual atau validasi data di ERPNext.

---

### 1. Item Groups
| Item Group | Parent Group | Keterangan |
|---|---|---|
| **Bahan Baku** | All Item Groups | Daging ayam, beras, tepung, telur, minyak, bumbu, sayuran |
| **Kemasan** | All Item Groups | Kotak bento plastik sekat, sumpit, sendok, master kardus |
| **Produk Setengah Jadi** | All Item Groups | Komponen olahan perantara (WIP) |
| **Produk Jadi** | All Item Groups | Paket bento siap saji untuk konsumen |

---

### 2. Warehouses (Gudang)
| Nama Gudang | Singkatan | Parent Warehouse | Fungsi |
|---|---|---|---|
| **Gudang Bahan Baku - BM** | RM-WH | All Warehouses | Tempat penyimpanan bahan makanan mentah & bumbu |
| **Gudang Kemasan - BM** | PKG-WH | All Warehouses | Tempat penyimpanan kotak mika, sumpit, kardus |
| **Gudang Produksi WIP - BM** | WIP-WH | All Warehouses | Area dapur pengolahan saat proses memasak |
| **Gudang Barang Jadi - BM** | FG-WH | All Warehouses | Area bento siap saji sebelum dikirim ke pelanggan |

---

### 3. Daftar Lengkap Item & Harga Standar
| Kode Item | Nama Item | Grup | UOM | Harga Beli | Harga Jual | Gudang Default |
|---|---|---|---|---|---|---|
| `RM-AYM-001` | Daging Ayam Fillet Segar | Bahan Baku | Kg | Rp 42.000 | - | Gudang Bahan Baku |
| `RM-BRS-001` | Beras Pulen Japonica | Bahan Baku | Kg | Rp 16.000 | - | Gudang Bahan Baku |
| `RM-TPG-001` | Tepung Roti Panko Katsu | Bahan Baku | Kg | Rp 24.000 | - | Gudang Bahan Baku |
| `RM-TLR-001` | Telur Ayam Horn | Bahan Baku | Kg | Rp 28.000 | - | Gudang Bahan Baku |
| `RM-MYK-001` | Minyak Goreng Sawit | Bahan Baku | Liter | Rp 18.000 | - | Gudang Bahan Baku |
| `RM-SAU-001` | Saus Katsu & Teriyaki | Bahan Baku | Liter | Rp 35.000 | - | Gudang Bahan Baku |
| `RM-SYR-001` | Sayur Campur Kol & Wortel | Bahan Baku | Kg | Rp 15.000 | - | Gudang Bahan Baku |
| `RM-MAY-001` | Saus Mayones Dressing | Bahan Baku | Liter | Rp 32.000 | - | Gudang Bahan Baku |
| `RM-BMB-001` | Racikan Bumbu Marinasi | Bahan Baku | Kg | Rp 30.000 | - | Gudang Bahan Baku |
| `PKG-BOX-001` | Bento Box Sekat 4 + Tutup | Kemasan | Pcs | Rp 1.800 | - | Gudang Kemasan |
| `PKG-STK-001` | Sumpit Bambu Higienis | Kemasan | Pcs | Rp 300 | - | Gudang Kemasan |
| `PKG-SDK-001` | Sendok Plastik Bening | Kemasan | Pcs | Rp 250 | - | Gudang Kemasan |
| `PKG-KRT-001` | Kardus Master Box (Isi 25)| Kemasan | Pcs | Rp 5.000 | - | Gudang Kemasan |
| `WIP-KTS-001` | Fillet Ayam Katsu Siap Goreng | Setengah Jadi| Pcs | Rp 6.500 | - | Gudang Produksi WIP |
| `FG-BNT-001` | Bento Box Paket Chicken Katsu | Produk Jadi | Box | Rp 16.500* | Rp 28.000 | Gudang Barang Jadi |
| `FG-BNT-002` | Bento Box Paket Chicken Teriyaki| Produk Jadi | Box | Rp 17.500* | Rp 30.000 | Gudang Barang Jadi |

*\*Estimasi Harga Pokok Produksi (HPP / Valuation Rate).*

---

### 4. Workstations & Operations
| Kode Stasiun | Nama Stasiun | Biaya/Jam | Operasi Terkait | Waktu / Box |
|---|---|---|---|---|
| `WS-PREP` | Dapur Persiapan | Rp 25.000 / Jam | `OP-PREPARATION` | 3 menit |
| `WS-COOK` | Dapur Masak & Goreng | Rp 35.000 / Jam | `OP-COOKING` | 4 menit |
| `WS-PACK` | Meja Perakitan & Packing | Rp 20.000 / Jam | `OP-PACKAGING` | 2 menit |

---

### 5. Suppliers & Customers
| Entitas | Nama Relasi | Tipe | Kontak / Keterangan |
|---|---|---|---|
| **Supplier** | PT Pangan Berkah Utama | Company | Supplier Utama Daging Ayam & Beras |
| **Supplier** | CV Sumber Kemasan Indah | Company | Supplier Kotak Bento, Mika, Kardus |
| **Supplier** | UD Segar Barokah Sayur | Individual | Supplier Sayur Kol & Wortel Segar |
| **Supplier** | Toko Bumbu Nusantara | Individual | Supplier Saus, Bumbu Marinasi, Minyak |
| **Customer** | Panitia Seminar Nasional Undip | Individual/Org| Pemesan Event Katering Kampus |
| **Customer** | PT Solusi Digital Semesta | Company | Langganan Makan Siang Karyawan |
| **Customer** | RS Sehat Sentosa Katering | Company | Rekanan Pasokan Diet Normal RS |
| **Customer** | Toko Retail Bento Express | Company | Outlet Distribusi Bento Harian |
