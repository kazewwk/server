# server

个人安装包与测试构建下载。

## DSH Go LocalFix

非官方个人修复测试版，与官方 App 并存。已装 LocalFix 第一版可直接覆盖安装第二版，保留 SSH 配置，请勿先卸载。

| 版本 | 平台 | 下载 |
|---|---|---|
| 1.0.9-localfix.2（当前测试版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-arm64.apk) |
| 1.0.9-localfix.1（旧版） | Android arm64，约 193 MB | [下载 APK](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-20261103/dsh-go-1.0.9-localfix.1-arm64.apk) |

第二版针对加载、连接和同步时切页出现的阻塞：先异步完成 WebView 启动，再构造插件页面；设备信息查询移出 UI 线程；隐藏页面暂停探测；页面或连接地址改变后拒绝过期加载任务。保留第一版的大对话后台解析与线性历史合并。

新增 Android 11+ 系统退出原因与经过滤的 ANR 主线程栈、WebView 启动耗时。若仍退出，请重新打开 LocalFix，从设置导出诊断包，不是导出某个对话。系统记录的完整程度取决于 Android 版本和厂商。

本次 233 项相关 Flutter 测试、9 项 Android 单元测试通过，App 静态分析无问题。尚未连接红米 Turbo 4 Pro 真机验证，手机实际退出原因还没有由系统记录确认，不能保证解决所有闪退。

- [第二版发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-r2-20261104)
- [完整对应源码](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-1.0.9-localfix.2-source.tar.gz)
- [源码补丁](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/dsh-go-localfix-r2-source.patch)
- [构建说明](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/LOCALFIX-NOTES.txt)
- [验证记录](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/verification.json)
- [SHA256 校验和](https://github.com/kazewwk/server/releases/download/dsh-go-localfix-v1.0.9-r2-20261104/SHA256SUMS)
- [第一版发布页](https://github.com/kazewwk/server/releases/tag/dsh-go-localfix-v1.0.9-20261103)

第二版 APK SHA256：`1646151c88bf98ace5c2000cc523943a92be59fa0b2fd0cff4f09bf10a44635e`

源码基于 [ccch1mneyyy/dsh-Go](https://github.com/ccch1mneyyy/dsh-Go) 的 `8e36cdb`，第一版参考修复提交 `mcl0z/dsh-Go@5376c644`。许可与素材说明见源码内 LICENSE、ASSETS.md 和 LOCALFIX-NOTES.txt。
