# Cloudflare firewall rules
This rules is optimized for `Free plan`, which only have 5 rules available.

#### Rule 1: Allow Bots:
* Action: Allow
* ` (cf.client.bot) or (ip.geoip.asnum eq 2635) or (ip.src eq 54.68.32.247) or (ip.src eq 44.235.211.232) or (ip.src eq 54.71.203.174) or (ip.geoip.asnum eq 32934) or (ip.geoip.asnum eq 63293) or (ip.geoip.asnum eq 36459) `

#### Rule 2: Allow valid query string
* Action: Allows
* ` (http.request.uri eq "") or (http.request.uri contains "?f") or (http.request.uri contains "?a") or (http.request.uri contains "?u") `

#### Rule 3: Challenge request not in VN
* Action: Legacy CAPTCHA
* ` (not ip.geoip.country in {"VN"}) `

#### Rule 4: Block request from botnets, china, tor, random query string ddos
* Action: Block
* ` (ip.geoip.asnum eq 4134) or (ip.geoip.asnum eq 14061) or (ip.geoip.asnum eq 53667) or (ip.geoip.asnum eq 14618) or (ip.geoip.asnum eq 63949) or (ip.geoip.asnum eq 4837) or (ip.geoip.asnum eq 396507) or (ip.geoip.asnum eq 135951) or (ip.geoip.country in {"CN" "T1"}) or (ip.geoip.country eq "VN" and http.request.uri.query ne "") or (ip.geoip.country ne "VN" and http.request.uri.query ne "") or (http.x_forwarded_for contains ".") `
