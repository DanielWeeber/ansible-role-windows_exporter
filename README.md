[![CI](https://github.com/DanielWeeber/ansible-role-windows_exporter/actions/workflows/release.yml/badge.svg?branch=master)](https://github.com/DanielWeeber/ansible-role-windows_exporter/actions/workflows/release.yml)

# Ansible Role: Windows exporter

This role installs Prometheus' [Windows exporter](https://github.com/prometheus/windows_exporter) on Windows hosts.

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    windows_exporter_version: '0.18.1'

The version of Windows exporter to install. Available releases can be found on the [tags](https://github.com/prometheus-community/windows_exporter/tags) listing in the Windows exporter repository. Drop the `v` off the tag.

If you change the version, the `windows_exporter` binary will be replaced with the updated version, and the service will be restarted.

    windows_exporter_arch: 'amd64'
    windows_exporter_download_url: https://github.com/prometheus-community/windows_exporter/releases/download/v{{ windows_exporter_version }}/windows_exporter-{{ windows_exporter_version }}-{{ windows_exporter_arch }}.msi


    windows_exporter_bin_path: 'C:\Windows\temp\windows_exporter-{{ windows_exporter_version }}-{{ windows_exporter_arch }}.msi'

The path where the `windows_exporter` binary will be downloaded and installed from.

    windows_exporter_listen_address: '0.0.0.0'
    windows_exporter_listen_port: 9182
    windows_exporter_textfile_dir: null

Commonly used service options.

    windows_exporter_options: ''

Any additional options to pass to `windows_exporter` when it starts, e.g. `--no-collector.wifi` if you want to ignore any WiFi data.
Need to use MSI Parameters as stated in https://github.com/prometheus-community/windows_exporter#installation

    windows_exporter_state: started
    windows_exporter_start_mode: delayed

Controls for the `windows_exporter` service. `windows_exporter_start_mode` controls the [start_mode](https://docs.ansible.com/ansible/latest/collections/ansible/windows/win_service_module.html#parameter-start_mode) of the service. `windows_exporter_state` controls the [state](https://docs.ansible.com/ansible/latest/collections/ansible/windows/win_service_module.html#parameter-state) of the service on the host.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - role: danielweeber.windows_exporter

## License

MIT / BSD

## Author Information

This role was created in 2021 by [Daniel Weeber](https://github.com/DanielWeeber). Heavily inspired and forked from [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
