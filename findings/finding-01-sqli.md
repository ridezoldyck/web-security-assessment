# F-01 — SQL Injection pada `detail.php?id`

**Severity:** High  
**Status:** Confirmed at input-to-query boundary; full database impact intentionally not demonstrated.

## Affected Endpoint
`https://lilystyle.my.id/detail.php?id=`

## Description
Parameter `id` menerima input pengguna dan tampak digunakan dalam query database tanpa validasi/parameterisasi yang memadai. Karakter quote tunggal menyebabkan PHP menampilkan SQL syntax error.

## Evidence
Normal:
```bash
curl -s -o /dev/null -w "Normal: %{http_code} %{size_download}\\n" "https://lilystyle.my.id/detail.php?id=1"
```
Observed: `Normal: 200 5500`

Controlled malformed input:
```bash
curl -s "https://lilystyle.my.id/detail.php?id=1'" | head -30
```
Response contained `Fatal error`, `mysqli_sql_exception`, `You have an error in your SQL syntax`, `MariaDB`, `mysqli_query`, dan `detail.php:8`.

## Impact
Potentially unauthorized database access/disclosure, modification, or authentication-related impact depending on query context. Full impact was not tested.

## Recommendation
Gunakan prepared statements/parameterized queries dan validasi integer.
```php
$id = filter_input(INPUT_GET, 'id', FILTER_VALIDATE_INT);
$stmt = $conn->prepare("SELECT * FROM produk WHERE id = ?");
$stmt->bind_param("i", $id);
```
Disable database error display in production.

**Priority:** P0 / immediate remediation.
