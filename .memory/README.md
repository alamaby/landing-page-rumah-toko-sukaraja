# Project Memory

Last Updated: 2026-08-25 12:55:57
Format Version: 1

## Current State
Landing page statis satu file (`index.html`) untuk iklan sewa ruko Jatiwangi Majalengka. **Deploy via Vercel** (`https://disewakan-rumah-toko-sukaraja.vercel.app/`) sejak PR #2/#3 remote. Tanpa framework/build tool. Gambar sudah full WebP (~590 KB total), SEO lengkap (OG/Twitter/JSON-LD/sitemap/robots), aksesibilitas diperbaiki.

## Active Decisions
- Hosting: Vercel — SEMUA URL absolut (og:url, canonical, og:image, JSON-LD, sitemap) harus pakai domain `disewakan-rumah-toko-sukaraja.vercel.app`, bukan github.io.
- Gambar properti memakai format WebP-only tanpa fallback (browser support universal).
- Social share image = `images/og-image.jpg` (JPEG 1200x630) demi kompatibilitas scraper.
- Semua styling di dalam `<style>` index.html — sengaja single-file, jangan pecah tanpa alasan kuat.

## Open Items / Blockers
- Tidak ada.

## Recent Entries
- [2026-08-25 Optimasi Landing Page](2026-08-25/125557-optimize-landing-page.md)
