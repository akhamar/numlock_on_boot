# Auto NumLock at console startup (tty)

## Binary

> nano /usr/local/bin/numlock

```bash
#!/bin/bash

for tty in /dev/tty{1..6}
do
    /usr/bin/setleds -D +num < "$tty";
done
```

```bash
chmod 755 /usr/local/bin/numlock
```

## Service

> nano /etc/systemd/system/numlock.service

```bash
[Unit]
Description=numlock

[Service]
ExecStart=/usr/local/bin/numlock
StandardInput=tty
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

```bash
systemctl enable numlock.service
```
