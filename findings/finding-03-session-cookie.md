# F-03 — Session Cookie Security Attributes

**Severity:** Low–Medium

## Observed Cookie
```text
PHPSESSID=REDACTED; path=/
```

Pada response yang diamati, atribut `Secure`, `HttpOnly`, dan `SameSite` tidak terlihat. Perlu diverifikasi pada konfigurasi production.

## Impact
Jika benar tidak diterapkan, risiko mencakup pengiriman cookie tanpa batas HTTPS, akses cookie oleh JavaScript pada skenario XSS, dan peningkatan risiko CSRF tergantung konfigurasi aplikasi.

## Recommendation
Gunakan:
```text
Secure
HttpOnly
SameSite=Lax
```
atau kebijakan lebih ketat sesuai kebutuhan.

Contoh PHP:
```php
session_set_cookie_params([
  'secure' => true,
  'httponly' => true,
  'samesite' => 'Lax'
]);
```

Session ID juga berubah antara sebelum dan sesudah login pada test, sehingga tidak ada indikasi session fixation dari pengujian tersebut.
