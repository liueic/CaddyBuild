# CaddyBuild

使用 GitHub Actions 自动自定义编译 [Caddy](https://caddyserver.com/)。

## 功能简介

- 基于 GitHub Actions 云端自动编译
- 支持自定义插件（如 cloudflare DNS、caddy-l4 等）
- 自动上传编译好的二进制文件为 GitHub Artifact

## 使用方法

1. **Fork 本仓库**  
   点击右上角 Fork，将本项目复制到你的仓库。

2. **手动触发编译**  
   进入你的仓库，点击 `Actions`，选择 `Build Custom Caddy` 工作流，点击 `Run workflow` 即可开始编译。

3. **下载编译产物**  
   编译完成后，在 Actions 的运行记录页面下载 `caddy` 二进制文件。

## 工作流说明

- 使用 [xcaddy](https://github.com/caddyserver/xcaddy) 工具自定义构建 Caddy
- 默认集成插件：
  - [cloudflare DNS](https://github.com/caddy-dns/cloudflare)
  - [caddy-l4](https://github.com/mholt/caddy-l4)
- 可根据需要修改 `.github/workflows/build.yaml` 添加或删除插件

## 修改插件

编辑 `.github/workflows/build.yaml` 文件，修改 `xcaddy build` 命令中的 `--with` 参数即可。

例如，添加更多插件：

```
xcaddy build \
  --with github.com/caddy-dns/cloudflare \
  --with github.com/mholt/caddy-l4 \
  --with <你的插件>
```