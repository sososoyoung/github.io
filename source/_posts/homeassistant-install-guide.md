---
title: homeassistant 安装指南
date: 2019-07-01 19:00:24
tags: homeassistant, python, N1, armbian, 树莓派
categories:
---

1. # 常规安装

   ```sh
   # init venv
   sudo apt-get install python3-venv
   python3 -m venv venv
   source ./venv/bin/activate
   pip3 install wheel

   # 安装依赖
   sudo apt-get install libffi-dev  build-essential libssl-dev libffi-dev python3-dev

   # error for cryptography:
   # https://cryptography.io/en/latest/installation/#building-cryptography-on-linux

    pip3 install homeassistant
   ```

2. N1 armbian 系统创建 service: https://www.home-assistant.io/docs/autostart/systemd/

   ```sh
   # /etc/systemd/system/home-assistant.service
   [Unit]
   Description=Home Assistant
   After=network-online.target

   [Service]
   Type=simple
   User=shty
   ExecStart=/<path>/hass -c "/<configpatch>/homeassistant"

   [Install]
   WantedBy=multi-user.target

   ```

   启用:

   ```sh
    sudo systemctl --system daemon-reload
    sudo systemctl enable home-assistant
    sudo systemctl start home-assistant

    sudo systemctl status home-assistant
    sudo systemctl disable home-assistant
   ```

3. 获取 cpu 温度 `command_line`
   ```
   - platform: command_line
     name: CPU Temperature
     command: "cat /sys/class/hwmon/hwmon0/temp1_input"
     unit_of_measurement: "°C"
     value_template: '{{ value | multiply(0.001)|round(1)  }}'
     scan_interval: 30
   ```
