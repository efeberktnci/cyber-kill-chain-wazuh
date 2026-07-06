# Security Policy

## Scope

This repository contains defensive lab documentation and detection content. All simulations must occur only on systems the operator owns or is explicitly authorized to test.

## Reporting a Security Issue

Do not open a public issue containing credentials, exploitable secrets, personal data, or details that could expose a live environment. Contact the repository owner privately through an appropriate GitHub channel.

## Evidence Handling

- Sanitize hostnames, addresses, usernames, and tokens when disclosure creates risk.
- Do not commit raw packet captures or event-log exports without reviewing their contents.
- Record evidence integrity hashes in the evidence manifest when raw artifacts are retained outside Git.
- Treat screenshots as potentially sensitive data.

