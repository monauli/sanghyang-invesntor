# Handoff Mobile Customer

## Baseline yang sudah stabil

- Repository: `monauli/sanghyang-invesntor`
- Commit terakhir: `e6d1e91`
- Link utama: https://sanghyang-investor-deck-20260924.vercel.app/
- Link utama tetap satu; perangkat mobile diarahkan otomatis ke shell mobile.

## Pola implementasi

- `index.html` tetap menjadi sumber utama deck, foto, dan interaksi.
- `mobile.html` hanya menjadi shell ringan yang memuat:
  `/index.html?embedded=1#1`
- `index.html` mendeteksi perangkat mobile dan mengarahkan entry biasa ke `/mobile.html`.
- Parameter `embedded=1` mencegah redirect berulang di dalam iframe.
- Saat halaman dibuka atau reload, slide selalu dinormalisasi ke `#1`.
- Foto dan fungsi interaktif tidak diduplikasi sehingga perilakunya tetap konsisten.

## Saat diterapkan ke proyek Mobile Customer

1. Salin pola redirect dari `index.html`.
2. Buat `mobile.html` sebagai shell iframe dengan `viewport-fit=cover`.
3. Gunakan `?embedded=1#1` pada iframe.
4. Uji link utama di desktop dan HP.
5. Uji tombol interaktif, foto/zoom, dan perpindahan slide sebelum deploy.

## Catatan fullscreen

Fullscreen otomatis tidak dapat dipaksa dari link biasa di iPhone. Android dapat memakai fullscreen setelah tap pengguna; iPhone membutuhkan Add to Home Screen/PWA untuk pengalaman tanpa address bar.

## Jangan diubah tanpa kebutuhan

- Jangan menggandakan seluruh file deck untuk versi mobile.
- Jangan mengubah asset foto atau handler interaksi yang sudah berjalan.
- Jangan menambahkan toolbar Previous/Next jika targetnya tetap tampilan bersih.
