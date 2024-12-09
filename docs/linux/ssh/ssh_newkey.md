# SSH_key nový klíč

1. Pro reset klíče na klientské počítači
```
$ ssh-keygen -R {server.name.com}
$ ssh-keygen -R {ssh.server.ip.address}
$ ssh-keygen -R {ssh.server.ip.address} -f {/path/to/known_hosts}
$ ssh-keygen -R server.example.com
```