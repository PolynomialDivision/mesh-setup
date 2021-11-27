**This is derived from [bbb-configs](https://github.com/Freifunk-Spalter/bbb-configs).**

# Mountains Mesh (Ansible Config Management)

### How to get started

```
pip3 install -r requirements.txt
```

### How to spin up a config run (generate only, output path is /tmp/configs/..:

```
ansible-playbook play.yml
```

### How to spin up a config run and generate images

```
ansible-playbook play.yml --tags image
```

### How to limit image creation to a single location

```
ansible-playbook play.yml --limit example-core
ansible-playbook play.yml --limit example-*
```

### How to spin up a config run, generate image and flash (Requires IPv6 Connectivity from inside freifunk network, not yet fully working)

```
ansible-playbook play.yml --tags flash
```

### Whats required to bringup a location?

```
/group_vars : Create location folder
/host_vars : Create host folder for every openwrt device
Done!

```

### Avarange: How to deploy images?

Add ssh config to `/ssh_config` that match your configured hostname (e.g. `mountain-ap101`).

```
Host mountain-ap101
    Hostname 10.12.2.101
    User root
```

Make sure that the device has `python3` installed, since it is required for using ansible remotely!

Than just run:

```
ansible-playbook deploy.yml
```

(Attention: The sysupgrade might not register that it was successfully and loop forever.)