# SizeChangeCallback

```TypeScript
export type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void
```

当输入法面板大小变化时触发的回调。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | window.Size | 是 | 当前面板大小。 |
| keyboardArea | KeyboardArea | 否 | 当前面板中可作为键盘区域的大小。当需要获取或监听键盘区域变化时传入此参数，不传入时默认为undefined（不返回键盘区域信息）。 |

