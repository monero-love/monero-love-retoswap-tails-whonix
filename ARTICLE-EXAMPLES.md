# Published examples

Source: https://monero.love/guides/retoswap-tails-whonix/

Read the article for the ordering, prerequisites and version limits of these separate examples.

## Block 1

```text
sudo apt update
sudo apt full-upgrade
```

## Block 2

```text
sudo apt install --no-install-recommends curl gnupg
```

## Block 3

```text
umask 077
mkdir -p "$HOME/Downloads/haveno-verify"
cd "$HOME/Downloads/haveno-verify"
RETO_BASE='https://github.com/retoaccess1/haveno-reto/releases/download/v1.12.0-reto'
RETO_FILE='haveno-v1.12.0-linux-x86_64-installer.deb'
curl --fail --location --remote-name "$RETO_BASE/$RETO_FILE"
curl --fail --location --remote-name "$RETO_BASE/$RETO_FILE.sig"
curl --fail --location --output reto_public.asc https://retoswap.com/reto_public.asc
mkdir -m 700 verify-keyring
gpg --homedir ./verify-keyring --import reto_public.asc
gpg --homedir ./verify-keyring --fingerprint
gpg --homedir ./verify-keyring --verify "$RETO_FILE.sig" "$RETO_FILE"
```

## Block 4

```text
sudo apt install /home/user/Downloads/haveno-verify/haveno-v1.12.0-linux-x86_64-installer.deb
```

## Block 5

```text
ip -4 addr
```

## Block 6

```text
sudoedit /usr/local/etc/torrc.d/50_user.conf
```

## Block 7

```text
HiddenServiceDir /var/lib/tor/haveno_service/
HiddenServicePort 9999 10.152.152.11:9999
```

## Block 8

```text
sudo -u debian-tor tor --verify-config
sudo systemctl reload tor@default.service
sudo systemctl status tor@default.service
sudo cat /var/lib/tor/haveno_service/hostname
```

## Block 9

```text
sudoedit /usr/local/etc/whonix_firewall.d/50_user.conf
```

## Block 10

```text
EXTERNAL_OPEN_PORTS+=" 9999 "
```

## Block 11

```text
sudo whonix_firewall
```

## Block 12

```text
read -r -p 'Gateway onion hostname: ' HAVENO_ONION
/opt/haveno/bin/Haveno --hiddenServiceAddress="$HAVENO_ONION" --nodePort=9999
```

## Block 13

```text
curl --fail --max-time 60 --socks5-hostname 127.0.0.1:9050 \
  https://check.torproject.org/api/ip
```

## Block 14

```text
ip route
ss -lntp
curl --fail --max-time 60 https://check.torproject.org/api/ip
```

## Block 15

```text
cd "$HOME/Persistent"
curl --fail --location --output haveno-install.sh \
  https://raw.githubusercontent.com/haveno-dex/haveno/v1.12.0/scripts/install_tails/haveno-install.sh
less haveno-install.sh
bash haveno-install.sh \
  https://github.com/retoaccess1/haveno-reto/releases/download/v1.12.0-reto/haveno-v1.12.0-linux-x86_64-installer.deb \
  DAA24D878B8D36C90120A897CA02DAC12DAE2D0F
```
