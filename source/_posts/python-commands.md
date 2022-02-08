---
title: python常用命令行
date: 2019-07-01 18:55:08
tags: python, cmd, virtualenv, pip, requirements
categories:
---

# python 命令行

1. 新建虚拟环境

   ```sh
   # use virtualenv
   virtualenv --no-site-packages venv --python=python3

   # or
   sudo apt-get install python3-venv
   python3 -m venv venv

   # then
   source venv/bin/activate
   pip install wheel

   ```

1. pm2 启动 python

   `pm2 start ./src/main.py --name py-demo --interpreter ./venv/bin/python`

1. 生成当前项目的 `requirements.txt`：

   ```sh
   pip freeze
   pip freeze > requirements.txt
   # install
   pip install -r requirements.txt
   ```

1. 修改国内 pip 镜像：

   ```
   # ~/.pip/pip.conf

   [global]
   trusted-host =  mirrors.aliyun.com
   index-url = https://mirrors.aliyun.com/pypi/simple
   ```
