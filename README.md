# dating-public-data-test

Test pool repo for [dating.dev](https://dating.dev).

## Structure

```
users/{hash}.bin             Encrypted user profiles
matches/{pair_hash}/         Matched pairs
relationships/{pair_hash}/   Committed relationships
```

## .bin Format

```
[32 bytes ed25519 public key][NaCl box encrypted profile data]
```

The public key is used by the relay server for challenge-response authentication. The encrypted data can only be decrypted by the user who holds the corresponding private key.

## How Users Join

1. User runs `dating pool join` from the CLI
2. OAuth authenticates the user (GitHub or Google)
3. CLI creates encrypted `.bin` and opens a PR
4. Pool operator reviews the PR (decrypts identity proof) and merges
5. User is now registered — can discover, match, and chat

