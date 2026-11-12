# Carbonated — license control

This repo hosts the **revocation list** for the Carbonated Hypixel SkyBlock mod.

The mod checks `carbonated-revoked.json` automatically (on launch and every ~30 minutes)
at this repo's raw URL:

https://raw.githubusercontent.com/fizzlefizzlefizzlefizzle/carbonated-licenses/main/carbonated-revoked.json

## How it works

- Licenses are offline, cryptographically signed keys. There is **no server**.
- This file is the only remote piece: a list of revoked account UUIDs, **signed with the
  owner's private key**. A copy that isn't validly signed is ignored by the mod.
- Only ItsFizzle (the owner, with the private key file on their PC) can produce a valid list.

## Revoking / restoring access

1. In-game: `/carbonated revoke <name>` (or `/carbonated unrevoke <name>` to restore).
   The mod writes a freshly-signed `carbonated-revoked.json` to `config/carbonated/` on the owner's PC.
2. Upload / replace `carbonated-revoked.json` in this repo with that file.
3. Every client applies the change on its next check (≤30 min, or immediately on restart).

`carbonated-revoked.json` here starts empty (no one revoked). Replace it with the real
signed file the first time you run a revoke.

Keep this repo **public** — the raw URL can't be read if it's private.
