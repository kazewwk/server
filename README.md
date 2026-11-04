# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人测试版。沿用 LocalFix 包名和签名，可覆盖安装并保留 SSH 配置，不要先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.10-localfix.2（当前测试版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-arm64.apk) |
| 1.0.10-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-arm64.apk) |
| 1.0.9-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

本次修复已复现的对话通道恢复缺口：SSH 在线、但对话 mux 关闭或拒绝旧 cookie 后，重新登录并发布新客户端；不再复用已关闭通道。恢复过程中发生的 cookie 拒绝会在当前重连释放后继续处理。保活、返回前台和手动重试也会检查该状态。

补齐诊断记录：已捕获的同步异常及原始堆栈通过现有脱敏器进入内存错误日志，记录意外的 follow 结束；正常连接观察同时保留 mux 状态、错误类型与 HTTP 状态码。导出诊断不会额外创建连接。若仍复现，请在失败后直接导出，强行停止会清空内存错误记录。

验证：2234 项相关 App 套件通过（8 跳过），最后 15 项生命周期/EOF/诊断用例通过（与前者有重叠，不相加），静态检查通过。关闭 mux 的用例先复现无法恢复，再验证修复；cookie 拒绝重连时序与日志脱敏通过。在真实 work 服务上主动关闭本测试客户端后约 1 秒重连，随后重新取得会话快照；普通和约 1 Mbps 限速链路也做了只读检查。

限制：手机上传的 localfix.1 日志确认 SSH connected、刷新率 max、无新 ANR，但未记录原始同步异常。手机最初断开的触发原因仍未证实；此版修复已复现的恢复缺口并补齐记录，不保证覆盖其他原因，新 APK 尚未真机验证。

保留 [官方 1.0.10](https://github.com/ccch1mneyyy/dsh-Go/releases/tag/v1.0.10)（`b4f2d240`）及前版修复：动效/模糊优化、远程上传、默认模型、图片/待办与 compact 更新；SSH 后台加解密、JSON/快照后台处理；后台对话恢复与默认前台最高 120 Hz 请求，实际帧率受系统与渲染负载影响。

运行时仍与已校验的官方 1.0.10 APK 一致。手机本地 Linux 的官方迁移只保留 `/root`；远程电脑不随 APK 更新。

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.10-r2-20261104)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/dsh-go-1.0.10-localfix.2-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r2-20261104/SHA256SUMS)

APK SHA256：`cf492fa48819124afd4371fbe4504f0837c98486dc8ff04d4b17271c568239c6`

源码沿用上游 AGPL-3.0；r1 背景解析参考 `mcl0z/dsh-Go@5376c644`。许可、署名与素材说明见 LICENSE、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断包、会话内容、私钥与签名密钥不在附件中。
