# MOS Security Advisory #1:  
## Remote Code Execution in NGINX ([nginx2root](https://nginx2root.com))

**Severity:** Critical  
**Fixed in:** MOS 0.6.3-stable  
**Affected versions:** All versions prior to MOS 0.6.3-stable

### Description

Multiple vulnerabilities in NGINX (CVE-2026-123007, CVE-2026-123634, CVE-2026-123633, CVE-2026-121810, CVE-2026-113425) allow an unauthenticated remote visitor to execute arbitrary code on the server. The lead vulnerability, CVE-2026-123007, is a memory corruption bug in NGINX's HTTP/2 handling that has existed since NGINX 1.9.3. When chained with a kernel privilege escalation, this grants root access on the host.

Risk is elevated for any public-facing NGINX deployment, not just those exposed to untrusted networks.

### Fix

Upgrade MOS to the latest version, which includes the latest nginx patch version with all security patches applied.

### Recommendation

- Update to the latest MOS version immediately
- Do not expose the MOS server directly to the internet. If external access is required, always use a reverse proxy or NetBird/Tailscale/Wireguard

***

# MOS Security Advisory #2:
## Unauthenticated Notification Socket Access (mos-notify)

**Severity:** Low–Medium  
**Fixed in:** MOS 0.6.3-stable  
**Affected versions:** All versions prior to MOS 0.6.3-stable

### Description

An unauthenticated client could connect to the mos-notify notification socket if the MOS server was exposed publicly (e.g. via a reverse proxy or directly on the internet). The issue granted read-only access to notifications and did not allow modification or execution.

Risk was limited to deployments where the MOS server is reachable from outside the local network, which is not the recommended configuration.

### Fix

Upgrade MOS to the latest version which includes the latest mos-notify version. The notification socket now requires authentication before accepting connections.

### Recommendation

- Update to the latest MOS version immediately
- Do not expose the MOS server directly to the internet. If external access is required, always use a reverse proxy or NetBird/Tailscale/Wireguard
