# Cat girl memoryOC · 发布仓库

**猫娘记忆体超频工具** — AMD DDR5 内存调校 · 面向 Raphael / Granite Ridge 桌面平台

## 获取发行版

运行包（Windows x64，自包含 .NET 8.0.30，无需安装）在仓库右侧 **Releases** 页面下载：

- 最新版本：**0.4.0.4（频率与分频修订版）** → `Cat-girl-memoryOC-0.4.0.4-UI-Windows-x64.zip`
- 压缩包内含：`Cat girl memoryOC.exe`、使用说明（README）、许可证、修复与验证文档（`docs/`）、测试证据（`tests/`）与完整性清单（`manifest.json`）。

本仓库只发布运行包与验证证据，**源码保持私有**，不在此发布。

## 功能要点

- 浅粉三栏界面：频率 / 分频 / 信号控制、主时序 + 副时序、电压与极限设置。
- 只读探测（无需管理员）：CPU / 主板信息、AMD_ACPI 接口版本、参数当前值与允许列表。
- 频率输入按 DDR 数据率（`6400` / `DDR5-6400` / `6400 MT/s`）或显式 `MCLK 3200`，必须在固件允许列表内。
- UCLK 分频：同频 / 分频（DIV1=1 / 0），首次确认会话授权后即选即提交。
- 完整配置保存 / 载入（含未修改、只读、未匹配项）；写入前备份 + 审计，异常不自动重发。
- 电压显示为固件记录值（`1.500 V` / Auto / 原始 VID），**不是实时传感器测量值**。

## 安全提示

- 程序未进行 Authenticode 签名。
- **尚未做实机调参写入认证**：命令返回、固件当前设置、实际时钟 / 电压测量与稳定性是不同阶段；频率 / 分频设置通常需重启训练后独立核对。
- 分频 = 关闭 DIV1，不保证强制半频；仅限管理员 + Raphael / Granite Ridge 桌面平台。
- 使用前请保存工作，并准备主板规定的 BIOS / 清 CMOS 恢复方法。

## 许可与致谢

- MIT（见 `LICENSE`）；第三方组件与素材来源见 `THIRD-PARTY-NOTICES.md`。
- 作者：**纯爱出演小猪**；协助：**Sakura、旗鱼超频、墨白超频、老嘤评测、景涛**。
- 研究参考：[AMD WMI 接口维护者讨论](https://lkml.iu.edu/hypermail/linux/kernel/2607.3/15067.html)、[ZenTimings 上游发行说明](https://github.com/irusanov/ZenTimings/releases)。
