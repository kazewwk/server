# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人修复测试版，与官方 App 并存。沿用已有 LocalFix 包名和签名，可直接覆盖安装并保留 SSH 配置，请勿先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.10-localfix.1（当前测试版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-arm64.apk) |
| 1.0.9-localfix.3（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

本次以官方 [1.0.10](https://github.com/ccch1mneyyy/dsh-Go/releases/tag/v1.0.10)（`b4f2d240`）为基础，保留动效与弹簧手势、移动时减少模糊、远程文件上传及主机详情、默认模型、图片/待办和 compact 等更新。

官方 SSH 源码仍未覆盖手机 ANR 日志中 `GCMBlockCipher._mult → SSHTransport._processAead` 的界面线程阻塞，因此保留 LocalFix r3 的 SSH 后台 worker、接收背压和连接清理，也保留前两版的大数据后台解析和 WebView 生命周期修复。

- 高刷：首次升级默认选择“最高”，前台请求同分辨率下最高不超过 120 Hz 的模式，后台释放请求。之后的手动选择仍会保留；实际 FPS 由系统策略、屏幕模式和渲染负载决定。
- 后台恢复：闲置对话的订阅失效后，返回前台自动恢复；覆盖失效通知先于或晚于前台回调到达的顺序。旧 SSH ping 的延迟结果不会误断新连接，健康的短暂后台切换不会重新加载对话。
- 运行时：使用已校验的官方 1.0.10 runtime 和四个 JNI 库。若使用手机本地 Linux，本次官方运行时更新只保留 `/root`；apt 安装及 `/usr/local`、`/opt` 内容需重新安装。远程电脑不随 APK 更新。

验证：2609 项 Flutter 测试通过（8 跳过），523 项客户端测试通过（2 跳过），313 项远程通信包测试通过；App 与两个库静态检查、双语文案和指南检查通过。新增后台恢复/过期 ping 用例已先复现失败再验证修复；高刷迁移和后续选择保存通过测试。性能截图的变化仅在刷新率选择控件，已人工查看。

尚未在红米真机验证新包、实际刷新率与后台恢复行为。若仍退出或同步失败，请从当前版本的设置导出新的诊断包。

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.10-r1-20261104)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/dsh-go-1.0.10-localfix.1-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.10-r1-20261104/SHA256SUMS)
- [1.0.9 LocalFix r3 发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-r3-20261104)

当前 APK SHA256：`e846a15532f534874b3f74fa8d0ba5127c7f5dd7faa4d0cef8311eac8539f8e3`

源码沿用上游 AGPL-3.0；r1 背景解析参考修复为 `mcl0z/dsh-Go@5376c644`。许可、署名与素材说明见源码内 LICENSE、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断包、会话内容和签名密钥未包含在附件中。
