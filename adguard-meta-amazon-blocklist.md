# AdGuard Home: Meta/Instagram and Amazon DNS Sinkhole Rules

These rules send matching IPv4 DNS requests to `0.0.0.0` using AdGuard Home's `dnsrewrite` syntax.


## Rules

```adblock
! ============================================================
! Meta / Facebook / Instagram
! Apex domains and every subdomain are rewritten to 0.0.0.0.
! ============================================================

||facebook.com^$dnsrewrite=NOERROR;A;0.0.0.0
||facebook.net^$dnsrewrite=NOERROR;A;0.0.0.0
||fb.com^$dnsrewrite=NOERROR;A;0.0.0.0
||fbcdn.net^$dnsrewrite=NOERROR;A;0.0.0.0
||fbsbx.com^$dnsrewrite=NOERROR;A;0.0.0.0
||fb.me^$dnsrewrite=NOERROR;A;0.0.0.0
||facebookmail.com^$dnsrewrite=NOERROR;A;0.0.0.0
||facebookbrand.com^$dnsrewrite=NOERROR;A;0.0.0.0
||facebookcareers.com^$dnsrewrite=NOERROR;A;0.0.0.0
||facebook.design^$dnsrewrite=NOERROR;A;0.0.0.0
||facebook.net^$dnsrewrite=NOERROR;A;0.0.0.0
||instagram.com^$dnsrewrite=NOERROR;A;0.0.0.0
||cdninstagram.com^$dnsrewrite=NOERROR;A;0.0.0.0
||ig.me^$dnsrewrite=NOERROR;A;0.0.0.0
||meta.com^$dnsrewrite=NOERROR;A;0.0.0.0
||meta.ai^$dnsrewrite=NOERROR;A;0.0.0.0
||metacareers.com^$dnsrewrite=NOERROR;A;0.0.0.0
||messenger.com^$dnsrewrite=NOERROR;A;0.0.0.0

! ============================================================
! Amazon retail domains by country/region
! Apex domains and every subdomain are rewritten to 0.0.0.0.
! This section does not intentionally block AWS domains.
! ============================================================

||amazon.com^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.ca^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.com.mx^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.com.br^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.co.uk^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.de^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.fr^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.it^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.es^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.nl^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.se^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.pl^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.com.be^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.ie^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.co.jp^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.cn^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.in^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.com.au^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.sg^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.ae^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.sa^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.com.tr^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.eg^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.co.za^$dnsrewrite=NOERROR;A;0.0.0.0

! Common Amazon retail/static-content domains
||amazonusercontent.com^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon-adsystem.com^$dnsrewrite=NOERROR;A;0.0.0.0
||amazonpay.com^$dnsrewrite=NOERROR;A;0.0.0.0
||amazonpay.in^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.jobs^$dnsrewrite=NOERROR;A;0.0.0.0
||amazon.science^$dnsrewrite=NOERROR;A;0.0.0.0
||media-amazon.com^$dnsrewrite=NOERROR;A;0.0.0.0
||ssl-images-amazon.com^$dnsrewrite=NOERROR;A;0.0.0.0
||images-amazon.com^$dnsrewrite=NOERROR;A;0.0.0.0
```

## Notes

- The `||domain^` form matches the named domain and all of its subdomains.
- The rewrite affects DNS hostnames, not complete URL paths. DNS cannot distinguish paths such as `/shop` or `/login` on the same hostname.
- `0.0.0.0` is an IPv4 sinkhole response. AdGuard Home may return an empty answer for other record types when a matching `dnsrewrite` rule applies.
- This list deliberately avoids broad AWS domains such as `amazonaws.com`, because blocking them would disrupt many unrelated websites and services.
- Meta and Amazon may add or change domains over time, so no static list can guarantee permanent coverage of every future hostname.

## Quick test

Run one of these commands from a device that uses your AdGuard Home server:

```sh
nslookup facebook.com
nslookup instagram.com
nslookup amazon.com
nslookup amazon.co.uk
```

The IPv4 answer should be `0.0.0.0`.
