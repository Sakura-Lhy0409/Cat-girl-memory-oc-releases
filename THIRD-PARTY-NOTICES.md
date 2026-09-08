# 来源与许可证

- 原始 Cat girl memoryOC 0.4.0：本地已核对的原始构建；主体 SHA256 见 README；沿用工作区 MIT 许可，见 LICENSE。
- dnlib 4.5.0：仅在构建工具中读取、修改和核对 .NET 元数据。MIT，版权和完整许可见 `tools/dnlib-4.5.0/LICENSE.txt`。官方上游：https://github.com/0xd4d/dnlib 。下载自官方 NuGet 包： https://api.nuget.org/v3-flatcontainer/dnlib/4.5.0/dnlib.4.5.0.nupkg 。包内源提交 c78d296c522aae0520df2afd825d48266321cf36。
- Microsoft.NET.HostModel：使用安装的 .NET SDK 8.0.424 自带组件构建单文件。Microsoft / .NET Foundation，MIT。官方上游：https://github.com/dotnet/runtime/tree/main/src/installer/managed/Microsoft.NET.HostModel 。运行时文件沿用输入程序的原始文件。
- .NET 单文件布局参考：https://github.com/dotnet/runtime/blob/main/src/installer/managed/Microsoft.NET.HostModel/Bundle/Manifest.cs 和 https://github.com/dotnet/runtime/blob/main/src/installer/managed/Microsoft.NET.HostModel/Bundle/FileEntry.cs 。本项目自行实现有边界检查的读取器，未引入第三方解包程序。
- ILSpy 9.1.0.7988：仅用于静态阅读原程序，未作为应用运行依赖。MIT。官方上游：https://github.com/icsharpcode/ILSpy 。恢复代码目录仅供核对，不参与核心重编译。
- Logo：用户提供的原始 JPG。使用范围按用户本次软件换肤请求；不额外主张该素材的著作权或再分发授权。

这些构建工具没有集成进最终 EXE。最终 EXE 使用与原版一致的 .NET 运行依赖及 System.Management 依赖。0.4.0.4 内嵌本工程自编译的 `CatGirl.ProfileIO.dll`（MIT，见 LICENSE），处理完整配置、明确的固件读取、时钟校验、用户确认后的分频单项提交和离线自测。

`baseline/System.Management.dll` 是从已核对的原始单文件中提取的相同依赖，仅作为编译引用，不是新下载的运行依赖。SHA256：`B2D6E7E991DC9EF154B29F4966F04FD8ED4EBB2C1D1242EA1D5F3E90F8AE5143`。
