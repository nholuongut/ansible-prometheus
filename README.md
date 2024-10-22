# Ansible Prometheus
![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

Ansilbe playbook for installing Prometheus monitoring system.

Playbook installs and manages services using systemd. Currently supported:
  - Prometheus
  - Node Exporter (collects metrics of host machine)
  - Alert manager
  - Push gateway
  - SNMP exporter
  - Blackbox exporter

Playbook includes extensive configuration options check default/main.yml

Installation
------------

ansible-galaxy install ernestas-poskus.ansible-prometheus

Requirements
------------

Systemd

Role Variables
--------------

```yaml
---
# defaults file for ansible-prometheus

prometheus_install: true
prometheus_node_exporter_install: true
prometheus_alert_manager_install: true
prometheus_push_gateway_install: false
prometheus_snmp_exporter_install: false
prometheus_blackbox_exporter_install: false

prometheus_owner: 'prometheus'
prometheus_group: 'prometheus'

prometheus_install_dir: '/usr/local/opt'
prometheus_config_dir: '/etc/prometheus'
prometheus_lib_dir: '/var/lib/prometheus'
prometheus_rules_dir: "{{ prometheus_config_dir }}/rules"

prometheus_data_dir: "{{ prometheus_lib_dir }}/prometheus2"
prometheus_alert_manager_data_dir: "{{ prometheus_lib_dir }}/alertmanager"
prometheus_alert_manager_config_dir: "{{ prometheus_config_dir }}/alertmanager"
prometheus_alert_manager_templates_dir: "{{ prometheus_config_dir }}/alertmanager/templates"
prometheus_snmp_exporter_config_dir: "{{ prometheus_config_dir }}/snmpexporter"
prometheus_blackbox_exporter_config_dir: "{{ prometheus_config_dir }}/blackboxexporter"

# Prometheus
prometheus_version: '2.13.1'
prometheus_platform_architecture: 'linux-amd64'

# Node exporter
prometheus_node_exporter_version: '0.18.1'

# Alert manager
prometheus_alert_manager_version: '0.18.0'

# Pushgateway
prometheus_push_gateway_version: '1.0.0'

# SNMP exporter
prometheus_snmp_exporter_version: '0.15.0'

# Blackbox exporter
prometheus_blackbox_exporter_version: '0.15.1'
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- name: Installing Prometheus on hosted machine
  hosts: vagrant1
  sudo: yes
  roles:
    - role: ansible-prometheus
      prometheus_config_scrape_configs:
        - job_name: 'prometheus'
          honor_labels: true
          scrape_interval: '15s'
          scrape_timeout: '3s'
          metrics_path: '/metrics'
          scheme: 'http'
          static_configs:
            - targets:
                - 'localhost:9090' # Prometheus itself
                - 'localhost:9100' # Node exporter
        - job_name: 'consul-services'
          consul_sd_configs:
            - server: "localhost:8500"
```

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟
