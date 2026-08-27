# isolated_component(System API)

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IsolatedComponentAttribute(System API)](arkts-arkui-isolatedcomponentattribute-c-sys.md) | 仅支持width、height和backgroundColor通用属性。不支持通用事件。事件经过坐标转换后异步传递给受限Worker线程处理。不支持线程之间的事件冒泡，线程之间的UI交互存在事件冲突现象。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IsolatedOptions(System API)](arkts-arkui-isolatedoptions-i-sys.md) | 用于在IsolatedComponent构造时传递构造参数。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ErrorCallback(System API)](arkts-arkui-errorcallback-t-sys.md) | 错误回调类型，用于接收异常信息。 |
| [IsolatedComponentInterface(System API)](arkts-arkui-isolatedcomponentinterface-t-sys.md) | 创建IsolatedComponent组件，用于显示受限Worker运行的Abc。 |
| [RestrictedWorker(System API)](arkts-arkui-restrictedworker-t-sys.md) | 用于运行Abc的受限Worker。 |
| [Want(System API)](arkts-arkui-want-t-sys.md) | 表示Want。 |
<!--DelEnd-->

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IsolatedComponent(System API)](arkts-arkui-isolatedcomponent-con-sys.md) | IsolatedComponent用于支持在本页面内嵌入显示独立Abc（方舟字节码，.abc文件）提供的UI，展示的内容在受限Worker线程中运行。通常用于有Abc热更新（可动态替换IsolatedComponent加载的Abc文件，无需通过重新安装应用的方式实现内容更新）诉求的模块化开发场景。 |
| [IsolatedComponentInstance(System API)](arkts-arkui-isolatedcomponent-con-sys.md#isolatedcomponentinstance) | 定义IsolatedComponent组件实例。 |
<!--DelEnd-->
