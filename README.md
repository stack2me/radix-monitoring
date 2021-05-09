# ansible-radix

Roles of Ansible for monitor Radix node.

## System requirements

- Ubuntu 18 or newest

## Roles:

- **common** - preparing system and install dependencies
- **radix-monitor** - preparing for exporting metrics
- **prometheus-node-exporter** - exporter for hardware and OS metrics exposed
## Functional

- Node Monitoring
  - Install netdata for realtime status <host>/netdata
  - install prometheus-node-exporter for collect metrics
    - collecting data about node status(node diff, total validators, if your node became validator, current epoch)
- Install nginx for close entry poins of monitoring systems
- Install and sync ntp server for avoid time shift

* System upgrade

## Installation

- Pull repository
- Add your host to `hosts` file
- Change role for installation (common should be always)
- Change nginx user/password for basic_auth in `vars/variables.yml`
- Run ansible: `ansible-playbook radix.yaml -i hosts.yaml --ask-become-pass -v --ask-pass`

## Custom metrics in prometheus-node-exporter

- **rx_total_next_validators** - next epoch validators
- **rx_total_current_validators** - current epoch validators
- **rx_epoch_progress** - current epoch progress
- **rx_epoch_num** - epoch number
- **rx_epoch_sign** - node epoch signs
- **rx_tps** - network tps
- **rx_tps_mem** - network tps mem
- **rx_diff** - node diff


## Example Dashboard based on prometheus-node-exporter

![Alt text](images/dashboard.png?raw=true "Radix dashboard")
