# Copy files between Vagrant and local machine

### Vagrant info

In the directory where the vagrant lives, run the following command:

```bash
vagrant port
```

Example output:

```bash
The forwarded ports for the machine are listed below. Please note that
these values may differ from values configured in the Vagrantfile if the
provider supports automatic port collision detection and resolution.

    22 (guest) => 2222 (host)
  8200 (guest) => 8200 (host)
```

We need the host value from the first line: `2222`.

### Copying local files to vagrant

```
scp -P 2222 /path/to/file.zip vagrant@127.0.0.1:/home/vagrant/.
```

If you are prompted for a password, chances are the password will be: `vagrant`

### Copying vagrant files to local

```
scp -P 2222 vagrant@127.0.0.1:/path/to/file.zip /path/where/to/save/.
```

If you are prompted for a password, chances are the password will be: `vagrant`





