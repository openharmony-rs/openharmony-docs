# isPiPEnabled

## isPiPEnabled

```TypeScript
function isPiPEnabled(): boolean
```

判断当前设备是否支持画中画功能。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前系统是否支持画中画功能。true表示支持，false则表示不支持。 |

**示例：**

```TypeScript
let enable: boolean = PiPWindow.isPiPEnabled(); // 获取当前系统是否支持画中画功能
console.info('isPiPEnabled:' + enable);

```

