# Github SSH

> Setup SSH Keys for Github Authentication

* [Github: Connect to GitHub with SSH](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
* [DevConnected: How to Setup SSH Keys on GitHub](https://devconnected.com/how-to-setup-ssh-keys-on-github/)

---

## Generate SSH Key

```bash
# Navigate to SSH Directory
$ cd ~/.ssh/

# Generate SSH Keys using RSA Algorithm and GitHub Email
$ ssh-keygen -t rsa -b 4096 -C "name@email.com"
```

### Prompt
* File Name: Leave Blank for SSH Key to be added to `id_rsa`
* Passphrase: Leave Blank for Non-prompt when Executing Operation
* Passphrase Confirmation

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/schkn/.ssh/id_rsa): custom_id_rsa
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in custom_id_rsa.
Your public key has been saved in custom_id_rsa.pub.
The key fingerprint is:
SHA256:6yBEAZCCAZCAfdeokgo256452574ffaaz+F6dedefr23222CUXTQc email@example.com
The key's randomart image is:
+---[RSA 4096]----+
|@*o+=+.   E..    |
|*+.+o    o .     |
|... =.  ....     |
| . + =. ..o      |
|  . *.o.S  .     |
|   . o.= =  .    |
|    . o o.+.     |
|     . o.oo      |
|        =*o      |
+----[SHA256]-----+
```

### Configure SSH Keys

* If Public Key file is custom name, configure SSH Client

Create Config File
```bash
# Create `config` file in ./ssh Directory
$ touch ~/.ssh/config

# Open File for Update
$ sudo nano ~/.ssh/config
```

Add Config Options
```
Host *
    Hostname github.com
    User git
    IdentityFile ~/.ssh/custom_id_rsa
```

## Add SSH to SSH-Agent

Start `ssh-agent` in background
```bash
$ eval "$(ssh-agent -s)"
> Agent pid 59555
```

Add SSH Key to SSH-Agent
```bash
$ ssh-add -K ~/.ssh/custom_key
```

## Add SSH Keys to GitHub

* Navigate to `SSh and GPG Keys` in GitHub Settings
* Click `New SSH Key` Button

```bash
# Get Contents of Public Key
$ cat ~/.ssh/custom_id_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQC+HvRnxwPJyUiUO/UCPKrW6mFPgJF8LxsC2lbBePtn+UDv4Xy+eMJRgG5fbaqy2i0tvP+7T7bjVWCXJGIYunPbH978H4jrebF6Ts+dsgel4+ALf3wkT6nAJkmPDSk3qHleBbjKP1UtO9AAIlclkIVeu5LmV7RaE8H78VXxGVQLcWXvlS0SGlwIxXXd9hBeGh6qPmrya63Ezrt/J1fNy6Ro9s5+ndLogBG2G0JKdAoytbCIBgPmm6sK9nvv3kHrjSK4S0rRz0nb9oaxCQF6V+T75hPgYp+JMOl8yZZMGLN3GPadE2ye2/lskJXzYjlHyjAE6a0g+vrHmMjOULPUrO+aHEA84f   email@example.com
```

* Add New SSH Key to GitHub Account
* Ensure `read` and `write` permission are set correctly
