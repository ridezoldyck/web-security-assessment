# Scope & Rules of Engagement

## Target
```text
Target: Lily Style
Domain: lilystyle.my.id
Protocol: HTTPS
Primary URL: https://lilystyle.my.id/
```

## Authorization
Pengujian dilakukan terhadap website milik teman dengan izin dari pemilik website. Assessment dibatasi pada aktivitas aman, terkontrol, dan tidak merusak data.

## In-Scope
- DNS lookup, IP/CDN identification, port discovery terbatas, service/version identification.
- Public pages, authentication flow, session behavior, product detail parameter, cart, checkout access control, error handling, security headers.
- Input validation, controlled SQL injection detection, authentication checks, basic authorization checks, session cookie review.

## Out-of-Scope
- Sistem pihak ketiga di luar kontrol pemilik.
- Website/domain lain.
- Database extraction, data modification/deletion, brute force, credential stuffing, DDoS, malware, social engineering, pengujian pengguna lain.

## Rules
1. Gunakan akun pengujian yang sah.
2. Jangan mempublikasikan credential/session cookie.
3. Jangan mengambil data pribadi pengguna lain.
4. Gunakan payload seminimal mungkin.
5. Hentikan pengujian bila berpotensi merusak sistem.
6. Semua bukti repository harus disanitasi.

## Evidence Handling
```text
PHPSESSID=REDACTED
email=test@example.com
password=REDACTED
token=REDACTED
```

## Objective
`Identify → Validate → Document → Recommend Fix`
