# TextMenuItemId

自定义菜单项的Id值。用于识别菜单选项，内置菜单项Id值见下列属性表格。

**起始版本：** 12

<!--Device-unnamed-declare class TextMenuItemId--><!--Device-unnamed-declare class TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="equals"></a>
## equals

```TypeScript
equals(id: TextMenuItemId): boolean
```

判断TextMenuItemId是否相等。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-equals(id: TextMenuItemId): boolean--><!--Device-TextMenuItemId-equals(id: TextMenuItemId): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | 是 | TextMenuItemId的id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 两个TextMenuItemId是否相等。<br/>true表示相等，false表示不相等。 |

<a id="of"></a>
## of

```TypeScript
static of(id: ResourceStr): TextMenuItemId
```

根据id创建TextMenuItemId。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static of(id: ResourceStr): TextMenuItemId--><!--Device-TextMenuItemId-static of(id: ResourceStr): TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | [ResourceStr](arkts-arkui-resourcestr-t.md) | 是 | 菜单的id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | TextMenuItemId的对象。 |

## AI_WRITER

```TypeScript
static readonly AI_WRITER: TextMenuItemId
```

<!--RP1--><!--RP1End-->可对选中的文本进行润色、摘要提取、排版等，为一级菜单项。该菜单项依赖大模型能力，否则不生效。

**类型：** TextMenuItemId

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly AI_WRITER: TextMenuItemId--><!--Device-TextMenuItemId-static readonly AI_WRITER: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CAMERA_INPUT

```TypeScript
static readonly CAMERA_INPUT: TextMenuItemId
```

拍摄输入，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly CAMERA_INPUT: TextMenuItemId--><!--Device-TextMenuItemId-static readonly CAMERA_INPUT: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLLABORATION_SERVICE

```TypeScript
static readonly COLLABORATION_SERVICE: TextMenuItemId
```

互通服务，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly COLLABORATION_SERVICE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly COLLABORATION_SERVICE: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COPY

```TypeScript
static readonly COPY: TextMenuItemId
```

默认复制，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly COPY: TextMenuItemId--><!--Device-TextMenuItemId-static readonly COPY: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CUT

```TypeScript
static readonly CUT: TextMenuItemId
```

默认剪切，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly CUT: TextMenuItemId--><!--Device-TextMenuItemId-static readonly CUT: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PASTE

```TypeScript
static readonly PASTE: TextMenuItemId
```

默认粘贴，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly PASTE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly PASTE: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEARCH

```TypeScript
static readonly SEARCH: TextMenuItemId
```

搜索，为一级菜单项。对选中的文本提供搜索服务，拉起浏览器搜索选中文本内容。

**类型：** TextMenuItemId

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly SEARCH: TextMenuItemId--><!--Device-TextMenuItemId-static readonly SEARCH: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELECT_ALL

```TypeScript
static readonly SELECT_ALL: TextMenuItemId
```

默认全选，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly SELECT_ALL: TextMenuItemId--><!--Device-TextMenuItemId-static readonly SELECT_ALL: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SHARE

```TypeScript
static readonly SHARE: TextMenuItemId
```

分享，为一级菜单项。对选中的文本提供分享服务，拉起分享窗口分享选中文本内容。

**类型：** TextMenuItemId

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly SHARE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly SHARE: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE

```TypeScript
static readonly TRANSLATE: TextMenuItemId
```

翻译，为一级菜单项。对选中的文本提供翻译服务。

**类型：** TextMenuItemId

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly TRANSLATE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly TRANSLATE: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## address

```TypeScript
static readonly address: TextMenuItemId
```

导航前往，为一级菜单项。对选中的地址提供跳转服务，拉起地图应用。

**类型：** TextMenuItemId

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly address: TextMenuItemId--><!--Device-TextMenuItemId-static readonly address: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## askAI

```TypeScript
static readonly askAI: TextMenuItemId
```

<!--RP2--><!--RP2End-->对选中的文本提供AI问询能力，为一级菜单项。

**类型：** TextMenuItemId

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly askAI: TextMenuItemId--><!--Device-TextMenuItemId-static readonly askAI: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoFill

```TypeScript
static readonly autoFill: TextMenuItemId
```

自动填充，为一级菜单项。点击后会展开二级菜单项“密码保险箱”，仅支持[Search](../arkts-components/arkts-arkui-search.md)、[TextInput](../arkts-components/arkts-arkui-textinput.md)、[TextArea](../arkts-components/arkts-arkui-textarea.md)或[RichEditor](../arkts-components/arkts-arkui-richeditor.md)。

**类型：** TextMenuItemId

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly autoFill: TextMenuItemId--><!--Device-TextMenuItemId-static readonly autoFill: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dateTime

```TypeScript
static readonly dateTime: TextMenuItemId
```

新建日程，为一级菜单项。对选中的日期和时间提供跳转服务，拉起新建日程页面。

**类型：** TextMenuItemId

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly dateTime: TextMenuItemId--><!--Device-TextMenuItemId-static readonly dateTime: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## email

```TypeScript
static readonly email: TextMenuItemId
```

新建邮件，为一级菜单项。对选中的邮箱地址提供跳转服务，拉起邮箱应用。

**类型：** TextMenuItemId

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly email: TextMenuItemId--><!--Device-TextMenuItemId-static readonly email: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## passwordVault

```TypeScript
static readonly passwordVault: TextMenuItemId
```

密码保险箱，为二级菜单项。点击该菜单项后会拉起密码保险箱应用，该应用提供自动填充账号密码能力，仅支持[Search](../arkts-components/arkts-arkui-search.md)、[TextInput](../arkts-components/arkts-arkui-textinput.md)、[TextArea](../arkts-components/arkts-arkui-textarea.md)或[RichEditor](../arkts-components/arkts-arkui-richeditor.md)。

**类型：** TextMenuItemId

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly passwordVault: TextMenuItemId--><!--Device-TextMenuItemId-static readonly passwordVault: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## phoneNumber

```TypeScript
static readonly phoneNumber: TextMenuItemId
```

呼叫，为一级菜单项。对选中的电话号码跳转服务，拉起电话拨号页面。

**类型：** TextMenuItemId

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly phoneNumber: TextMenuItemId--><!--Device-TextMenuItemId-static readonly phoneNumber: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## url

```TypeScript
static readonly url: TextMenuItemId
```

打开链接，为一级菜单项。对选中的URL提供跳转服务，拉起浏览器搜索或者应用页面。

**类型：** TextMenuItemId

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextMenuItemId-static readonly url: TextMenuItemId--><!--Device-TextMenuItemId-static readonly url: TextMenuItemId-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

