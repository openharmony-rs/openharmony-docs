# IsolatedComponentAttribute（系统接口）

仅支持width、height和backgroundColor通用属性。不支持通用事件。事件经过坐标转换后异步传递给受限Worker线程处理。不支持线程之间的事件冒泡，线程之间的UI交互存在事件冲突现象。

**继承/实现关系：** IsolatedComponentAttribute extends CommonMethod<IsolatedComponentAttribute>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## onError

```TypeScript
onError(
    callback: ErrorCallback
  ): IsolatedComponentAttribute
```

IsolatedComponent加载的Abc（以Ability扩展形式运行）在运行过程中发生异常时触发本回调。可通过回调参数中的code、name和message获取错误信息并做处理。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](arkts-arkui-errorcallback-t-sys.md) | 是 | 异常发生时的错误回调，可通过回调参数获取code、name和message错误信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IsolatedComponentAttribute](arkts-arkui-isolatedcomponentattribute-c-sys.md) |  |
