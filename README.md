# server

个人安装包与测试构建下载。

## DSH Go LocalFix

针对 SSH 大对话同步阻塞的非官方修复测试版，与官方 App 并存，安装后需要重新添加 SSH 主机。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.9-localfix.1 | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

- [发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-20261103)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-localfix-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/LOCALFIX-NOTES.txt)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/SHA256SUMS)

APK SHA256：`7a51fa1584286e2362fb9fa049c875fb8557f1a0cfdd92210d4271a36cc4c9b5`

已通过 515 项通信包测试和 81 项相关界面测试；尚未完成真机验证，不能保证解决所有闪退。源码基于 [ccch1mneyyy/dsh-Go](https://github.com/ccch1mneyyy/dsh-Go) 的 `8e36cdb`，参考修复提交 `mcl0z/dsh-Go@5376c644`。许可与素材说明见源码内 LICENSE、ASSETS.md 和 LOCALFIX-NOTES.txt。
