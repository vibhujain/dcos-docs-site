---
layout: layout.pug
navigationTitle: dcos storage provider list
title: dcos storage provider list
menuWeight: 0
notes: Code generated by docgen.go, DO NOT EDIT
enterprise: true
origin: github.com/mesosphere/dcos-storage/cli/pkg/cmd/cmd_provider_list.go
excerpt: List existing volume providers.
---

## dcos storage provider list

List existing volume providers.

### Synopsis

List existing volume providers.

```bash
dcos storage provider list [flags]
```

### Examples

1. Create two volume providers then list them:

```bash
cat <<EOF | dcos storage provider create
{
    "name": "ssds",
    "spec": {
        "plugin": {
            "name": "lvm",
            "config-version": "latest"
        },
        "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S2",
        "plugin-configuration": {
            "devices": ["xvdb", "xvdc"]
        },
        "labels": {"rotational": "false"}
    }
}
EOF

cat <<EOF | dcos storage provider create
{
    "name": "spinning-rust",
    "spec": {
        "plugin": {
            "name": "lvm",
            "config-version": "latest"
        },
        "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
        "plugin-configuration": {
            "devices": ["xvde", "xvdf"]
        },
        "labels": {"rotational": "true"}
    }
}
EOF
```
```bash
dcos storage provider list
```
```
PLUGIN  NAME           NODE                                     STATUS
lvm     ssds           c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S2  ONLINE
lvm     spinning-rust  c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  ONLINE
```
```bash
dcos storage provider list --json
```
```
{
    "providers": [
        {
            "name": "ssds",
            "spec": {
                "plugin": {
                    "name": "lvm",
                    "config-version": 1
                },
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S2",
                "plugin-configuration": {
                    "devices": [
                        "xvdb",
                        "xvdc"
                    ]
                },
                "labels": {
                    "rotational": "false"
                }
            },
            "status": {
                "state": "ONLINE",
                "nodes": [
                    "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S2"
                ],
                "asset-id": "dfgj9sdfg7s9dfg"
            }
        },
        {
            "name": "spinning-rust",
            "spec": {
                "plugin": {
                    "name": "lvm",
                    "config-version": 1
                },
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "plugin-configuration": {
                    "devices": [
                        "xvde",
                        "xvdf"
                    ]
                },
                "labels": {
                    "rotational": "true"
                }
            },
            "status": {
                "state": "ONLINE",
                "nodes": [
                    "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1"
                ],
                "asset-id": "lkjsdoguosd9g8"
            }
        }
    ]
}
```
```bash
dcos storage provider list --name ssds --json
```
```
{
    "providers": [
        {
            "name": "ssds",
            "spec": {
                "plugin": {
                    "name": "lvm",
                    "config-version": 1
                },
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S2",
                "plugin-configuration": {
                    "devices": [
                        "xvdb",
                        "xvdc"
                    ]
                },
                "labels": {
                    "rotational": "false"
                }
            },
            "status": {
                "state": "ONLINE",
                "nodes": [
                    "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S2"
                ],
                "asset-id": "dfgj9sdfg7s9dfg"
            }
        }
    ]
}
```

### Options

Name | Description
--- | ---
`--json` | Display the list of volume providers in json format.
`-n`,`--name` stringArray | Only show the named provider. May be specified multiple times.
`--node` string | Only show local volume providers on node.
`--plugin` string | Only show providers of the specified plugin.

### Options inherited from parent commands

Name | Description
--- | ---
`-h`,`--help` | Help for this command.
`--timeout` duration | Override the default operation timeout. (default 55s)
`-v`,`--verbose` | Verbose mode.
