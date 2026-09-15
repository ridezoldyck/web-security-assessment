# F-04 — Verbose PHP Error / Path Disclosure

**Severity:** Low

## Evidence
Error response menampilkan detail internal seperti:
```text
/var/www/html/linda/web/detail.php:8
mysqli_query
mysqli_sql_exception
MariaDB
```

## Impact
Membocorkan struktur filesystem, nama file aplikasi, database component, dan stack trace yang dapat membantu reconnaissance.

## Recommendation
Production sebaiknya menggunakan:
```ini
display_errors = Off
log_errors = On
```
Tampilkan generic error page kepada user dan simpan detail hanya di server-side logs.
