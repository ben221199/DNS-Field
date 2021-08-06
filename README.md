# DNS Field

## Field Types

| Name | Description | Size | Format | Example |
| --- | --- | --- | --- | --- |
| FQDN | Fully Qualified Domain Name (could be compressed with pointers) | variable | ( {UINT8:length} {CHAR*} ) | www.iana.org. |
| IPV4 | Internet Protocol address version 4 | 32 bits | {UINT8} {UINT8} {UINT8} {UINT8} | 192.168.1.5 |
| IPV6 | Internet Protocol address version 6 | 128 bits  | {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} | 2001:0db8:85a3:0000:0000:8a2e:0370:7334 |
| STRING | String | variable | {UINT8:length} {CHAR*} | "v=DMARC1; p=none; rua=mailto:dmarc@yourdomain.com" |
| UINT8 | Unsigned 8-bit integer (big endian) | 8 bits | | 30 |
| UINT16 | Unsigned 16-bit integer (big endian) | 16 bits | | 500 |

## Record Types

| Name | Value | Format | Example |
| --- | --- | --- | --- |
| A | 1 | {IPV4} | 192.168.1.5 |
| NS | 2 | {FQDN} | ns1.iana.org. |
