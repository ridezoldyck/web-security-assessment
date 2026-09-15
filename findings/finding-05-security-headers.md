# F-05 — Missing Security Headers

**Severity:** Low / Informational

## Observed
Beberapa security header umum tidak terlihat pada response yang diamati:
```text
Strict-Transport-Security
Content-Security-Policy
X-Frame-Options
X-Content-Type-Options
Referrer-Policy
Permissions-Policy
```

## Impact
Mengurangi defense-in-depth terhadap clickjacking, MIME sniffing, beberapa skenario XSS, dan downgrade/transport risks.

## Recommendation
Tambahkan header sesuai kebutuhan aplikasi, misalnya:
```text
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin
```
CSP perlu disesuaikan dengan resource aplikasi.
