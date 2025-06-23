# Detailed

The files in this folder depict specific censorship behavior by censors in China, Iran, and Russia. Below, we interpret the censorship behavior seen in each file:

`mozilla.cloudflare-dns.com` and `firefox.dns.nextdns.io` are the encrypted DNS servers pre-defined in Firefox.

#### china_encrypted_dns
China blocks ClientHello with SNI `mozilla.cloudflare-dns.com` (behavior as described for MB-New, [Niere et al.](https://ris.uni-paderborn.de/download/59824/59826/TLS_Obscurity.pdf)) but not `firefox.dns.nextdns.io`.

#### china_firefox_nextdns
China allows a full TLS handshake to `firefox.dns.nextdns.io`.

#### china_quicdns
China does not block QUIC InitialPackets with SNI `firefox.dns.nextdns.io` but with SNI `mozilla.cloudflare-dns.com` (behavior as described in [Heitmann et al.](https://upb-syssec.github.io/blog/2025/quic-china/))

#### germany_cloudflare
Ground-truth ECH connections with cloudflare from Germany. Cloudflare requires the outer SNI to be cloudflare-ech.com in TLS 1.3 and QUIC. Other connections are rejected.

#### iran_encrypted_dns
Iran censors `mozilla.cloudflare-dns.com` and `firefox.dns.nextdns.io` in TLS SNI (`TCP RST`), DNS (blockpage injection), and HTTP GET requests (blockpage injection). TLS censorship as described by [Niere et al.](https://ris.uni-paderborn.de/download/59824/59826/TLS_Obscurity.pdf), DNS and HTTP censorship as described by [Lange et al.](https://www.petsymposium.org/foci/2025/foci-2025-0002.pdf)

#### russia_ech_cloudflare
Russia blocks ECH to Cloudflare servers if the outer SNI is set to `cloudflare-ech.com` Blocking is realized by dropping the `ClientHello` message as described by [ValdikSS](https://github.com/net4people/bbs/issues/393#issuecomment-2461603654). 

#### russia_ech_non_cloudflare
Russia does not block ECH to non-Cloudflare servers even if the outer SNI is set to `cloudflare-ech.com`.

### russia_ech_cloudflare_fragmentation
Russia can reassemble and censor TCP segmented ald TLS record fargmented `ECH ClientHello` messages.