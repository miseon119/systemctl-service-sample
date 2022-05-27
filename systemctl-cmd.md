# Systemctl Service Command

## Check Service list

```bash
sudo systemctl list-units
sudo systemctl list-unit-files
```

enabled/failed/active/running service list:
```bash
sudo systemctl list-units --state=enabled
sudo systemctl list-units --state=failed
sudo systemctl list-units --state=active
sudo systemctl list-units --all --state=inactive
sudo systemctl list-units --type=service --state=running
```

others
```bash
sudo systemctl is-active nginx
sudo systemctl is-enabled nginx
```

[more](https://www.lesstif.com/system-admin/systemd-system-daemon-systemctl-24445064.html)
