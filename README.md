# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人测试版。沿用现有 LocalFix 包名和签名，覆盖安装保留 SSH 配置，不要先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.15-localfix.1（当前测试版） | Android arm64，约 211 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/dsh-go-1.0.15-localfix.1-arm64.apk) |
| 1.0.10-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/dsh-go-1.0.10-localfix.3-arm64.apk) |
| 1.0.10-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-arm64.apk) |
| 1.0.10-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-arm64.apk) |
| 1.0.9-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

本次基于官方 [1.0.15（2026-11-10）](https://github.com/ccch1mneyyy/dsh-Go/releases/tag/v1.0.15)，合入 1.0.11–1.0.15 的伙伴小屋、图片查看与视频播放、聊天布局和动效、远程终端/传文件、SSH 启动与诊断、扫码修复和保留 Linux 环境的引擎更新流程。功能依主机能力开放；电脑上的 DSH 服务不会随 APK 更新。

保留 SSH 后台加解密、ChaCha20-Poly1305 优先及 AES 回退、大 JSON/快照后台处理、本地转发写失败收尾、前后台同步恢复和 mux 重新登录。保留默认前台最高 **120 Hz** 请求，尊重用户后续手动选择；实际帧率仍受系统和负载影响。官方已改进的历史分页和会话错误记录采用新版实现，避免重复旧补丁。

官方 runtime/JNI 逐项校验一致，官方 APK 独有的伙伴素材也已补齐并校验。包名为 `io.github.ccch1mneyyy.dsh_app.localfix`，构建号 `11130255`，与上一版 LocalFix 同签名。

验证：选定应用回归最终 1913 项通过、2 跳过；dsh_client 838 通过、31 跳过；dsh_remote 499 通过、4 跳过；Android 原生检查 43 项通过，静态分析、文案和指南检查通过。6 项伙伴计时用例在并行编译时失败，未改代码，串行重跑对应两个文件的 10 项全部通过。较大范围首轮在 3748 项通过后达到命令时间上限，未记作整套通过；各轮重叠数量未累加，详情见验证记录。

新 APK 尚未在红米真机验证：安装、真实 120 Hz、前后台体验仍需实机确认。

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.15-r1-20261113)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/dsh-go-1.0.15-localfix.1-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/dsh-go-1.0.15-localfix.1-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.15-r1-20261113/SHA256SUMS)

APK SHA256：`a88f2051f7de89d08b539e117d87f8b221888c4101993a4c39bd2c68612b8598`

应用源码沿用 AGPL-3.0；背景解析最初参考 `mcl0z/dsh-Go@5376c644`。素材及第三方组件保留各自的许可，详见 LICENSE、THIRD_PARTY_NOTICES.md、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断、会话、私钥、签名密钥及真实主机测试脚本不在交付源码内。
