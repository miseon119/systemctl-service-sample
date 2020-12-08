# systemctl-service-sample
A service sample file

> This Config file is a basic example on how to execute a script during a boot time and auto-restart program on systemd Linux 


## Usage
---


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


`RestartSec`: Time to sleep before restarting a service.
`StartLimitIntervalSec` `StartLimitBurst` [reference](https://www.freedesktop.org/software/systemd/man/systemd.service.html) 

+ If your app needs to display GUI window, you need to add `Environment`.
```
Environment="DISPLAY=:0"
```

You need to find your `XAUTHORITY` path. Just type `echo $XAUTHORITY` to check.
```
Environment="XAUTHORITY=/yourPath/Xauthority"
```

### Step 3
```console
$ sudo chmod 755 foo.service
```

### Step 4
```console
$ sudo systemctl  daemon-reload
```

### Step 5: Start Your App Service
```console
$ sudo systemctl start foo.service
```

### Step 6: Check your service status
```console
$ sudo systemctl status foo.service
```
