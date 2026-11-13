# Security Advisory: Unauthenticated Notification Socket Access (mos-notify)

**Severity:** Low–Medium  
**Fixed in:** mos-notify 0.5.3  
**Affected versions:** All versions prior to 0.5.3

## Description

An unauthenticated client could connect to the mos-notify notification socket if the MOS server was exposed publicly (e.g. via a reverse proxy or directly on the internet). The issue granted read-only access to notifications and did not allow modification or execution.

Risk was limited to deployments where the MOS server is reachable from outside the local network, which is not the recommended configuration.

## Fix

Upgrade MOS to the latest version which includes the latest mos-notify version. The notification socket now requires authentication before accepting connections.

## Recommendation

- Update to the latest MOS version immediately.
- Do not expose the MOS server directly to the internet. If external access is required, always use a reverse proxy or NetBird/Tailscale/Wireguard.
