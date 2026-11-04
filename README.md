# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人修复测试版，与官方 App 并存。已装 LocalFix 可直接覆盖安装第三版，保留 SSH 配置，请勿先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.9-localfix.3（当前测试版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-arm64.apk) |
| 1.0.9-localfix.2（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

第三版按手机系统 ANR 栈定位：用与第二版 APK 匹配的符号确认，多次前台卡死停在 `GCMBlockCipher._mult → SSHTransport._processAead`，SSH AES-GCM 解密占住了界面线程。

修复将 SSH 握手、认证、加解密和传输移到后台 isolate；主机指纹仍由原界面确认；隧道接收有确认与背压，分段读取使保活和关闭能及时执行，退出时释放底层连接。保留前两版的大对话后台解析及加载生命周期修改。

278 项远程相关测试通过，7 项需另配真实 SSH/DSH 主机的测试跳过，App 静态分析无问题。临时 loopback sshd 强制 AES-GCM，验证了字节完整性、EOF、暂停恢复、拒绝端口和下载中途关闭。桌面同一 4 MiB 下载，旧路径最大界面事件间隔 5121.771 ms，后台传输 12.663 ms；总耗时分别为 6672 / 8037 ms。这是界面响应测试，不表示总传输加快或手机实测结果。

第三版尚未在红米真机验证。若仍退出，请重新打开 LocalFix，从设置导出诊断包；保留的系统退出原因和 ANR 栈便于继续定位。

- [第三版发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-r3-20261104)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-1.0.9-localfix.3-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/dsh-go-localfix-r3-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r3-20261104/SHA256SUMS)
- [第二版发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-r2-20261104)
- [第一版发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-20261103)

第三版 APK SHA256：`0ea4c4c1be692107c0a7f7c19827e3b679d8716a1886be320fea5ca34fed45a7`

源码基于 [ccch1mneyyy/dsh-Go](https://github.com/ccch1mneyyy/dsh-Go) 的 `8e36cdb`，第一版参考修复提交 `mcl0z/dsh-Go@5376c644`。许可与素材说明见源码内 LICENSE、ASSETS.md 和 LOCALFIX-NOTES.txt。用户诊断包、会话内容和签名密钥未包含在附件中。
