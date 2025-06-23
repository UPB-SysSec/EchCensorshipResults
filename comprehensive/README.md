# Comprehensive

The files in this folder contain overall measurements of ECH censorship in China, Iran, and Russia. Measurements were taken from vantage points inside the country to a server specified in the file name.

[Cloudflare IP Ranges](https://www.cloudflare.com/ips/)

## `cf_cdn.pcapng/txt`, `cf_single_ip.pcapng/txt`, `vps.pcapng/txt`

These files contain network traffic and summarizing results of ECH requests sent from the censoring country to the specified vantage point outside the censoring country. 
- `cf_cdn`: Connections to a Cloudflare IP that is part of their official IP ranges
- `cf_single_ip`: Connections to a Cloudflare IP that hosts a single server, not part of Clouflare's official IP ranges.
- `vps`: Connections to a server not part of Cloudflare's official IP ranges.
