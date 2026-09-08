# Cat girl memoryOC · 发布仓库（Release）

**猫娘记忆体超频工具** — AMD DDR5 内存调校 · 面向 Raphael / Granite Ridge 桌面平台

> 本仓库只发布 **0.4.0.4 运行包** 与配套验证证据；项目**源码保持私有**，不在此发布。

## 下载

| 文件 | 说明 |
|---|---|
| [`Cat girl memoryOC.exe`](Cat%20girl%20memoryOC.exe) | 0.4.0.4 单文件运行程序（自包含，无需安装 .NET） |
| [`Cat-girl-memoryOC-0.4.0.4-UI-Windows-x64.zip`](Cat-girl-memoryOC-0.4.0.4-UI-Windows-x64.zip) | 完整运行包（含程序、文档与测试证据，推荐下载此包） |

## 功能特性

- 浅粉三栏界面：频率 / 分频 / 信号控制、主时序 + 副时序、电压与极限设置；每行显示「设置 / 当前 / 目标」。
- 只读探测：CPU / 主板信息、AMD_ACPI 接口版本、固件函数表、参数当前值与允许列表（无需管理员）。
- 内存频率输入：按 DDR 数据率（`6400`、`DDR5-6400`、`6400 MT/s`）或显式 `MCLK 3200`；须在固件发布允许列表内。
- UCLK 分频：「同频 / 分频」（DIV1=1 / 0），首次手动选择确认会话授权后即选即提交。
- 完整配置保存 / 载入：包含未修改、只读与未匹配项，往返无损；载入只恢复目标文本，不写入硬件。
- 提交前校验：命令 ID、当前值、允许列表、命令缓冲边界、管理员权限与平台白名单；写入前备份 + 审计。
- 电压显示：固件记录的当前设置（`1.500 V`）、Auto 或原始 VID — **不是实时传感器测量值**。

## 快速开始

1. 解压 `Cat-girl-memoryOC-0.4.0.4-UI-Windows-x64.zip`，双击 `Cat girl memoryOC.exe`。
2. 启动即只读探测；需要写入时点击 **管理员重启** 以管理员身份运行。
3. 常规参数（频率、电压等）：修改目标 → **预览并写入**；频率通常需重启训练后生效。
4. UCLK 分频：点击参数行分频按钮，首次确认会话授权，之后即选即提交。
5. 建议保留工作备份，并准备主板规定的 BIOS / 清 CMOS 恢复方法。

> ⚠️ 程序未进行 Authenticode 签名；`manifest.json` 中的 SHA256 仅核对文件完整性，不代表可信签名。

## 安全与风险边界

- 只读探测无需提权；写入必须管理员，异常不自动重发，关闭软件结束会话授权。
- **尚未做实机调参写入认证**：本版本的实机验证仅为只读探测（AMD_ACPI v6、62 个参数）；命令返回、固件当前设置、实际时钟 / 电压测量与稳定性是不同阶段。
- 分频 = 关闭 DIV1（`DIV1=0`），不保证强制半频；实际比例由 BIOS 训练决定，需重启后独立核对。
- 分频仅限管理员 + Raphael（family 0x19 / model 0x61）、Granite Ridge（family 0x1A / model 0x44）桌面平台。
- 非时钟参数的旧版写入编码沿用旧版；电压显示修复不等于认证旧版全部电压写入。

## 验证证据

| 项目 | 结果 |
|---|---|
| 离线回归 | **128 / 128 通过，HARDWARE_WRITES 0**（见 [`tests/profile-tests.txt`](tests/profile-tests.txt)） |
| 成品自测 `--self-test` | 原版 23 项 + 配置入口 10 项 + 时钟回归 71 项 + 时钟补丁入口 4 项全部通过（见 [`tests/packaged-self-test.txt`](tests/packaged-self-test.txt)） |
| 核心等价性 | 488 个原始方法中 471 个逐字节一致；17 个变化全部在限定名单，0 意外变更（见 [`docs/core-equivalence-0.4.0.4.json`](docs/core-equivalence-0.4.0.4.json)） |
| 依赖一致性 | 447 个原始运行依赖哈希一致，仅新增本地扩展模块 |

### 文件 SHA256

```
Cat girl memoryOC.exe
4F477EC6D288E7C249B65011495F886933C8F4857A9575719B7C48AF6FFF2B9D

Cat-girl-memoryOC-0.4.0.4-UI-Windows-x64.zip
3439BB5D3D250705ACEF3793C61D5E9BAE8DFCC63DAEC55D9B04A5D5359494EE
```

`manifest.json` 为**运行包**逐文件清单（与 ZIP 内容一致，覆盖程序、许可、文档与测试证据）。

## 系统要求

- Windows x64（10 / 11）；单文件发布为 .NET 8.0.30 自包含（含 WPF 运行时），**无需单独安装 .NET**。
- 完整功能（硬件写入）需要管理员权限；只读探测不需要。

## 许可与致谢

- 许可证：MIT（见 [`LICENSE`](LICENSE)）；第三方组件与素材来源见 [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md)。
- 作者：**纯爱出演小猪**；协助：**Sakura、旗鱼超频、墨白超频、老嘤评测、景涛**。
- 界面 Logo：用户提供的原始素材，仓库仅做格式转换与采样，未使用图像生成模型重绘。
- 研究参考：[AMD WMI 接口维护者讨论](https://lkml.iu.edu/hypermail/linux/kernel/2607.3/15067.html)、[ZenTimings 上游发行说明](https://github.com/irusanov/ZenTimings/releases)。
