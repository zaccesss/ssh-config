# Contributing

Thanks for taking an interest. Contributions are welcome: config corrections and
guide improvements.

## What belongs here

- An option OpenSSH no longer accepts or that behaves differently on a platform
- Improvements to the key generation walkthrough
- Improvements to the guides
- Improvements to the guides

## What does not belong here

- An option that only reflects one person's taste rather than something broadly
  useful, keep that in your own copy

## How to contribute

1. Fork the repository and create a branch named `fix/<short-description>` or
   `feat/<short-description>`.
2. Make your change and check it with `ssh -F <platform>/config -G github.com`. Keep the three
   platform files identical except for `UseKeychain`.
3. Open a pull request with a clear title and a one-paragraph description of what changed and
   why. CI parses each config on its real platform and fails on any private key.

## Style rules

> [!IMPORTANT]
> - **Comments**: explain the why, not the what.
> - **Never commit a private key, a real public key or a real host entry.**

## Reporting bugs

Open an issue with your OpenSSH version and platform and platform, what you expected versus what happened.

More about me and my work: [isaacadjei.me](https://isaacadjei.me).
