# F-06 — Improper Handling of Invalid Product ID

**Severity:** Informational / Low

## Affected Endpoint
`detail.php?id=`

## Evidence
Test values:
```text
id=1
id=999999
id=abc
id=0
id=-1
id=1.5
```
Semua mengembalikan HTTP 200. ID yang tidak tersedia menghasilkan template dengan informasi produk kosong, misalnya `Rp <br />`.

## Impact
Dampak keamanan langsung tidak terbukti, tetapi response menjadi tidak konsisten dan menunjukkan kurangnya input validation.

## Recommendation
Validasi integer dan kembalikan `400` untuk input invalid serta `404` untuk product yang tidak ditemukan.
```php
$id = filter_input(INPUT_GET, 'id', FILTER_VALIDATE_INT);
if ($id === false || $id === null || $id < 1) {
    http_response_code(400);
    exit('Invalid product ID');
}
```
