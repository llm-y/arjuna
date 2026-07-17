# arjuna
Orkestrasi


Saya sudah memiliki dua sistem lokal: satu untuk Mamba (untuk meringkas teks panjang) dan satu untuk Transformer/ExLlamaV2 (untuk reasoning). 

Tolong buatkan skrip Python orkestrasi bernama 'academic_workflow.py' yang menggabungkan keduanya menjadi satu alur kerja otomatis untuk tugas akademik:

1. FUNGSI SUMMARIZER (MAMBA):
   - Muat model Mamba.
   - Buat fungsi yang menerima input berupa path folder berisi file teks/PDF.
   - Gunakan Mamba untuk membaca seluruh konten file tersebut dan menghasilkan 'Ringkasan Terstruktur' yang padat.
   - Setelah selesai, bersihkan memori VRAM dari model Mamba (unload model) agar GPU kosong kembali.

2. FUNGSI REASONING (TRANSFORMER):
   - Setelah Mamba selesai dan VRAM kosong, muat model Transformer (DeepSeek-R1-Distill EXL2).
   - Masukkan 'Ringkasan Terstruktur' tadi ke dalam prompt Transformer.
   - Minta Transformer untuk melakukan tugas spesifik: "Analisis ringkasan ini untuk mencari celah penelitian (research gap)" atau "Tulis ulang menjadi pendahuluan manuskrip yang koheren".

3. MEKANISME SWAPPING:
   - Pastikan skrip menangani manajemen VRAM dengan ketat: Hapus model Mamba dari GPU -> Garbage Collect -> Baru muat model Transformer. Ini krusial karena RTX 5060 Ti saya hanya punya 16GB, tidak cukup untuk memuat kedua model sekaligus.

4. INPUT/OUTPUT:
   - Buat agar skrip ini bisa dijalankan via terminal dengan argumen folder input.

Berikan kode lengkapnya dan jelaskan cara kerjanya.
