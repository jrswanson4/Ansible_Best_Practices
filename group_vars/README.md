# Group and Host Variables

Ansible's inventory variables are grouped into two classes of internal categories: `groupvars` and `hostvars`.

The differences are exactly what you would expect. Any high-level info/data that applies to multiple hosts will be contained in `groupvars`, versus per-host details that are specified in your `hostvars`.

Ideally, `groupvars` are obtained from your CMDB. But regardless of whether that data is built automatically by an inventory script, or populated manually in a file, your `groupvars` structure should match 1:1 with our inventory classifications.

Example:

```
group_vars
  ├─ all
  │   ├── ios
  │   │   └── main.yaml
  │   │   └── vault.yaml
  │   │   └── special.yaml
  │   ├── windows
  │   │   └── main.yml
  │   │   └── vault.yaml
  │   │   └── extra.yaml
  │   ├── redhat
  │   │   └── main.yaml
  │   │   └── vault.yaml
  │   │   └── more.yaml
```

And for broader infrastructure projects, this sort of structure also scales quite well:

```
group_vars
  │  ├── all
  │  │   ├── network
  │  │   │   ├── ios
  │  │   │   ├── nxos
  │  │   │   ├── junos
  │  │   ├── provisioning
  │  │   │   ├── azure
  │  │   │   ├── redhat
  │  │   ├── redhat
  │  │   │   ├── services
  │  │   │   ├── apps
  │  │   ├── windows
  │  │   │   ├── services
  │  │   │   ├── apps
```
