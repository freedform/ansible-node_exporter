# node_exporter

Role node_exporter provides full control over Prometheus node exporter.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [node_exporter_actions](#node_exporter_actions)
  - [node_exporter_bin_dir](#node_exporter_bin_dir)
  - [node_exporter_download_base](#node_exporter_download_base)
  - [node_exporter_download_dir](#node_exporter_download_dir)
  - [node_exporter_extra_flags](#node_exporter_extra_flags)
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

**_Type:_** String<br />

#### Default value

```YAML
node_exporter_bin_dir: /usr/local/bin
```

### node_exporter_download_base

Base URL to download installation artifacts

**_Type:_** String<br />

#### Default value

```YAML
node_exporter_download_base: https://github.com/prometheus/node_exporter/releases/download
```

### node_exporter_download_dir

Destination directory for downloading node exporter binaries

**_Type:_** String<br />

#### Default value

```YAML
node_exporter_download_dir: /tmp
```

### node_exporter_extra_flags

node_exporter command-line flags, keyed by flag name (without leading dashes). This is the
single source for all flags passed to node_exporter, including which address it listens on
(`web.listen-address`, defaults to `:9100` if not set here). Values set here are merged on
top of the role's own defaults, so only the keys you want to change need to be set. A
boolean value renders as `--flag` / `--no-flag` (for `--[no-]collector.*` style toggle
flags); any other value renders as `--flag=value`.

**_Type:_** Dict<br />

#### Default value

```YAML
node_exporter_extra_flags: {}
```

#### Example usage

```YAML
  node_exporter_extra_flags:
    web.listen-address: ":9200"
    web.telemetry-path: /metrics
    collector.processes: true
    collector.ntp: false
    collector.textfile.directory: /var/lib/node_exporter/textfile_collector
```

### node_exporter_state

Target state for the node_exporter daemon

**_Required:_** `true`, only in case `node_exporter_actions: state_control`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  node_exporter_state: started
  node_exporter_state: restarted
```

### node_exporter_user

Linux user name to run node exporter service

**_Type:_** String<br />

#### Default value

```YAML
node_exporter_user: node-exporter
```

### node_exporter_version

Node exporter version to be installed

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
