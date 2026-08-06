# create

## create

```TypeScript
function create(): DisplaySync
```

创建DisplaySync对象，通过此对象设置UI自绘制内容帧率。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-displaySync-function create(): DisplaySync--><!--Device-displaySync-function create(): DisplaySync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回当前创建的DisplaySync对象实例。 |

**示例：**

```TypeScript
let backDisplaySync: displaySync.DisplaySync = displaySync.create();
```

