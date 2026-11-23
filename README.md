# CampusHub 官方插件市场源

本仓库托管 CampusHub 声明式插件（`dsl-v1`）及其 ECDSA P-256 数字签名索引。

## 目录结构

- `plugins/<slug>/`：插件源码清单（`manifest.json` + `dsl.json`）
- `dist/<slug>.chpkg`：确定性打包后的声明式插件包
- `registry.json` 与 `registry.json.sig`：市场索引及 ECDSA P-256 签名（`keyId`: `campushub-plugin-ecdsa-2026-v1`）
- `keys/campushub-plugin-ecdsa-2026-v1.pub.pem`：公开验签公钥

## 安全说明

- 所有插件仅声明 `dsl-v1` 数据模板，不包含可执行字节码。
- 所有网络通信由宿主 `ScopedHttpBridge` 强制限定 HTTPS 与 `allowedHosts` 白名单。
- 私钥不入库；每次索引与 `.chpkg` 更新均经 ECDSA P-256（`SHA256withECDSA`）离线签名验证。
