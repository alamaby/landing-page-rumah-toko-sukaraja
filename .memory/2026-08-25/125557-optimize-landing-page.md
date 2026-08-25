# Optimasi Landing Page Ruko Sukaraja

Created: 2026-08-25 12:55:57

## Task
Analisa & perbaikan menyeluruh landing page statis sewa ruko (single-file `index.html`, GitHub Pages).

## Files Changed
- `.gitignore` — diisi ulang (sebelumnya berisi teks sampah artefak AI)
- `favicon_creation_instructions.txt` — dihapus (sisa instruksi AI, tidak ter-track git)
- `index.html` — banyak perubahan (lihat keputusan)
- `images/*` — 6 foto asli (.jpg/.png) dikonversi ke .webp, ditambah `og-image.jpg`
- `robots.txt`, `sitemap.xml` — baru

## Technical / Business Decisions
- **Konversi WebP full**: semua foto properti → WebP quality 82 (Pillow, method=6). Total ~2,5 MB → ~590 KB. Original dihapus dari working tree (masih ada di riwayat git).
- **OG image baru** `images/og-image.jpg` (1200x630, center-crop dari foto hero): sebelumnya og:image mengklaim 1200x630 padahal file asli 988x928. og:image/twitter:image kini menunjuk og-image.jpg (JPEG, bukan WebP — kompatibilitas maksimal dengan scraper sosial media lama).
- **WebP-only tanpa fallback `<picture>`**: dukungan browser WebP sudah universal (Safari 14+, 2020). Trade-off: browser jadul tak terawat akan gagal load gambar.
- **Aksesibilitas**: lightbox jadi `role="dialog" aria-modal`, tombol close `<span>` → `<button>` + aria-label + fokus manajemen (focus close saat buka, restore fokus saat tutup); gambar galeri `tabindex="0" role="button"` + handler Enter/Space; skip-link dipindah ke atas `<body>` pakai kelas CSS (hapus hack `onfocus` inline); aria-label pada tombol WhatsApp float; `title` pada iframe maps; focus-visible outline.
- **Refactor inline style**: seksi deskripsi/FAQ/iframe → kelas CSS (`bg-white`, `bg-gray`, `description-content`, `faq`, `faq-item`, `.map-container iframe`). Nol atribut `style=` tersisa.
- **Lain-lain**: meta theme-color, tahun footer dinamis via JS.

## Assumptions / Risks
- Perubahan belum di-commit/deploy; GitHub Pages masih serve versi lama sampai push.
- JSON-LD image list sekarang menunjuk .webp — Google mendukung, tapi validator scraper pihak ketiga yang tak dukung WebP bisa warning.
- Tahun footer via JS: non-JS user lihat fallback "2026".

## Verification
- Python script: tidak ada referensi gambar stale, semua file yang direferensikan ada, kedua JSON-LD valid parse, tag balance OK (section/details/button/iframe), 5 tabindex galeri, semua check a11y PASS, 0 inline style.

## Commit Proposal
`feat: optimize images to webp, add seo files, and improve accessibility`

## Progress Log
- 2026-08-25 12:55 — Optimasi selesai, verifikasi lolos.
- 2026-08-25 13:05 — Commit & push. Push pertama ditolak (remote maju ke a1329ad: migrasi domain GitHub Pages → Vercel via PR #2/#3). Rebase menghasilkan konflik di 3 blok URL absolut index.html; diselesaikan dengan mempertahankan domain Vercel + og-image.jpg WebP baru. robots.txt & sitemap.xml ikut diarahkan ke Vercel. Final: `c19aafc` ter-push ke main.
- 2026-08-25 13:20 — Tambah penanda "properti sementara tidak tersedia / sudah ada penghuni" di 7 titik: banner sticky merah atas halaman (role=status), badge hero, status tag + note di seksi pricing, notice box di deskripsi lengkap, FAQ baru (HTML + JSON-LD, posisi pertama, `open` default), meta description/og/twitter di-update, JSON-LD utama + `"availability": "https://schema.org/SoldOut"`. CTA WhatsApp direframe jadi "Tanyakan Ketersediaan". Verifikasi lolos semua.
