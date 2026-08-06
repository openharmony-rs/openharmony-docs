# onSystemBarTintChange（系统接口）

## onSystemBarTintChange

```TypeScript
function onSystemBarTintChange(callback: Callback<SystemBarTintState>): void
```

开启状态栏、导航栏属性变化的监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-window-function onSystemBarTintChange(callback: Callback<SystemBarTintState>): void--><!--Device-window-function onSystemBarTintChange(callback: Callback<SystemBarTintState>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SystemBarTintState&gt; | 是 | 回调函数。返回当前的状态栏、导航栏信息集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
try {
  window.onSystemBarTintChange((data) => {
    console.info(`Succeeded in enabling the listener for systemBarTint changes. Data: ${JSON.stringify(data)}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to enable the listener for systemBarTint changes. Cause code: ${error.code}, message: ${error.message}`);
}
```

