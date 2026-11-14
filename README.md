# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人测试版。沿用现有 LocalFix 包名和签名，覆盖安装保留 SSH 配置，不要先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.16-localfix.1（当前测试版） | Android arm64，约 215 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/dsh-go-1.0.16-localfix.1-arm64.apk) |
| 1.0.15-localfix.1（旧版） | Android arm64，约 211 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/dsh-go-1.0.15-localfix.1-arm64.apk) |
| 1.0.10-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/dsh-go-1.0.10-localfix.3-arm64.apk) |
| 1.0.10-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-arm64.apk) |
| 1.0.10-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-arm64.apk) |
| 1.0.9-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

本次基于官方 [1.0.16（2026-11-13）](https://github.com/ccch1mneyyy/dsh-Go/releases/tag/v1.0.16)。合入超长工具输出折叠与全文页、SSH 认证后压缩和连接已有实例、酒馆模式、创意工坊、悬浮伙伴，以及运行时和手机操控的稳定性改进。tawcroot 加速启动仍是默认关闭的实验选项。安装 APK 不会升级电脑上的 DSH 服务。

保留 SSH 后台加解密、ChaCha20-Poly1305 优先及 AES 回退、大 JSON/快照后台准备、转发写失败收尾、前后台同步恢复和 mux 重新登录。采用官方新解析和列表缓存，移除重复实现；前台最高 **120 Hz** 请求继续保留，尊重后续手动设置，实际帧率仍受系统和负载影响。

包名 `io.github.ccch1mneyyy.dsh_app.localfix`，构建号 `11150013`。同签名覆盖安装校验通过；官方运行时、伙伴素材和 tawcroot 预编译组件逐项校验一致。

应用相关回归最终 1161 通过 / 12 跳过；dsh_client 884 / 31，dsh_remote 499 / 4，SSH 压缩、加密和写入顺序测试 44 / 0；静态分析、文案、指南和 Android release 编译通过。测试服务器调试日志曾干扰两项 stderr 断言，改为独立日志文件后，该文件 10 项通过、1 跳过，详见验证记录，重叠数量未累加。本轮未重复运行未改动的原生单元测试。

未连接红米真机，手机安装、真实刷新率和前后台体验仍需实机确认。

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.16-r1-20261115)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/dsh-go-1.0.16-localfix.1-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/dsh-go-1.0.16-localfix.1-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/SHA256SUMS)

APK SHA256：`f25ab6ddc769269da846e0de0bce5dc5b72a981e3a420315f27ee7c3cca02817`

应用源码沿用 AGPL-3.0；背景解析最初参考 `mcl0z/dsh-Go@5376c644`。素材及第三方组件保留各自的许可，详见 LICENSE、THIRD_PARTY_NOTICES.md、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断、会话、私钥、签名密钥及真实主机测试脚本不在交付源码内。
