---
layout: post
title: "Have to sign your commits, do it like a pro"
date: 2019-06-01 07:23:22 +0200
categories: git github gnupg
---

> This post shares my ❤️ to all **git-related** stuff 

Recently my OSS project I'm involved on introduced security rule enforcing commit signing. Git and [GitHub supports](https://github.blog/2016-04-05-gpg-signature-verification/) commit signing with GPG signing keys. If you ever have forked someone else branch and merge it into master you know that [author and committer](https://stackoverflow.com/questions/18750808/difference-between-author-and-committer-in-git) are two different things. So this is an option to verify commit authenticity and integrity.

### TL;DR
Sneak peek at final result, cool huh?
 ![GitHub screen](/assets/github-screen.png)

### Sign like a PRO
GitHub's help page guides you to setup signing with huge 4096 bits RSA key. Nothing fancy here, old, borring RSA. I'll show you how to use cutting-edge cryptography to signing your commits. We will create Eliptic Curve key based on Ed25519 curve. GitHub accepts these signatures as well, it wouldn't have sense otherwise.

Before we start you should have modern `gpg` tool installed. I ran on 2.2.4, check on you side with `gpg --version` or `gpg2 --version`. I symlinked `gpg` command to point to 2.2.4 version for convenience.

### Create new key for signing purposes

Open terminal and launch `gpg --expert --full-gen-key` here are options I've chosen:

```
Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
...
   (9) ECC and ECC
  (10) ECC (sign only)

Your selection? 10


Please select which elliptic curve you want:
   (1) Curve 25519
   (3) NIST P-256
...
   (9) secp256k1
Your selection? 1
```

For key expiration `0 = key does not expire` is probably fine as we intended to use this key to particular project.

When you set `Real name` and `Email address` to values corresponded to you git configuration for `user.name` and `user.email` git should find your key automaticaly.
This isn't required however because we can specifically select the key to use.

Also don't be reluctant to set strong key protection passphrase. On most sane systems you would need to provide it just once when signing for the first time and it could be remembered then.

Once you have your key created to can follow steps on GitHub's help. I'll provided them here briefly.

### Exporting key to GitHub
`gpg --list-secret-keys --keyid-format LONG` - get key identifier, it should looks like   `    ed25519/->CF91662CAD32FF5F<- 2019-05-31 [SC] [expires: 2022-01-15]`

Export the key in text format and add it in [your profile's setting](https://github.com/settings/keys).
`gpg --armor --export <key-id>`

### Configure git to use the key
`git config --global gpg.program gpg2` use gpg2 everywhere.

Select key to use and sing on commit just for the repository
`git config --global user.signingKey <key-id>`
`git config commit.gpgSign true`

### Check if it works
`git commit --allow-empty -m 'Lets sign this commit message'`

Check the commit
```
git show HEAD --show-signature

commit 2b09-long-commit-sha-8548 (HEAD -> tmp/branch-name)
gpg: Signature made Fri, May 31th 2019, 14:52:15 CEST
gpg:                using EDDSA key 5AC2-long-key-id-FF5F
gpg: Good signature from "First Lastname (optional key description) <me@example.com>" [ultimate]

```

Pushing your branch to GitHub for final check. 
GitHub screen
![GitHub screen](/assets/github-screen.png)

Thanks for reading!