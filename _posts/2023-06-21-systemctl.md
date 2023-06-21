---
layout:     post
title:      "系统开机自动启动任务"
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
     - Web application
     - Linux
---

# 1.使用 systemd

Systemd 是一种系统和服务管理器，它负责初始化系统。在 CentOS 7 及更高版本中，Systemd 已经取代了旧的 SysV init 系统。要使用 systemd 创建一个服务并在启动时运行，你可以按照以下步骤操作：

- 创建一个新的 systemd 服务文件，如 `/etc/systemd/system/my_script.service`。你可以用你的脚本或命令替换 `my_script`。
- 在这个文件中，添加以下内容：

```
[Unit]
Description=My Script

[Service]
ExecStart=/path/to/your/script.sh

[Install]
WantedBy=multi-user.target
```

- 确保你的脚本在 `ExecStart` 行中的路径是正确的。
- 保存并退出编辑器。
- 让 systemd 重新加载新的配置文件，使用命令 `sudo systemctl daemon-reload`。
- 启用服务以在启动时运行，使用命令 `sudo systemctl enable my_script.service`。

# 2.使用 cron

Cron 是一个在 Unix-like 系统中用于定时执行任务的工具。你可以使用 `@reboot` 选项在每次系统启动时运行一个命令。例如：

- 打开 crontab 文件，使用命令 `crontab -e`。
- 在文件中，添加一行 `@reboot /path/to/your/script.sh`。
- 保存并退出编辑器。

这将在每次系统启动时运行你的脚本。

注意：确保你的脚本或程序具有正确的权限，并且在所需的环境中运行。在某些情况下，你可能需要在脚本中包含完整的环境路径。

