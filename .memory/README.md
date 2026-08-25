# Project Memory

Last Updated: 2026-08-25 12:55:57
Format Version: 1

## Current State
Landing page statis satu file (`index.html`) untuk iklan sewa ruko Jatiwangi Majalengka. Host GitHub Pages (`https://alamaby.github.io/landing-page-rumah-toko-sukaraja/`). Tanpa framework/build tool. Gambar sudah full WebP (~590 KB total), SEO lengkap (OG/Twitter/JSON-LD/sitemap/robots), aksesibilitas diperbaiki.

## Active Decisions
- Gambar properti memakai format WebP-only tanpa fallback (browser support universal).
- Social share image = `images/og-image.jpg` (JPEG 1200x630) demi kompatibilitas scraper.
- Semua styling di dalam `<style>` index.html — sengaja single-file, jangan pecah tanpa alasan kuat.

## Open Items / Blockers
- Perubahan optimasi 2026-08-25 belum di-commit/push (menunggu konfirmasi user).

## Recent Entries
- [2026-08-25 Optimasi Landing Page](2026-08-25/125557-optimize-landing-page.md)
