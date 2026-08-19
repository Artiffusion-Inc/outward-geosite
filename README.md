# hypcat-geosite

Auto-updated custom `geosite.dat` combining multiple sources for optimal RU/BY proxy routing.

## Sources

- [v2fly/domain-list-community](https://github.com/v2fly/domain-list-community) — base with all standard categories (`category-ip-geo-detect`, `google`, `youtube`, etc.)
- [hydraponique/roscomvpn-geosite](https://github.com/hydraponique/roscomvpn-geosite) — custom RU categories (`torrent`, `category-ru`, `whitelist`, service-specific lists)
- [runetfreedom/russia-blocked-geosite](https://github.com/runetfreedom/russia-blocked-geosite) — RKN-blocked domains, ad block, `ru-blocked`/`ru-blocked-all`
- [runetfreedom/russia-domains-list](https://github.com/runetfreedom/russia-domains-list) — `ru-available-only-inside`

## Key differences from upstream

- IP checkers (`ifconfig.me`, `api.ipify.org`, `checkip.amazonaws.com`, `ip.sb`, `2ip.ru`) are **removed** from `category-ru` and `whitelist`. They should be blocked via `category-ip-geo-detect`, not routed direct.
- `torrent` category is included (from roscomvpn) for blocking torrent traffic through shared proxies.
- `ru-blocked` and `ru-blocked-all` categories include RKN-blocked domains from antifilter + refilter.
- `category-ads-all` is built from AdGuard DNS filter + Peter Lowe's list.

## Download

```bash
# Latest release
curl -fsSL https://github.com/Xpos587/hypcat-geosite/releases/latest/download/geosite.dat -o geosite.dat

# release branch (raw)
curl -fsSL https://raw.githubusercontent.com/Xpos587/hypcat-geosite/release/geosite.dat -o geosite.dat
```

## Update schedule

Every 6 hours via GitHub Actions cron: `0 3,9,15,21 * * *`.

## License

This project aggregates public domain lists from multiple sources. Each source retains its own license.
