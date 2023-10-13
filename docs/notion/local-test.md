---
status: 已发布
sort: 130
urlname: local-test
上次编辑时间: "2023-10-13T06:11:00.000Z"
catalog: 配置详情
tags: Elog-Docs
title: 本地调试
date: "2023-10-13 05:27:00"
updated: "2023-10-13 06:11:00"
---

# 本地调试

## 环境变量配置

Elog 配置文件默认为`elog.config.js`，可在配置文件中通过`process.env.xxx`根据需要自定义环境变量，一般不需要改动，只有当环境变量冲突时才需要变更。

> ⚠️ 为了安全，在实际配置中请不要将敏感信息直接写在配置文件中，Elog 提供了更优雅的本地调试方式。

## 本地调试

为了方便本地调试，Elog 支持从本地文件中获取环境变量。只需要在部署平台根目录新增`.elog.env`文件，将用到的配置写入，然后在执行同步命令时指定环境变量文件即可。

> ⚠️ 注意：请将`.elog.env`文件加入 `.gitignore`，防止误提交到 git 仓库

```shell
// 指定同步时读取的环境变量
elog sync -e .elog.env
```

```shell
# .elog.env

# 语雀（Token方式）
YUQUE_TOKEN=
# 语雀（帐号密码方式）
YUQUE_USERNAME=
YUQUE_PWD=
YUQUE_LOGIN=
YUQUE_REPO=

# Notion
NOTION_TOKEN=
NOTION_DATABASE_ID=

# FlowUs
FLOWUS_TABLE_PAGE_ID=

# 飞书
FEISHU_APP_ID=
FEISHU_APP_SECRET=
FEISHU_FOLDER_TOKEN=

# Confluence
CONFLUENCE_BASE_URL=
CONFLUENCE_USER=
CONFLUENCE_PASSWORD=
CONFLUENCE_SPACE_KEY=
CONFLUENCE_ROOT_PAGE_ID=

#WordPress
WORDPRESS_USERNAME=
WORDPRESS_PASSWORD=
WORDPRESS_ENDPOINT=

# 腾讯云
COS_SECRET_ID=
COS_SECRET_KEY=
COS_BUCKET=
COS_REGION=
COS_HOST=

# 阿里云
OSS_SECRET_ID=
OSS_SECRET_KEY=
OSS_BUCKET=
OSS_REGION=
OSS_HOST=

# 七牛云
QINIU_SECRET_ID=
QINIU_SECRET_KEY=
QINIU_BUCKET=
QINIU_REGION=
QINIU_HOST=

# 又拍云
UPYUN_USER=
UPYUN_PASSWORD=
UPYUN_BUCKET=
UPYUN_HOST=

# Github
GITHUB_USER=
GITHUB_TOKEN=
GITHUB_REPO=
```

## 自动化配置

自动化时，需要提前将以上`.elog.env`中用到的变量信息配置到环境变量上。 以 Github 为例，可以在仓库的`设置-Secrets and variables-Actions-Secrets`中进行配置，然后在流水线中注入即可。

> 记得在仓库的`设置-Action-Workflow permissions`中开启读写权限

详细的自动化配置请移步 [持续集成](/notion/vy55q9xwlqlsfrvk) 页面。