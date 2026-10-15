# Connect via SSH Without Saving Host Keys

By default, SSH stores a server's host key in `~/.ssh/known_hosts`. For temporary connections, you can prevent SSH from saving that entry:

```sh
ssh \
  -o UserKnownHostsFile=/dev/null \
  -o GlobalKnownHostsFile=/dev/null \
  -o StrictHostKeyChecking=ask \
  -o UpdateHostKeys=no \
  user@192.0.2.10
```

## Options

- `UserKnownHostsFile=/dev/null` — Discards user-level known-host entries.
- `GlobalKnownHostsFile=/dev/null` — Ignores system-wide known-host files.
- `StrictHostKeyChecking=ask` — Prompts before accepting an unknown host key.
- `UpdateHostKeys=no` — Disables learning additional host keys.

SSH may still display a message saying the host was permanently added. However, the configured destination is `/dev/null`, so the entry is not saved.

**Note:** Always verify the server's fingerprint before accepting it. Without a saved host key, SSH cannot detect unexpected key changes on subsequent connections.

This prevents persistent known-host entries, not all SSH artifacts. Shell history and authentication logs may still record the connection.
