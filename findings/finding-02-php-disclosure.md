# F-02 — PHP Version Disclosure

**Severity:** Low / Informational

## Evidence
Observed response header:
```text
Server: cloudflare
X-Powered-By: PHP/8.4.23
```

## Impact
Version disclosure membantu fingerprinting dan pemilihan vulnerability yang relevan. Disclosure ini sendiri tidak membuktikan vulnerability.

## Recommendation
Hilangkan `X-Powered-By`, misalnya dengan:
```ini
expose_php = Off
```

**Priority:** Low.
