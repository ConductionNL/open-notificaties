# Single-server deployment

This directory contains the tooling to deploy Open Notificaties against a single
server. It has been tested with Debian 9 and 10.

The application is deployed as docker containers, and the playbook will
set up all the required dependencies.

## Requirements

* Debian 9/10 server with root access (see [testserver](#testserver))
* SSH access (with the root user)
* A python virtualenv with the [requirements](../requirements.txt) installed
* Ansible-vault password to decrypt `vars/secrets.yml`

## Deploying

Keep your secrets out of this repository, and symlink the files:

```shell
[user@host]$ ln -s /path/to/secrets.yml ./vars/open-notificaties.yml
```

For maximum security, we recommend you to Ansible-Vault encrypt the secrets.

Add secrets to the `vars/secrets.yml` encrypted with Ansible-vault.
You can use `vars/secrets.yml.example` as an example of the content.

```shell
[user@host]$ ansible-vault create vars/secrets.yml
```

Run the Ansible playbook:

```shell
[user@host]$ ansible-galaxy install -r requirements.yml
[user@host]$ ansible-playbook open-zaak.yml --ask-vault-pass
```
