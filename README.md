# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人测试版。沿用现有 LocalFix 包名和签名，覆盖安装保留 SSH 配置，不要先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.10-localfix.3（当前测试版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/dsh-go-1.0.10-localfix.3-arm64.apk) |
| 1.0.10-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-arm64.apk) |
| 1.0.10-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-arm64.apk) |
| 1.0.9-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

本次针对新诊断中的本地 `127.0.0.1 Broken pipe`：复现了接收端断开后，转发写失败从未观察的 `Socket.done` 漏到全局平台异常处理器的路径。现在正确收尾该连接，保护双向转发写入，并继续清理延迟打开的通道。

SSH 优先协商现有 ChaCha20-Poly1305，保留原 AES 回退。同线路传输 4 MiB 合成数据，桌面 AES-256-GCM 7385 ms，ChaCha20-Poly1305 567 ms。指定对话通过真实服务的 App 连接管理/会话控制器只读测试，达到同步状态从约 4517 ms 降到 1847 ms，前后台恢复也通过。此为桌面测量，不代表所有手机、网络都相同。

439 项相关测试通过（8 跳过），静态检查通过。包括先失败后修复的重置接收端用例、半关闭与最终回复、延迟通道、指纹拒绝、传输完整性，以及强制 AES-GCM 的兼容回退。

保留官方 [1.0.10](https://github.com/ccch1mneyyy/dsh-Go/releases/tag/v1.0.10) 与前版修复：SSH 后台加解密、JSON/快照后台处理、会话关闭与 cookie 失效恢复、同步异常/堆栈诊断、默认前台最高 120 Hz 请求（实际 FPS 受系统和负载影响）。

新 APK 尚未真机验证；修复了已复现的写失败路径并减少实测解密瓶颈，手机最初关闭接收端的全部触发因素尚未完全证实。若仍失败，请在发生后直接导出诊断，先不要强行停止 App，以保留内存错误记录。

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.10-r3-20261104)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/dsh-go-1.0.10-localfix.3-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/dsh-go-1.0.10-localfix.3-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r3-20261104/SHA256SUMS)

APK SHA256：`91491fdc748ef620c5c8f6fe7f3fba1a7079500f5bcafb6c4079472797dc4cb0`

源码沿用 AGPL-3.0；r1 背景解析参考 `mcl0z/dsh-Go@5376c644`。许可、署名与素材说明见 LICENSE、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断、会话内容及标识、QQ 配置/人格、真实主机测试脚本和签名密钥不在交付源码或 APK 内。运行时与已校验官方 1.0.10 相同；手机本地 Linux 的官方迁移只保留 `/root`，远程电脑不会随 APK 更新。
