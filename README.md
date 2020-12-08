# systemctl-service-sample
A service sample file

> This Config file is a basic example on how to execute a script during a boot time and auto-restart program on systemd Linux 

---

> Usage


### Step 1: Create foo.service in /etc/systemd/system
```console
$ cd /etc/systemd/system
```
```console
$ touch apc.service
```

### Step 2: Modify your foo.service file
`Description` : Your app simple description.
`ExecStart` : Your app or shell script path.
`Restart` : Restart [options](https://www.freedesktop.org/software/systemd/man/systemd.service.html) 

| Restart settings/Exit causes | always |  on-success | on-failure | on-abnormal | on-abort | on-watchdog |
| -----------------------------| -------| ----------- | ---------- | ----------- | -------- | ----------- |
| Clean exit code or signal    | *      | *           |			   |	         |          |             |
| Unclean exit code            | *      |             | *          |             |          |             |
| Unclean signal               | *      |             | *          | *           | *        |             |
| Timeout                      | *      |             | *          | *           |          |             |
| Watchdog                     | *      |             | *          | *           |          | *           |    