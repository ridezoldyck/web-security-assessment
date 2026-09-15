# Web Security Assessment — Lily Style

Authorized Web Application Security Assessment terhadap website **Lily Style** (`lilystyle.my.id`).

> **Important:** Pengujian dilakukan berdasarkan izin dari pemilik website. Dokumentasi ini hanya memuat pengujian terkontrol dan non-destruktif. Data sensitif, kredensial, dan session cookie telah disanitasi.

## Tujuan
- Mengidentifikasi potensi kerentanan keamanan.
- Menilai konfigurasi keamanan aplikasi.
- Mendokumentasikan bukti dan dampak.
- Memberikan rekomendasi remediation.

## Scope
`https://lilystyle.my.id/`

Area: DNS/network exposure, HTTP/HTTPS, endpoint mapping, authentication/authorization, session management, input validation, `detail.php?id`, cart/checkout, error handling, dan security headers.

## Metodologi
```text
Reconnaissance → Information Gathering → Endpoint Mapping → Security Configuration Review
→ Controlled Vulnerability Testing → Risk Assessment → Remediation → Final Report
```

## Tools
- Kali Linux
- Nmap
- curl
- nslookup / dig
- Wireshark
- Browser Developer Tools

## Ringkasan Temuan
| ID | Temuan | Severity |
|---|---|---|
| F-01 | SQL Injection pada `detail.php?id` | High |
| F-02 | PHP Version Disclosure | Low / Informational |
| F-03 | Session Cookie Security Attributes | Low–Medium |
| F-04 | Verbose PHP Error / Path Disclosure | Low |
| F-05 | Missing Security Headers | Low / Informational |
| F-06 | Improper Handling of Invalid Product ID | Informational / Low |

## Positive Observations
- Endpoint cart melakukan pemeriksaan login pada request tanpa session.
- `update_cart_qty.php` menolak request unauthenticated dengan pesan `Not logged in`.
- `checkout.php` meminta login ketika session tidak valid.
- `profile.php` dan `pesanan.php` terlindungi autentikasi.
- Tidak ditemukan bukti IDOR pada `pesanan.php` selama assessment terbatas.
- Session ID berubah antara sebelum dan sesudah login pada pengujian, sehingga tidak ada indikasi session fixation dari test tersebut.

## Batasan
Tidak melakukan database extraction, modifikasi/penghapusan data pengguna lain, brute force, DDoS, malware deployment, social engineering, atau pengujian sistem pihak ketiga.

## Struktur
```text
web-security-assessment-lilystyle/
├── README.md
├── scope.md
├── reconnaissance/
│   ├── dns.txt
│   └── nmap.txt
├── findings/
│   ├── finding-01-sqli.md
│   ├── finding-02-php-disclosure.md
│   ├── finding-03-session-cookie.md
│   ├── finding-04-error-disclosure.md
│   ├── finding-05-security-headers.md
│   └── finding-06-invalid-id.md
└── screenshots/
    └── README.md
```

## Disclaimer
Dokumentasi ini untuk pembelajaran dan portfolio cybersecurity. Pengujian hanya boleh dilakukan pada sistem yang dimiliki atau telah memberikan izin.
