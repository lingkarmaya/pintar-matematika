# berhitung.web.id — Matematika Ceria

Situs belajar matematika interaktif untuk anak SD kelas 1-6. Statis (HTML/CSS/JS murni, tidak ada backend).

## Repo
- GitHub: `lingkarmaya/pintar-matematika` (public)
- **PENTING:** repo `lingkarmaya/math-belajar-sd` BUKAN sumber situs ini meski namanya mirip — itu app PHP terpisah yang sempat salah dikira sebagai sumber berhitung.web.id. Sumber yang benar dikonfirmasi lewat field `homepageUrl` repo di GitHub, yaitu `pintar-matematika`.
- File utama: `index.html` (single file, semua CSS/JS inline)
- `CNAME` — berisi `berhitung.web.id`, dipakai kalau situs ini di-host ulang lewat GitHub Pages

## Hosting saat ini: VPS (bukan GitHub Pages lagi)
- VPS: `VPS_2601_2C2G40G` — kredensial & detail lengkap di `~/Documents/Claude/VPS_2601_2C2G40G/docker-stack-credentials.md`
- IP VPS: `43.133.130.25`
- SSH: `ssh ubuntu@43.133.130.25` (password ada di `~/Documents/Claude/VPS_2601_2C2G40G/.env`)
- DNS `berhitung.web.id` sudah diarahkan (A record) ke IP VPS ini — tidak lagi ke GitHub Pages
- Arsitektur: Caddy (native, host, auto-HTTPS) → reverse proxy ke container `php-app` (Apache) → virtual host `berhitung.web.id` → `DocumentRoot /var/www/sites/berhitung.web.id`
- Path file di VPS: `~/apps/sites/berhitung.web.id/index.html`

## Cara update situs ini
1. Edit `index.html` di folder lokal ini
2. Commit & push ke GitHub repo `pintar-matematika` (kalau mau simpan histori)
3. Upload file terbaru ke VPS:
   ```
   scp index.html ubuntu@43.133.130.25:~/apps/sites/berhitung.web.id/index.html
   ```
4. Tidak perlu restart container atau reload Caddy — Apache langsung baca file baru

## Domain terkait lain (bukan urusan folder ini)
- `coratcoret.web.id` (repo `pintar-menulis`) dan `bocilpintar.web.id` (+ subpath `pintar-catur`, `pintar-koding`) juga di-host di VPS yang sama, tapi migrasi DNS-nya dilakukan satu-satu — cek status terbaru di catatan VPS di atas.
