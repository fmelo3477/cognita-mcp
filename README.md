<p align="center">
  <img src="icon.png" alt="Cognita" width="96" height="96">
</p>

<h1 align="center">Cognita</h1>

<p align="center">
  A remote <a href="https://modelcontextprotocol.io">MCP</a> server with 51 read-only, keyless tools that AI agents use to research a website, domain or IP: web security, DNS, TLS, email, OSINT and threat intel.
</p>

<p align="center">
  <a href="https://cognita.fmelo.net">Live demo</a> ·
  <a href="https://fmelo.net">fmelo.net</a> ·
  <a href="https://registry.modelcontextprotocol.io/v0/servers?search=net.fmelo/cognita">MCP Registry</a> ·
  <code>https://cognita.fmelo.net/mcp</code>
</p>

---

## What it is

Cognita gives an AI assistant the reconnaissance toolkit a security analyst would reach for, so you can investigate a domain, IP or certificate in plain language without leaving your chat.

- **Remote and hosted** — nothing to install or run locally.
- **No API key, no sign-in** — connect and use it.
- **Read-only** — the tools look things up; none of them changes anything on your side.
- **51 tools** — from a single DNS lookup to a one-shot `investigate` that combines several checks.

## Connect

The endpoint is `https://cognita.fmelo.net/mcp` (streamable HTTP, no authentication).

**Claude Code**

```bash
claude mcp add --transport http cognita https://cognita.fmelo.net/mcp
```

**Claude (web / desktop)** — add a custom connector and paste the URL above.

**Cursor** — `~/.cursor/mcp.json`

```json
{
  "mcpServers": {
    "cognita": { "url": "https://cognita.fmelo.net/mcp" }
  }
}
```

**VS Code** — `.vscode/mcp.json`

```json
{
  "servers": {
    "cognita": { "type": "http", "url": "https://cognita.fmelo.net/mcp" }
  }
}
```

**Any other MCP client** that supports remote (streamable HTTP) servers: point it at the URL.

Client configuration formats change between versions; if one of the snippets above does not work, check your client's documentation for adding a remote MCP server.

## Try it

Once connected, ask your assistant things like:

- *"Investigate example.com and summarise the security posture."*
- *"Check SPF, DKIM and DMARC for example.com. Could someone spoof this domain?"*
- *"Is the TLS certificate on example.com healthy? When does it expire?"*
- *"Is 203.0.113.7 on any blocklist, and what network does it belong to?"*
- *"Is CVE-2024-3094 in CISA's KEV catalog? What's its EPSS score?"*
- *"Find look-alike domains for example.com."*

## Tools

| Area | Tools |
|---|---|
| **One-shot** | `investigate`, `host_exposure`, `scan_site` |
| **DNS** | `dns_lookup`, `dns_propagation`, `reverse_dns`, `passive_dns`, `caa_dnssec`, `mx_lookup`, `zone_transfer_check` |
| **TLS and certificates** | `tls_certificate`, `tls_posture`, `cert_transparency`, `ct_org_search`, `cert_revocation`, `hsts_preload_check` |
| **Email security** | `email_posture`, `spf_check`, `spf_expand`, `dkim_lookup`, `dmarc_check`, `spoofability`, `email_header_analyzer` |
| **IP and domain reputation** | `ip_reputation`, `ip_reputation_aggregate`, `ip_blocklist_check`, `blacklist_check`, `dshield_ip_check`, `feodo_c2_check`, `tor_exit_check`, `tranco_rank` |
| **Network** | `asn_geoip`, `asn_prefixes`, `asn_relations`, `rpki_validation`, `geo_route` |
| **Registration and contacts** | `rdap`, `abuse_contact`, `disclosure_contacts`, `security_txt` |
| **Vulnerability intelligence** | `cve_lookup`, `cve_triage`, `kev_check`, `epss_score` |
| **Web and history** | `robots_sitemap`, `wayback_snapshot`, `wayback_urls`, `urlscan_lookup` |
| **Related assets and abuse** | `related_domains`, `subdomain_takeover_check`, `typosquat_scan` |

Your client lists each tool with its description and parameters when it connects.

## Notes on use

Most tools query public data sources (DNS, certificate logs, public blocklists, vulnerability feeds). A few, such as `scan_site`, `zone_transfer_check` and `typosquat_scan`, make requests towards the target you name. Use Cognita only on domains, hosts and networks you own or are authorised to assess.

## Listing

Published in the official MCP Registry as `net.fmelo/cognita`.

## Contact

Built by [Fernando Melo](https://fmelo.net) · [fmelo.net](https://fmelo.net)

Security contact: see [`security.txt`](https://fmelo.net/.well-known/security.txt).
