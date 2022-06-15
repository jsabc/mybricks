Windows 10 搭建工作环境

1.安装 WSL2 和 Ubuntu 20
用管理员身份打开 Powershell，并且运行 wsl --install，该指令会安装WSL(2)环境，以及默认安装 Ubuntu 20。安装完之后记得通过 apt 更新和升级系统。

2.WSL Ubuntu 安装开发环境
由于 WSL2 目前并不支持 snap，所以建议通过 nvm 来安装 node。如果安装 nvm 遇到 curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused 问题，主要是 DNS 受到污染，可以修改本地 DNS 为 8.8.8.8 和 8.8.4.4 来解决。

3.安装开发工具
在 WSL 环境下，建议使用 Visual Studio Code 编辑器。同时，为了让它和 WSL 正常搭配使用，还需要给它安装一个 Remote WSL 扩展。在安装完 Remote WSL 扩展之后，首次在 ubuntu 中启动 Visual Studio Code，可能会遇到报错，这时候只需要通过 wsl.exe --shutdown 重新启动 WSL 即可。

4.配置 Github
详情参考 github 官方文档。

