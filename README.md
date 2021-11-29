[![CI](https://github.com/DanielWeeber/ansible-role-windows_exporter/actions/workflows/release.yml/badge.svg?branch=master)](https://github.com/DanielWeeber/ansible-role-windows_exporter/actions/workflows/release.yml)

# Ansible Role: Windows exporter

This role installs Prometheus' [Windows exporter](https://github.com/prometheus/windows_exporter) on Windows hosts.

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    windows_exporter_version: '0.18.1'

The version of Windows exporter to install. Available releases can be found on the [tags](https://github.com/prometheus-community/windows_exporter/tags) listing in the Node exporter repository. Drop the `v` off the tag.

If you change the version, the `windows_exporter` binary will be replaced with the updated version, and the service will be restarted.

    windows_exporter_arch: 'amd64'
    windows_exporter_download_url: https://github.com/prometheus-community/windows_exporter/releases/download/v{{ windows_exporter_version }}/windows_exporter-{{ windows_exporter_version }}-{{ windows_exporter_arch }}.msi


    windows_exporter_bin_path: 'C:\Windows\temp\windows_exporter-{{ windows_exporter_version }}-{{ windows_exporter_arch }}.msi'

The path where the `windows_exporter` binary will be downloaded and installed from.

    windows_exporter_options: ''

Any additional options to pass to `windows_exporter` when it starts, e.g. `--no-collector.wifi` if you want to ignore any WiFi data.

    windows_exporter_state: started
    windows_exporter_enabled: true

Controls for the `windows_exporter` service.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - role: ansible-role-windows_exporter

## License

MIT / BSD

## Author Information

This role was created in 2021 by [Daniel Weeber](https://github.com/DanielWeeber). Heavily inspired and forked from [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
