# Generate Secure Random Passwords

There are several ways to generate cryptographically secure passwords in the terminal, depending on the desired format.

## Base64

Generate 32 random bytes encoded as Base64:

```sh
openssl rand -base64 32
```

Produces 44 characters, including padding. Useful when a long, randomly generated secret is needed.

## Hexadecimal

```sh
openssl rand -hex 16
```

Produces 32 hexadecimal characters (`0-9`, `a-f`).

## Alphanumeric

Generate a 24-character password containing letters and digits using Python's `secrets` module:

```sh
python3 -c 'import secrets, string; chars = string.ascii_letters + string.digits; print("".join(secrets.choice(chars) for _ in range(24)))'
```

## Apple-Style Passwords

Apple's default generated passwords contain 20 characters in three groups of six, separated by hyphens, including one uppercase letter and one digit.

A simplified approximation using Python:

```python
import secrets
import string

letters = string.ascii_lowercase
password = [secrets.choice(letters) for _ in range(18)]

digit_pos = secrets.choice([5, 6, 11, 12, 17])
upper_pos = secrets.choice([i for i in range(18) if i != digit_pos])

password[digit_pos] = secrets.choice(string.digits)
password[upper_pos] = password[upper_pos].upper()

print("-".join([
    "".join(password[0:6]),
    "".join(password[6:12]),
    "".join(password[12:18]),
]))
```

This produces the same overall character layout, but does not reproduce Apple's proprietary pronounceable-syllable generation algorithm.

## Security Notes

- OpenSSL and Python's `secrets` module use cryptographically secure randomness.
- Base64 and hexadecimal are encodings, not encryption.
- Longer passwords generally provide more resistance to guessing.
- Avoid logging terminal output containing generated passwords.
- Store generated passwords in a password manager.
