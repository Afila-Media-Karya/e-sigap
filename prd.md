# PRODUCT REQUIREMENTS DOCUMENT (PRD)
Sistem Integrasi Pengawasan Anggaran Pedesaan (SIGAP)

**STATUS: Draft Sementara**

| | |
| :--- | :--- |
| **Nama Produk** | Sistem Integrasi Pengawasan Anggaran Pedesaan (SIGAP) |
| **Versi Dokumen** | v0.4 |
| **Disusun oleh** | Tim Pengembang |
| **Untuk** | Inspektorat Daerah / Pemerintah Daerah |
| **Tanggal** | 17 Juli 2026 |
| **Dokumen Terkait** | KAK Dan PROBIS UTAMA APLIKASI KOORDINASI CAMAT DAN ITDA UNTUK DESA.pdf |

## 1. Ringkasan Produk (Overview)
Sistem Integrasi Pengawasan Anggaran Pedesaan (SIGAP) adalah sistem informasi terintegrasi untuk memfasilitasi proses perencanaan, penganggaran, pelaksanaan, dan pertanggungjawaban keuangan desa secara berjenjang. Sistem ini menggantikan evaluasi manual untuk mencegah keterlambatan, ketidaksesuaian data, dan penyimpangan penganggaran.

## 2. Tujuan & Sasaran (Goals)
* Meningkatkan akuntabilitas pengelolaan keuangan sesuai Permendagri No. 20/2018 dan fungsi pengawasan Permendagri No. 73/2020.
* Mempercepat proses evaluasi dan menyediakan data *real-time* bagi pengambil kebijakan.
* Mengurangi potensi penyimpangan dan *fraud*.

## 3. Pengguna & Peran (Users & Roles)
Sistem ini menggunakan struktur *Role-Based Access Control* (RBAC) dengan batasan yang ketat:
* **Super Admin** : Mengelola *master data* wilayah, sistem, dan hak akses pengguna secara menyeluruh.
* **Desa** : Membutuhkan kemudahan untuk input dokumen tanpa proses yang rumit.
* **BPD (Badan Permusyawaratan Desa)** : Membutuhkan akses cepat untuk meninjau dan menyetujui dokumen.
* **Kecamatan** : Bertindak sebagai *gatekeeper* administratif yang membutuhkan *checklist* verifikasi yang jelas.
* **TDA (Tim Daerah)** : Membutuhkan *dashboard* rekapitulasi untuk analisis makro.
* **APIP (Inspektorat Daerah)** : Membutuhkan sistem pendeteksi anomali (EWS) untuk investigasi dan audit.

## 4. Ruang Lingkup (Scope)

### 4.1 Termasuk (MVP)
* Modul Manajemen User dengan kontrol akses berbasis peran (RBAC).
* Modul Input Dokumen Desa (RKP, APBDes, LPJ) dan Bukti Dukung.
* Modul Review BPD (Setuju/Tidak Setuju).
* Modul Evaluasi Kecamatan dengan fitur *Checklist* wajib.
* Modul Pengawasan Inspektorat (Early Warning System Dasar) untuk deteksi waktu unggah dan kewajaran nilai anggaran.
* Modul Dashboard Spesifik dengan metrik yang disesuaikan untuk setiap jenis pengguna.
* Modul Laporan Spesifik untuk memfasilitasi pencetakan dan pengunduhan rekapitulasi data.
* Modul Audit Trail untuk merekam seluruh riwayat aksi pengguna.
* Integrasi data awal (bridging) dari Siskeudes.

### 4.2 Di Luar Lingkup Awal / Fase Lanjutan
* Teknologi PWA (Progressive Web App) untuk kapabilitas akses *offline*.
* Ekstraksi teks otomatis dari foto kuitansi menggunakan AI (OCR).
* Portal transparansi data publik (Citizen Dashboard).
* Pemetaan Geospasial (GIS) / Geotagging pembangunan fisik.

## 5. Asumsi & Batasan (Assumptions & Constraints)
* **Asumsi Teknis:** Platform berbasis web, menggunakan basis data relasional (misal: MySQL/PostgreSQL). Arsitektur direkomendasikan mendukung kapabilitas PWA untuk *offline-sync* di masa depan.
* **Batasan Jaringan:** Terdapat desa tertentu yang jaringan internetnya belum stabil, sehingga sistem harus dirancang ringan dan responsif.
* **Batasan Literasi:** Terdapat keterbatasan literasi SDM di tingkat pengguna, sehingga UI/UX dirancang sesederhana mungkin dengan metode langkah demi langkah (*wizard*).

## 6. Kebutuhan Fungsional (Functional Requirements)

### 6.1 Modul Manajemen User (USER)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| USER-1 | Sistem harus memungkinkan CRUD data pengguna beserta penetapan *role* (Super Admin, Desa, BPD, Camat, TDA, APIP). | Wajib |
| USER-2 | Sistem harus mengelola referensi *master data* daftar desa dan kecamatan. | Wajib |

### 6.2 Modul Input Dokumen Desa (DESA)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| DESA-1 | Sistem menyediakan *form* unggah khusus bagi operator desa untuk menginput dokumen RKP dan APBDes, serta menyimpannya sebagai *Draft* sebelum dikirim. | Wajib |
| DESA-2 | Sistem menyediakan sarana unggah dokumen LPJ beserta *file* Bukti Dukung (kuitansi, foto kegiatan, dll). | Wajib |
| DESA-3 | Sistem menampilkan *timeline* status dokumen (Draft, Menunggu BPD, Di Kecamatan, Disetujui/Dikembalikan) dilengkapi notifikasi dan catatan alasan penolakan. | Wajib |
| DESA-4 | Sistem menerapkan validasi *backend* wajib untuk memastikan format file (PDF/JPG) valid guna mencegah manipulasi, serta memunculkan *warning message* jika *upload* dilakukan mendekati tenggat waktu. | Wajib |

### 6.3 Modul Review BPD (BPDD)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| BPDD-1 | Sistem menyediakan antarmuka *Document Viewer* terintegrasi agar BPD tidak perlu mengunduh file satu per satu saat meninjau dokumen. | Penting |
| BPDD-2 | Sistem menyediakan 2 tombol aksi ("Setuju" / "Tidak Setuju") sesuai Permendagri 73 2020. Jika BPD memilih "Tidak Setuju", sistem wajib memunculkan *form pop-up mandatory* untuk mengisi catatan perbaikan. | Wajib |

### 6.4 Modul Evaluasi Kecamatan (KECM)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| KECM-1 | Sistem menampilkan tabel *inbox* dokumen masuk dari desa (yang telah disetujui BPD) dengan filter desa dan urutan tanggal masuk. | Wajib |
| KECM-2 | Sistem menyediakan fitur *Checklist* Wajib (Verifikasi Administrasi & LPJ) dan akan menonaktifkan (*disable*) tombol persetujuan akhir jika semua poin belum diverifikasi. | Wajib |
| KECM-3 | Sistem memfasilitasi pengembalian dokumen ke Desa jika tidak lengkap beserta *mandatory field* alasan pengembalian, atau menyetujuinya jika valid. | Wajib |

### 6.5 Modul Pengawasan Inspektorat / APIP (APIP)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| APIP-1 | Sistem memberikan peringatan otomatis (*Flagging* Nilai & Waktu) jika nilai anggaran tidak wajar atau dokumen diunggah mendekati batas waktu. | Wajib |
| APIP-2 | Sistem memberikan peringatan otomatis (*Flagging* Perilaku) jika ada pola persetujuan kecamatan yang terlalu cepat, atau revisi desa yang berulang tanpa alasan jelas. | Wajib |
| APIP-3 | Sistem melakukan kalkulasi deviasi otomatis atas selisih pencairan (SPP) dan realisasi pelaksanaan, serta memunculkan notifikasi jika melebihi ambang batas. | Wajib |
| APIP-4 | Sistem menyediakan fitur "Tandai Dokumen" yang memungkinkan APIP mengunci alur dokumen tertentu selama masa Investigasi atau Audit. | Wajib |

### 6.6 Modul Dashboard & Analisis Daerah (DAUD)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| DAUD-1 | Sistem menampilkan *dashboard* analitik untuk TDA yang merangkum persentase dokumen yang disetujui, diproses, atau dikembalikan per kecamatan. | Wajib |
| DAUD-2 | Sistem menyediakan Laporan SLA (*Service Level Agreement*) rata-rata waktu yang dihabiskan kecamatan untuk memproses satu dokumen. | Wajib |
| DAUD-3 | Sistem menyediakan tombol "Kirim ke APIP" bagi TDA untuk meneruskan rekapitulasi data evaluasi yang sudah dianalisis. | Wajib |

### 6.7 Modul Dashboard Spesifik Pengguna Lain (DASH)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| DASH-1 | **Dasbor Desa:** Menampilkan Total Anggaran Desa, Total Realisasi (SPP), Total SPJ (LPJ yang diunggah), dan *shortcut* status dokumen. | Wajib |
| DASH-2 | **Dasbor BPD:** Menampilkan Total Anggaran yang direview, persentase APBDes terserap, dan matriks status evaluasi. | Wajib |
| DASH-3 | **Dasbor Kecamatan:** Menampilkan metrik Total Desa di bawah kecamatan, persentase penyelesaian, jumlah antrian berjalan, dan rekap dokumen dikembalikan. | Wajib |
| DASH-4 | **Dasbor APIP:** Berfokus pada EWS, menampilkan Total Indikasi Fraud, grafik deviasi dana tertinggi, dan laporan desa mendekati tenggat waktu akhir. | Wajib |

### 6.8 Modul Audit Trail (AUDT)
| ID | Kebutuhan Fungsional | Prioritas |
| :--- | :--- | :--- |
| AUDT-1 | Sistem wajib merekam seluruh riwayat dokumen (*Audit Trail*), mencakup riwayat *upload*, perubahan data, waktu persetujuan, dan *IP address* pengakses untuk mencegah kolusi. | Wajib |
| AUDT-2 | Sistem memberikan akses tak terbatas bagi APIP ke log *Audit Trail* untuk mendukung fungsi Pembinaan & Pengawasan. | Wajib |

## 7. Alur Pengguna Utama & User Stories (Key User Flows)

### Epic 1: Manajemen Evaluasi Berjenjang
* **Desa:** Sebagai Operator Desa, saya menginput dokumen RKP dan APBDes beserta bukti dukung ke dalam sistem agar tercatat secara digital. Dokumen disimpan sebagai *Draft* lalu dikirimkan ke BPD. 
* **BPD:** Sebagai Anggota BPD, saya meninjau dokumen menggunakan *Document Viewer* terintegrasi. Saya memberikan keputusan "Setuju" agar dokumen diteruskan ke Kecamatan, atau "Tidak Setuju" disertai catatan revisi agar Desa tahu apa yang harus diperbaiki.

### Epic 2: Verifikasi & Kontrol Kualitas
* **Kecamatan:** Sebagai Verifikator Kecamatan, saya menerima dokumen di tabel *inbox*. Saya diwajibkan memeriksa secara teliti dan mencentang *Checklist* Verifikasi Administrasi & LPJ agar *review* tidak sekadar formalitas.
* **Keputusan Akhir:** Jika dokumen lengkap, saya menekan tombol "Setujui" yang akan merekam *Audit Trail* persetujuan. Jika tidak, saya memilih opsi "Kembalikan ke Desa" dengan mengisi alasan wajib.

### Epic 3: Pemantauan & Pengawasan (Anti-Fraud)
* **TDA:** Sebagai Tim Daerah, saya memantau *dashboard* persentase evaluasi per kecamatan dan laporan SLA kecepatan *review*. Setelah analisis selesai, saya menekan tombol "Kirim ke APIP" untuk meneruskan rekapitulasi.
* **APIP:** Sebagai Auditor APIP, saya secara pasif menerima notifikasi *flagging* jika ada perilaku anomali (waktu unggah mepet, persetujuan terlalu cepat, deviasi pencairan SPP vs realisasi fisik). Jika ditemukan indikasi kecurangan, saya mengakses riwayat penuh *Audit Trail* dan menggunakan fitur "Tandai Dokumen" untuk mengunci data selama masa investigasi.

## 8. Model Data (High-Level)
| Entitas | Field Utama | Keterangan |
| :--- | :--- | :--- |
| User | id, username, role_id, wilayah_id, status | Menyimpan kredensial dan peran pengguna. |
| Desa | id, nama_desa, kecamatan_id | Data referensi desa. |
| Dokumen_Desa | id, desa_id, jenis_dok, file_url, status | Menyimpan *file* dan tipe dokumen (RKP/APBDes/LPJ). |
| Evaluasi_Log | id, dokumen_id, user_id, aksi, catatan | Mencatat aksi Setuju/Tidak Setuju dari BPD dan Kec. |
| Audit_Trail | id, user_id, aksi, ip_address, timestamp | Wajib untuk kebutuhan lacak keamanan sistem. |
| [Data_Geotagging] | id, lpj_id, latitude, longitude, foto_url | [Fase 2] Validasi lokasi koordinat pembangunan. |

*Catatan: field dalam [tanda kurung siku] merupakan bagian dari fitur usulan/Fase Lanjutan (Bab 11).*

## 9. Kebutuhan Non-Fungsional (Non-Functional Requirements)
* **Kinerja & Aksesibilitas (Performance):** Aplikasi berbasis web harus dirancang minimalis dan ringan. Harus dapat memuat antarmuka dengan lancar bagi pengguna di daerah yang koneksinya terbatas.
* **Keamanan Akses (Security):** *Role-Based Access Control* (RBAC) wajib diterapkan secara presisi di level *routing* maupun *database* untuk memastikan pengguna hanya bisa mengakses panel wewenangnya.
* **Keamanan & Integritas Data:** Sistem harus memiliki perlindungan integritas agar *file* yang disetujui tidak dapat dimanipulasi secara retrospektif. Validasi *backend* harus kuat untuk mencegah *upload* format *file* berbahaya yang bisa merusak sistem dan berujung pada kerugian negara.
* **Transparansi (Auditability):** Ketersediaan sistem *Audit Trail* yang tidak dapat dimanipulasi atau dihapus oleh pengguna biasa.

## 10. Integrasi Pihak Ketiga
| Layanan | Fungsi | Catatan |
| :--- | :--- | :--- |
| Siskeudes API Gateway | Menarik nilai anggaran dan realisasi dasar dari aplikasi Siskeudes Nasional. | Untuk mencegah perbedaan data antara Siskeudes dan SIGAP, serta mencegah *input* ganda di desa. |

## 11. Fitur Usulan / Fase Lanjutan
* **Ekstraksi OCR (Optical Character Recognition)**. Implementasi AI untuk membaca angka pada foto kuitansi (Bukti Dukung) dan membandingkannya secara otomatis dengan nilai *input* sistem.
* **Dukungan Progressive Web App (PWA)**. Memungkinkan aplikasi menyimpan data *draft* form ke dalam *cache browser* saat koneksi terputus, dan melakukan sinkronisasi otomatis ketika jaringan *online*.
* **Geotagging Pembangunan Fisik**. Memaksa penyertaan data GPS pada setiap foto realisasi LPJ fisik untuk mencegah penipuan lokasi proyek.
* **Portal Transparansi Publik**. Dasbor *read-only* bagi masyarakat umum untuk memantau ringkasan penggunaan APBDes.
* **Smart Rules Engine**. Pengaturan variabel batas toleransi deviasi anggaran oleh admin tanpa harus mengubah kode dasar aplikasi.

## 12. Pertanyaan Terbuka / TBD
* Spesifikasi teknis, kredensial akses, dan format API (JSON/XML) dari Siskeudes yang akan digunakan untuk *bridging* data.
* Batas maksimal ukuran *file* (Mb) untuk dokumen Bukti Dukung yang boleh diunggah oleh desa demi menghemat ruang penyimpanan *server*.
* Mekanisme pendaftaran (*onboarding*) awal akun operator desa—apakah di-generate secara massal oleh Super Admin atau ada proses registrasi dengan verifikasi.
* Format rinci Laporan Pengujian UAT (*User Acceptance Testing*) yang disyaratkan oleh instansi.
* Format baku standar laporan cetak (PDF/Excel) yang diwajibkan oleh APIP dan TDA.

## 13. Glosarium
* **RKP** : Rencana Kerja Pemerintah (Desa).
* **APBDes** : Anggaran Pendapatan dan Belanja Desa.
* **LPJ** : Laporan Pertanggungjawaban.
* **APIP** : Aparat Pengawasan Intern Pemerintah (Inspektorat Daerah).
* **TDA** : Tim Daerah (Tim Analis Kabupaten).
* **Siskeudes** : Sistem Keuangan Desa (Aplikasi yang dikelola oleh Kemendagri & BPKP).
* **EWS** : Early Warning System (Sistem Peringatan Dini).
* **SIGAP** : Sistem Integrasi Pengawasan Anggaran Pedesaan (Nama Aplikasi).

*Dokumen ini merupakan draft sementara dan dapat berubah seiring pembahasan lebih lanjut dengan klien.*