# systemctl-service-sample
A service sample file

> This Config file is a basic example on how to execute a script during a boot time and auto-restart program on systemd Linux 


## Usage

### Step 1: Create foo.service in /etc/systemd/system
```console
$ cd /etc/systemd/system
```
```console
$ touch foo.service
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

You need to find your `XAUTHORITY` path. 
Just type `echo $XAUTHORITY` to check.
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

### Step 5: Enable Your App Service
```console
$ sudo systemctl enable foo.service
```

### Step 6: Start Your App Service
```console
$ sudo systemctl start foo.service
```

### Step 7: Check your service status
```console
$ sudo systemctl status foo.service
```

---

## service file parameter

`network-online.target`: is a target that actively waits until the nework is "up", where the definition of "up" is defined by the network management software.   [more](https://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/)

## Run Docker As A Service

[reference](https://blog.container-solutions.com/running-docker-containers-with-systemd)
