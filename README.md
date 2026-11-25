# obsidian-open

Static HTTPS → `obsidian://open` redirect, for links from Telegram (which hides raw `obsidian://` links).

## Link format

```
https://<user>.github.io/obsidian-open/#file=<path>[&vault=<vault>]
```

- `file` — note path inside the vault, `.md` optional. **Required.**
- `vault` — vault name. Optional; without it Obsidian uses the currently open vault.
- Encode each value with `encodeURIComponent` (Python: `urllib.parse.quote(value, safe="")`). Spaces must be `%20`, not `+`.
- Params go after `#`, so they never reach GitHub's servers or logs.

Example (fictional): `Inbox/Пример заметки.md` in vault `Demo`:

```
https://<user>.github.io/obsidian-open/#file=Inbox%2F%D0%9F%D1%80%D0%B8%D0%BC%D0%B5%D1%80%20%D0%B7%D0%B0%D0%BC%D0%B5%D1%82%D0%BA%D0%B8.md&vault=Demo
```

The page tries to open Obsidian automatically; if the browser blocks it, tap **Открыть в Obsidian**.
