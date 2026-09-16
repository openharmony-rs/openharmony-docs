# IsolatedComponent(System API)

IsolatedComponent用于支持在本页面内嵌入显示独立Abc（方舟字节码，.abc文件）提供的UI，展示的内容在受限Worker线程中运行。

通常用于有Abc热更新（可动态替换IsolatedComponent加载的Abc文件，无需通过重新安装应用的方式实现内容更新）诉求的模块化开发场景。

> **说明：** > > - 使用前需确保Abc已通过verifyAbc校验，且已在module.json5中配置ohos.permission.RUN_DYN_CODE权限。 > - 不支持构造参数更新，仅首次传入有效。 > - 不支持IsolatedComponent组件嵌套场景。

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [IsolatedOptions](arkts-arkui-isolatedoptions-i-sys.md) | 用于在IsolatedComponent构造时传递构造参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ErrorCallback](arkts-arkui-errorcallback-t-sys.md) | 错误回调类型，用于接收异常信息。 |
| [RestrictedWorker](arkts-arkui-restrictedworker-t-sys.md) | 用于运行Abc的受限Worker。 |
| [Want](arkts-arkui-want-t-sys.md) | 表示Want。 |
