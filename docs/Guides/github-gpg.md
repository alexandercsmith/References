# Github GPG

> Setup GPG Keys for Github Authentication

* [GitHub GPG Documentation](https://help.github.com/en/github/authenticating-to-github/managing-commit-signature-verification)
* [StackOverflow: Resolve GPG Command Error](https://stackoverflow.com/questions/27041885/how-to-resolve-gpg-command-not-found-error-during-rvm-installation)

---

## Check for GPG Keys

Check for Keys:
```bash
$ gpg --list-secret-keys --keyid-format LONG
```

If Error executing command, Install Command Line Tools:
```bash
$ brew install gnupg gnupg2
```

## Create GPG Keys

```bash
$ gpg --full-generate-key
```

* Key: `RSA and DSA`
* Length: `4096`
* Expiration: `Enter`
* User ID
* Passphrase

## List GPG Keys

```bash
$ gpg --list-secret-keys --keyid-format LONG
```

```
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```

* Copy the Key ID of the GPG Key to use

## Access ASCII Armor Format

```bash
$ gpg --armor --export <ID>
```

* Copy GPG Key
  * Beginning: `-----BEGIN PGP PUBLIC KEY BLOCK-----`
  * Ending: `-----END PGP PUBLIC KEY BLOCK-----`
