# node_exporter

Role node_exported provides full control over Prometheus node exporter.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [node_exporter_actions](#node_exporter_actions)
  - [node_exporter_bin_dir](#node_exporter_bin_dir)
  - [node_exporter_download_base](#node_exporter_download_base)
  - [node_exporter_download_dir](#node_exporter_download_dir)
  - [node_exporter_port](#node_exporter_port)
  - [node_exporter_state](#node_exporter_state)
  - [node_exporter_user](#node_exporter_user)
  - [node_exporter_version](#node_exporter_version)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.20`

## Default Variables

### node_exporter_actions

List of actions the role does, accepts one or more actions.
Use comma without spaces as a delimiter for multiple actions.

**_Required:_** `true`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  node_exporter_actions: install
  node_exporter_actions: install,state_control
```

### node_exporter_bin_dir

PATH directory for installed binary

**_Required:_** `true`, only in case `node_exporter_actions: install`<br />
**_Type:_** String<br />

#### Default value

```YAML
node_exporter_bin_dir: /usr/local/bin
```

### node_exporter_download_base

Base URL to download installation artifacts

**_Required:_** `true`, only in case `node_exporter_actions: install`<br />
**_Type:_** String<br />

#### Default value

```YAML
node_exporter_download_base: https://github.com/prometheus/node_exporter/releases/download
```

### node_exporter_download_dir

Destination directory for downloading node exporter binaries

**_Required:_** `true`, only in case `node_exporter_actions: install`<br />
**_Type:_** String<br />

#### Default value

```YAML
node_exporter_download_dir: /tmp
```

### node_exporter_port

TPC port node exporter uses to expose collected metrics

**_Required:_** `true`, only in case `node_exporter_actions: install`<br />
**_Type:_** String<br />

#### Default value

```YAML
node_exporter_port: 9100
```

### node_exporter_state

TPC port node exporter uses to expose collected metrics

**_Required:_** `true`, only in case `node_exporter_actions: state_control`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  node_exporter_state: started
  node_exporter_state: restarted
```

### node_exporter_user

Linux user name to run node exporter service

**_Required:_** `true`, only in case `node_exporter_actions: install`<br />
**_Type:_** String<br />

#### Default value

```YAML
node_exporter_user: node-exporter
```

### node_exporter_version

Node exporter version to be installed

**_Required:_** `true`, only in case `node_exporter_actions: install`<br />
**_Type:_** String<br />

#### Default value

```YAML
node_exporter_version: 1.10.2
```

## Dependencies

None.

## License

MIT

## Author

freedform
