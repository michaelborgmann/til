# Redirecting stdout and stderr in the Shell

Unix commands use two output streams: **stdout (1)** for normal output and **stderr (2)** for errors.

Redirecting output with `>` only captures stdout:

```sh
ls /tmp /nonexistent > output.txt
```

## Redirect Both Streams

```sh
ls /tmp /nonexistent > output.txt 2>&1
```

`2>&1` redirects stderr to the current destination of stdout:

- `2` — stderr (file descriptor 2)
- `>` — redirection
- `&` — refers to a file descriptor rather than a filename
- `1` — stdout (file descriptor 1)

## Display and Save Output

Use `tee` to display output while saving it:

```sh
ls /tmp /nonexistent 2>&1 | tee output.txt
```

Use `tee -a` to append instead of overwrite.

## Save the Command and Its Output

Enable shell tracing to capture the executed command alongside its output:

```sh
{
    set -x
    ls /tmp /nonexistent
    set +x
} 2>&1 | tee output.txt
```

Traced commands are prefixed with `+` and shown after shell expansion.

## Record a Terminal Session

Use `script` to record an entire interactive session:

```sh
script session.log
```

Run commands normally and type `exit` to stop recording. Review recordings for sensitive information and control characters before sharing.

## Quick Reference

| Syntax | Purpose |
|---|---|
| `> file` | Redirect stdout |
| `2> file` | Redirect stderr |
| `2>&1` | Redirect stderr to stdout's destination |
| `>> file` | Append stdout |
| `tee file` | Display and save output |
| `set -x` | Trace shell commands |
| `script file` | Record a terminal session |
