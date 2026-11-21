# How to Use RetoSwap on Tails and Whonix: configuration examples

Source: https://monero.love/guides/retoswap-tails-whonix/

These examples are for the article's Whonix DirectBind setup. Install and verify the appropriate RetoSwap release using current upstream instructions. The article includes older version-specific installation commands, so the archived command blocks are not a claim that those versions remain current.

On Whonix-Gateway, merge the Tor fragment into `/usr/local/etc/torrc.d/50_user.conf`. Replace `10.152.152.11` with the Workstation's actual internal address. Validate with `sudo -u debian-tor tor --verify-config` before reloading Tor. Read the generated hostname from `/var/lib/tor/haveno_service/hostname`. Keep the onion private key on the Gateway.

On the Workstation, merge the firewall fragment into `/usr/local/etc/whonix_firewall.d/50_user.conf`, then apply it using `sudo whonix_firewall`. The fragment uses shell variable append syntax and belongs in the Whonix configuration file, not at an ordinary terminal prompt. It permits the peer port 9999, not a management or wallet RPC port.

Replace the hostname placeholder in `haveno.properties.example` and merge the two properties into `~/.local/share/Haveno-reto/haveno.properties` while RetoSwap is stopped. Preserve existing settings. Confirm the same identity after restart. Keep Whonix's normal network layout and verify its documented local SOCKS forwarding at 127.0.0.1:9050.

Do not apply this DirectBind recipe to Tails. Tails uses its own upstream launcher and persistence procedure. No live trade or end-to-end Whonix/Tails routing test was performed for this bundle.

References: [Whonix RetoSwap instructions](https://www.whonix.org/wiki/RetoSwap), [versioned Haveno configuration](https://github.com/haveno-dex/haveno/blob/v1.12.0/common/src/main/java/haveno/common/config/Config.java).

## Files

- `gateway/50_user.torrc.fragment.conf`
- `workstation/50_user.firewall.fragment.conf`
- `workstation/haveno.properties.example`

`ARTICLE-EXAMPLES.md` preserves the published code blocks for context. It is a reference, not a script to execute in one pass. `SOURCE.json` identifies the fetched page and packaged file hashes. No services were installed or restarted when preparing this repository.
