# Punch Skill Registry

The official package index for [Punch](https://github.com/humancto/punch) skills.

## How It Works

This repository is a Git-based index (similar to crates.io-index). When you run
`punch move install <skill-name>`, the Punch CLI clones/pulls this index to
resolve versions, verify checksums, and validate Ed25519 signatures.

## Publishing a Skill

1. Create a skill directory with a `SKILL.md` file
2. Generate a signing keypair: `punch move keygen`
3. Validate your skill: `punch move scan ./my-skill/`
4. Publish: `punch move publish ./my-skill/`

The skill is scanned for security issues (20+ rules), packaged as a signed
tarball, and submitted as a PR to this repository.

## Index Format

Skills are stored using a two-character prefix routing scheme:

- `skills/co/code-reviewer.json`
- `skills/we/web-search.json`
- `skills/pr/productivity.json`

Each JSON file contains version history, checksums, signatures, and scan results.

## Security

Every skill in this registry is:

- **Scanned** — 20+ security rules check for prompt injection, credential
  harvesting, data exfiltration, and reverse shells
- **Signed** — Ed25519 signatures prevent tampering
- **Checksummed** — SHA-256 verification on install
- **Size-limited** — 100KB max per skill package

## License

MIT
