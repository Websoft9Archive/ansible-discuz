# Discuz 自动化安装与部署

本项目是基于Ansible的 [Discuz](https://discuz.net) 自动化安装脚本，实现在 Ansible 上一键安装 Discuz。本项目是开源项目，支持MIT开源协议。如果您不熟悉Ansible的使用，您可以直接使用我们在公有云上提供的镜像。

## 技术要求

操作系统：CentOS7.x

运行环境：LAMP, LNMP，其中 Dicuz3.2 需要 PHP5.6, Dicuz3.3/3.4 需 PHP7.0

服务器配置：最低1G内存，10G系统盘空间


## Discuz 版本控制

通过修改下载地址来控制版本，最新版本通过 git 地址

## Ansible安装指南

本Ansible脚本支持root用户、普通用户（+su权限提升）等两种账号模式，也支持密码和秘钥对登录方式。

## 组件

Discuz+LAMP(Apache, MySQL, PHP)

## 使用指南

文档链接：http://support.websoft9.com/docs/discuz