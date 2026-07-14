# isCaptured

## isCaptured

```TypeScript
function isCaptured(): boolean
```

检查设备的屏幕显示信息是否被获取。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | boolean值，返回设备的屏幕显示信息是否存在被获取的情况。返回true表示设备的屏幕信息存在被获取的情况，可能为：设备正处于截屏、投屏、录屏状态，或已创建虚拟屏幕(虚拟屏幕可能被应用获取屏幕图像)；返回false则表示设备的屏幕信息不存在被获取的情况。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
let ret: boolean = false;
// 检查屏幕显示信息是否被获取
ret = display.isCaptured();

```


## isCaptured

```TypeScript
function isCaptured(bundleNameList: Array<string>): boolean
```

检查该设备是否被bundle名称列表中的任何应用抓拍、投影或录制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleNameList | Array&lt;string&gt; | 是 | 需要检查的应用包名称列表。数组的最大大小为100。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示该设备包名称列表中的任何应用捕获、投影或录制。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-参数异常) | Parameter error. Possible cause:1.The size of bundleNameList is larger than 100. |

**示例：**

```TypeScript
try {
  const bundleList: Array<string> = ['com.example.app'];
  let ret = display.isCaptured(bundleList);
  console.info(`The screen is captured or not: ${ret}`);
} catch (err) {
  console.error(`Failed to get display isCaptured. Code: ${err.code}, message: ${err.message}`);
}

```

