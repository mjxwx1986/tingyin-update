# tingyin-update

「听音」APP 的在线升级清单（仅版本号与下载地址，不含源码、不含激活密钥）。

- `update.json` —— APP 真正读取的清单
- `test.json` —— 测试清单（版本号写高一位，用来验证弹窗）

| 字段 | 含义 |
|---|---|
| versionCode | 整数，必须大于用户手机上已安装的版本才会提示 |
| versionName | 显示给用户看的版本名 |
| notes | 更新说明，换行用 \n |
| apkUrl | APK 直链，填了就在 APP 内下载并自动调起安装 |
| pageUrl | 下载页面（如蓝奏云分享页）；apkUrl 为空时点「立即更新」跳浏览器 |
| size | APK 字节数，用于显示体积（可省略） |

发布新版本只要改 `versionCode` / `versionName` / `notes` / `apkUrl` 四项。

APP 读取顺序：jsDelivr CDN → GitHub raw → ghproxy 加速。

注意：`versionCode` 必须严格大于已发布版本，否则不会提示；`apkUrl` 换新包后记得同步 `size`。
