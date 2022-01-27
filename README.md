# Ansible Role: Stripper:Source

[![builds.sr.ht status](https://builds.sr.ht/~tleguern/ansible-role-stripper-source.svg)](https://builds.sr.ht/~tleguern/ansible-role-stripper-source?)

An Ansible role that installs and configures the Stripper:Source Metamod plugin.

Automatic testing is provided using molecule's delegated driver and <https://builds.sr.ht>.

## Requirements

An ansible role dedicated to the installation of SteamCMD such as [ansible-steamcmd](https://github.com/tleguern/ansible-steamcmd).

An ansible role dedicated to the installation of Metamod:Source such as [ansible-role-metamod-source](https://github.com/tleguern/ansible-role-metamod-source).

An ansible role dedicated to the installation of _Left4Dead2_, _Day of Defeat: Source_, _Counter-Strike: Source_ or any other game based on the Source engine providing the `Restart source games` handler.

## Role Variables

### Variables inherited from other roles

| Variable | Description | Default |
|----------|-------------|---------|
| `steamcmd_user` | User name for steamcmd | `steam` |
| `metamod_source_install_path` | Metamod:Source installation path | mandatory |

### Native variables

| Variable | Description | Default |
|----------|-------------|---------|
| `stripper_source_url` | HTTP URL for the project downloads | `http://www.bailopan.net/stripper/files` |
| `stripper_source_version` | Project's desired version | `1.2.2` |
| `stripper_source_target` | Archive name | `stripper-{{ stripper_source_version }}-linux.tar.gz` |
| `stripper_source_global_filters` | Main Stripper:Source configuration file | `""` |
| `stripper_source_maps_cfg` | Map specific configuration file | `[]` |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: game
  vars:
    cstrike_source_ip: 127.0.0.1
    cstrike_source_server_cfg: |
      hostname "My custom CS:S server"
    metamod_source_install_path: /home/steam/cstrike-source/cstrike
    stripper_source_global_filters: |
      ...
    stripper_source_maps_cfg:
      - name: de_dust2
        config: |
          add:
          {
            "classname" "prop_dynamic"
            "origin" "1376 3168 -112"
            "model" "models/props_office/vending_machine01.mdl"
          }
  roles:
    - role: tleguern.steamcmd
    - role: tleguern.cstrike_source
    - role: tleguern.metamod_source
    - role: ansible-role-stripper-source
```

## License

ISC

## Contributing

Either send [send GitHub pull requests](https://github.com/tleguern/ansible-role-stripper-source) or [send patches on SourceHut](https://lists.sr.ht/~tleguern/misc).

## Author Information

Tristan Le Guern <tleguern@bouledef.eu>
