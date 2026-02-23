# Security Policy untuk YSBS Mino Martani Website

## Fitur Keamanan yang Diterapkan

### 1. HTTP Security Headers
- **X-Content-Type-Options**: nosniff - Mencegah MIME type sniffing
- **X-Frame-Options**: SAMEORIGIN - Melindungi dari clickjacking attacks
- **X-XSS-Protection**: 1; mode=block - Aktivasi built-in XSS protection
- **Referrer-Policy**: strict-origin-when-cross-origin - Kontrol informasi referrer
- **Permissions-Policy**: Menonaktifkan akses kamera, microphone, geolocation
- **Strict-Transport-Security**: HTTPS only dengan max-age 1 tahun
- **Content-Security-Policy**: Pembatasan sumber konten yang diizinkan

### 2. Subresource Integrity (SRI)
- Hash integrity untuk Font Awesome CDN
- Crossorigin attributes untuk semua external resources
- Melindungi dari CDN compromises

### 3. Content Security Policy (CSP)
Membatasi sumber konten yang diizinkan:
- Scripts: self, unpkg.com, cdn.jsdelivr.net
- Styles: self, Google Fonts, cdnjs, unpkg
- Fonts: self, Google Fonts, cdnjs
- Images: self, data, https only
- Frame ancestors: self only

### 4. Proteksi Tambahan
- robots.txt untuk kontrol crawler
- .gitignore untuk proteksi file sensitif
- HTTPS enforcement melalui HSTS

## Cara Deploy ke Vercel

1. Push semua file ke repository Git Anda
2. Connect repository ke Vercel
3. Vercel akan otomatis mendeteksi `vercel.json` dan apply security headers
4. Website Anda akan terlindungi secara otomatis

## Best Practices

1. **Jangan commit file .env** - Sudah ada di .gitignore
2. **Update dependencies secara berkala** - Check Font Awesome dan AOS updates
3. **Monitor Vercel Analytics** - Untuk deteksi activity mencurigakan
4. **Regular backups** - Backup files dan database (jika ada)
5. **HTTPS only** - Always enforce HTTPS (sudah diset via HSTS)

## Pelaporan Keamanan

Jika menemukan vulnerability atau masalah keamanan, segera hubungi:
- Email: mino_martani@yahoo.com
- Telepon: +62-812-1546-6444

## Additional Recommendations

1. **Enable Vercel's DDoS Protection** (otomatis aktif di Vercel)
2. **Use Vercel Web Analytics** untuk monitoring (gratis, privacy-friendly)
3. **Pertimbangkan Cloudflare** untuk layer proteksi tambahan (optional)
4. **Regular security audits** - Gunakan tools seperti:
   - https://securityheaders.com/
   - https://observatory.mozilla.org/
   - Chrome Lighthouse Security Audit

## Update Log

- 2026-02-23: Initial security implementation
  - Added HTTP security headers via vercel.json
  - Implemented SRI for external resources
  - Added security meta tags
  - Created robots.txt dan .gitignore
