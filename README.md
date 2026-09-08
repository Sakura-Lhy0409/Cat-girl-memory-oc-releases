# Cat girl memoryOC

AMD DDR5 内存调校工具，给 Raphael / Granite Ridge 平台用的。
源码是私有的，这个仓库只发运行包和验证证据。

## 下载

最新版 0.4.0.4，去页面右边的 Releases 拿：
`Cat-girl-memoryOC.zip`

解压就能用。Windows x64，不用装 .NET。
包里有 exe、辉夜酱.png 和 `必须看.txt`（适配说明，先读这个）。

## 能干嘛

- 三栏界面：频率 / 分频 / 信号控制、时序、电压
- 只读探测，不需要管理员
- 改频率、分频，配置保存 / 载入
- 提交前有检查、备份和审计，失败不自动重发

## 用之前看一下

- 没签名
- 没在真机上验证过写入；频率 / 分频改完要重启训练，自己核对
- 分频 = 关掉 DIV1，不保证是半频
- 只支持管理员 + Raphael / Granite Ridge
- 电压那栏是固件记录值，不是实时测量

## 署名

作者：纯爱出演小猪
协助：Sakura、旗鱼超频、墨白超频、老嘤评测、景涛

MIT 许可，看 `LICENSE`。第三方东西看 `THIRD-PARTY-NOTICES.md`。
