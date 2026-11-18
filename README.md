# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人测试版。沿用现有 LocalFix 包名和签名，覆盖安装保留 SSH 配置，不要先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.1.0-localfix.2（当前测试版） | Android arm64，约 232 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r2-20261119/dsh-go-1.1.0-localfix.2-arm64.apk) |
| 1.1.0-localfix.1（旧版） | Android arm64，约 232 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r1-20261117/dsh-go-1.1.0-localfix.1-arm64.apk) |
| 1.0.16-localfix.1（旧版） | Android arm64，约 215 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.16-r1-20261115/dsh-go-1.0.16-localfix.1-arm64.apk) |
| 1.0.15-localfix.1（旧版） | Android arm64，约 211 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/dsh-go-1.0.15-localfix.1-arm64.apk) |
| 1.0.10-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/dsh-go-1.0.10-localfix.3-arm64.apk) |
| 1.0.10-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-arm64.apk) |
| 1.0.10-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-arm64.apk) |
| 1.0.9-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

**1.1.0-localfix.2** 新增「本机 ADB 常用命令免确认」。连接自连 ADB 后可开启，屏幕参数、电量、亮度查询和返回、主页、音量键可自动执行。其他 Shell 命令及 Shizuku 仍逐条确认。[发布页与源码](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.1.0-r2-20261119)

上一版 1.1.0-localfix.1 基于官方 [1.1.0（2026-11-15）](https://github.com/ccch1mneyyy/dsh-Go/releases/tag/v1.1.0)。合入语音朗读、语音输入和语音通话，酒馆玩法包/做卡工具及长对话优化，用量统计 v3 和新界面效果；包含远程重连、伙伴兼容、语音崩溃等修复。

保留 SSH 后台加解密、ChaCha20-Poly1305 优先及 AES 回退、认证后压缩、大 JSON/快照后台准备、转发写失败收尾、前后台同步恢复和 mux 重新登录。前台最高 **120 Hz** 请求继续保留，后续手动设置仍有效，实际帧率受系统和负载影响。接入新版持久化诊断，保留受限 ANR 堆栈。

包名 `io.github.ccch1mneyyy.dsh_app.localfix`，构建号 `11170204`。同签名覆盖安装校验通过；配套 PRoot 升至 **5.1.107.102**，官方运行时和预编译组件摘要一致。官方 1.1.0 不再附带旧的伙伴模型 ZIP，本构建跟随官方资源布局，已有导入模型仍保存在应用数据中。APK 更新不会升级电脑上的 DSH 服务。

验证：应用 1365 通过 / 12 跳过，dsh_client 885 / 31，远程最终 499 / 4，原生诊断 33 通过；静态分析、文案、指南和 release 编译通过。远程的一项大传输用例在并行检查时超过 5 秒看门狗，未改代码，单独复测该文件 4 项全部通过，重叠数量未累加。测试没有调用用户的模型账户或修改真实对话。

未连接红米真机，安装、实际刷新率、语音通话、前后台体验和运行时升级仍需实机确认。

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.1.0-r1-20261117)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r1-20261117/dsh-go-1.1.0-localfix.1-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r1-20261117/dsh-go-1.1.0-localfix.1-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r1-20261117/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r1-20261117/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.1.0-r1-20261117/SHA256SUMS)

APK SHA256：`ed754d10278d364736aafbe8a0e813aeb89d25927e2707d02cc4f2cdaf0ab0a8`

应用源码沿用 AGPL-3.0；背景解析最初参考 `mcl0z/dsh-Go@5376c644`。素材及第三方组件保留各自许可，详见 LICENSE、THIRD_PARTY_NOTICES.md、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断、会话、私钥、签名密钥及真实主机测试脚本不在交付源码内。
