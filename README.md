# ansible-role-openssh

Sensible and secure defaults for OpenSSH server.

## Defaults

The defaults provided in this role are compliant with the [Mozilla Modern](https://infosec.mozilla.org/guidelines/openssh) for OpenSSH 6.7+

If you are running this role with older versions of OpenSSH, such as version 5.3 on RHEL or CentOS 6, you will need to override the defaults elsewhere (i.e. in your `group_vars` or `host_vars`). Below are a few Mozzila recommendations.

### Mozilla Modern
This is the default in this role.

```yaml
openssh_kexalgorithms:
  - curve25519-sha256@libssh.org
  - ecdh-sha2-nistp521
  - ecdh-sha2-nistp384
  - ecdh-sha2-nistp256
  - diffie-hellman-group-exchange-sha256

openssh_ciphers:
  - chacha20-poly1305@openssh.com
  - aes256-gcm@openssh.com
  - aes128-gcm@openssh.com
  - aes256-ctr
  - aes192-ctr
  - aes128-ctr

openssh_macs:
  - hmac-sha2-512-etm@openssh.com
  - hmac-sha2-256-etm@openssh.com
  - umac-128-etm@openssh.com
  - hmac-sha2-512
  - hmac-sha2-256
  - umac-128@openssh.com
```

### Mozilla Intermediate
```yaml
openssh_hostkeys:
  - /etc/ssh/ssh_host_rsa_key
  - /etc/ssh/ssh_host_ecdsa_key

ssh_kexalgorithms:
  - diffie-hellman-group-exchange-sha256

ssh_ciphers:
  - aes256-ctr
  - aes192-ctr
  - aes128-ctr

ssh_macs:
  - hmac-sha2-512
  - hmac-sha2-256
```
