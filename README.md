# Website Staklim DIY (base)
Jalankan: `docker compose up --build` lalu buka http://localhost:8080

Arsitektur (3 container, sengaja tidak dipecah lebih jauh):
- web   : React + Vite + MapLibre GL JS, disajikan nginx; nginx meneruskan /api ke api dan /tiler ke tiler
- api   : FastAPI (berita, stasiun, metadata). Ganti data contoh di api/main.py
- tiler : TiTiler resmi, membaca COG dari ./data (mis. ./data/ch_harian.tif, ./data/lpi.tif)

Peta tampil walau ./data kosong; layer QPE/LPI baru muncul setelah file COG ada.
Dev tanpa Docker: `cd web && npm i && npm run dev` (api di :8000).
Langkah lanjut: Zarr via titiler.xarray, slider waktu (raster-array), deck.gl, Airflow/Prefect.

Halaman: / (beranda + peta), /iklim (daftar + kategori + pagination, parameter ?kategori=&hal=)
API: GET /api/iklim?kategori=&page=&per_page=
