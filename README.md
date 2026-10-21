# AZ Tailor — Laman Web

Laman web statik (HTML/CSS/JS tulen, tiada build) untuk AZ Tailor, kedai jahit di Bukit Gambir, Tangkak, Johor.

## Struktur

```
index.html
favicon.svg
assets/
  css/style.css
  js/main.js
  img/            ← gambar mockup (ganti dengan gambar sebenar)
```

## Ganti gambar mockup

Simpan gambar sebenar dalam `assets/img/` dan tukar `src` dalam `index.html`
(contoh: `hero.svg` → `hero.jpg`). Saiz disyorkan:

| Fail | Nisbah | Kegunaan |
|---|---|---|
| `hero` | 4:5 (potret) | Gambar utama |
| `about` | 5:6 | Bahagian Tentang |
| `baju_*.webp` | 4:5 (800×1000) | Galeri (6 keping) — siap |
| `raya` | 3:2 (landskap) | Bahagian Baju Raya |

Mampatkan gambar (JPG/WebP, < 300 KB setiap satu) supaya laman laju.

## Kod QR lokasi

`assets/img/qr-mockup.svg` hanyalah mockup. Untuk QR sebenar:
1. Buka Google Maps → cari kedai → **Share** → **Copy link**.
2. Jana QR dari pautan itu (cth. qr-code-generator / Canva), simpan sebagai `assets/img/qr-lokasi.png`.
3. Tukar `src` QR dalam `index.html`, dan kemas kini pautan **Buka di Google Maps** + `src` iframe peta dengan pautan yang sama/koordinat tepat.

## Hosting di GitHub Pages + domain sendiri

1. Push kandungan folder ini ke root repo (contoh `az-tailor`):
   ```
   git init
   git add .
   git commit -m "Laman web AZ Tailor"
   git branch -M main
   git remote add origin https://github.com/<username>/<repo>.git
   git push -u origin main
   ```
2. Repo → **Settings → Pages** → Source: *Deploy from a branch* → `main` / `/ (root)`.
3. Di bahagian **Custom domain**, masukkan domain anda (cth. `aztailor.com.my`) — GitHub akan cipta fail `CNAME` secara automatik.
4. Di panel DNS domain anda:
   - **Apex domain** (`aztailor.com.my`): 4 rekod `A` →
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **www**: rekod `CNAME` → `<username>.github.io`
5. Tunggu DNS propagate, kemudian tandakan **Enforce HTTPS**.
