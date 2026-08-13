# isPiPEnabled

## isPiPEnabled

```TypeScript
function isPiPEnabled(): boolean
```

判断当前设备是否支持画中画功能。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PiPWindow-function isPiPEnabled(): boolean--><!--Device-PiPWindow-function isPiPEnabled(): boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前系统是否支持画中画功能。true表示支持，false则表示不支持。 |

## 示例

```TypeScript
let enable: boolean = PiPWindow.isPiPEnabled();
console.info('isPiPEnabled: ' + enable);
```

