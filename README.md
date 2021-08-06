# DNS Field

## Field Types

| Name | Description | Size | Format | Example |
| --- | --- | --- | --- | --- |
| FQDN (*) | Fully Qualified Domain Name (could be compressed with pointers) | variable | ( {UINT8:length} {CHAR*} ) | www.iana.org. |
| INT32 | Signed 32-bit integer (big endian) | 32 bits | | -90000 |
| IPV4 | Internet Protocol address version 4 | 32 bits | {UINT8} {UINT8} {UINT8} {UINT8} | 192.168.1.5 |
| IPV6 | Internet Protocol address version 6 | 128 bits | | {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} {UINT16} | 2001:0db8:85a3:0000:0000:8a2e:0370:7334 |
| NID | Node Id | 64 bits | {UINT16} {UINT16} {UINT16} {UINT16} | 0015:5fff:ff21:ee65 |
| STRING | String | variable | {UINT8:length} {CHAR*} | "v=DMARC1; p=none; rua=mailto:dmarc@yourdomain.com" |
| UINT8 | Unsigned 8-bit integer (big endian) | 8 bits | | 30 |
| UINT16 | Unsigned 16-bit integer (big endian) | 16 bits | | 500 |
| UINT32 | Unsigned 32-bit integer (big endian) | 32 bits | | 700000 |

(*) FQDN could be relative in a zone file, but is always sent as absolute in the DNS protocol. Pointers can be used in FQDNs as compression.

## Quantity Types

| Symbol | Description |
| --- | --- |
| ? | Zero or one. |
| + | One or more. |
| * | Zero or more. |

## Record Types

| Name | Value | Format | Example |
| --- | --- | --- | --- |
| A | 1 | {IPV4:address} | 192.168.1.5 |
| NS | 2 | {FQDN:nsdname} | ns1.iana.org. |
| MD | 3 | {FQDN:madname} | md1.iana.org. |
| MF | 4 | {FQDN:madname} | mf1.iana.org. |
| CNAME | 5 | {FQDN:cname} | website.iana.org.
| SOA | 6 | {FQDN:mname} {FQDN:rname} {UINT32:serial} {UINT32:refresh} {UINT32:retry} {UINT32:expire} {UINT32:minimum} | ns1.iana.org. dns\\.info.iana.org. (20 7200 600 3600000 60) |
| MB | 7 | {FQDN:madname} |
| MG | 8 | {FQDN:mgmname} |
| MR | 9 | {FQDN:newname} |
| NULL | 10 | {*:anything} | |
| WKS | 11 | {IPV4:address} {UINT8:protocol} {__BITMAP:bit_map}
| PTR | 12 | {FQDN:ptrdname} | server.iana.org. | 
| HINFO | 13 | {STRING:cpu} {STRING:os} |
| MINFO | 14 | {FQDN:rmailbx} {FQDN:emailbx} |
| MX | 15 | {UINT16:preference} {FQDN:exchange} |
| TXT | 16 | {STRING+:txt-data} |
| RP | 17 | {FQDN:mbox-dname} {FQDN:txt-dname} |
| AFSDB | 18 | {UINT16:subtype} {FQDN:hostname} |
| X25 | 19 | {STRING:PSDN-address} |
| ISDN | 20 | {STRING:ISDN-address} {STRING?:sa}
| RT | 21 | {UINT16:preference} {FQDN:intermediate-host}
| NSAP | 22 |
| NSAP-PTR | 23 |
| SIG | 24 |
| KEY | 25 |
| PX | 26 | {UINT16:preference} {FQDN:map822} {FQDN:mapx400}
| GPOS | 27 | {STRING:longitude} {STRING:latitude} {STRING:altitude}
| AAAA | 28 | {IPV6:__address} |
| LOC | 29 | {UINT16:version=0} {UINT16:size} {UINT16:horiz_pre} {UINT16:vert_pre} {UINT16:latitude} {UINT16:latitude} {UINT16:longitude} {UINT16:longitude} {INT16:altitude} {INT16:altitude} |
| NXT | 30 | {FQDN:next_domain_name} {__BITMAP2:type_bit_map}
| EID | 31 |
| NIMLOC | 32 |
| SRV | 33 | {UINT16:priority} {UINT16:weight} {UINT16:port} {FQDN:target}
| ATMA | 34 |
| NAPTR | 35 | 
| KX | 36 |
| CERT | 37 |
| A6 | 38 |
| DNAME | 39 |
| SINK | 40 |
| OPT | 41 |
| APL | 42 |
| DS | 43 |
| SSHFP | 44 |
| IPSECKEY | 45 |
| RRSIG | 46 |
| NSEC | 47 |
| DNSKEY | 48 |
| DHCID | 49 |
| NSEC3 | 50
| NSEC3PARAM | 51 |
| TLSA | 52 |
| SMIMEA | 53 |
| <ins>*Unassigned*</ins> | 54 |
| HIP | 55 |
| NINFO | 56 |
| RKEY | 57 |
| TALINK | 58 |
| CDS | 59 |
| CDNSKEY | 60 |
| OPENPGPKEY | 61 |
| CSYNC | 62 |
| ZONEMD | 63 |
| SVCB | 64 |
| HTTPS | 65 |
| <ins>*Unassigned*</ins> | 66-98 |
| SPF | 99 | {STRING+}
| UINFO | 100 |
| UID | 101 |
| GID | 102 |
| UNSPEC | 103 |
| NID | 104 | {UINT16:preference} {NID:nodeid} |
| L32 | 105 | {UINT16:preference} {IPV4:locator32} |
| L64 | 106 | {UINT16:preference} {NID:locator64} |
| LP | 107 | {UINT16:preference} {FQDN:fqdn} |
| EUI48 | 108 |
| EUI64 | 109 |
| <ins>*Unassigned*</ins> | 110-248 |
| TKEY | 249 |
| TSIG | 250 |
| IXFR | 251 |
| AXFR | 252 |
| MAILB | 253 |
| MAILA | 254 |
| * | 255 |
| URI | 256 |
| CAA | 257 |
| AVC | 258 |
| DOA | 259 |
| AMTRELAY | 260 |
| <ins>*Unassigned*</ins> | 261-32767 |
| TA | 32768 |
| DLV | 32769 |