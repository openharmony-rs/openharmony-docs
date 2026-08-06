# back

## back

```TypeScript
function back(options?: RouterOptions): void
```

返回上一页面或指定的页面，会删除当前页面与指定页面之间的所有页面。如果此前调用了\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 开启了返回询问对话框，则在执行返回操作时会先弹出确认对话框，用户确认后才执行返回；用户取消则不执行返回。 > **说明：** > > - 从API version 8开始支持，从API version 18开始废弃，建议使用 > [back]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_替代。back需先通过 > [UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_对象。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#back](arkts-arkui-arkui-uicontext-router-c.md#back)(options?:

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function back(options?: RouterOptions): void--><!--Device-router-function back(options?: RouterOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 返回页面描述信息，其中url指返回目标页面的路由地址，如果页面栈中不存在指定url的页面，则不响应当前返回请求。如果url未设置，则返回上一页，页面不会重新构建，页面栈里面的page不会回收，出栈后会被回收。back是返回接口，url设置为特殊值"/"不生效。如果是用命名路由的方式跳转，传入的url需是命名路由的名称。 |

**示例：**

```TypeScript
this.getUIContext().getRouter().back({ url: 'pages/detail' });
```


## back

```TypeScript
function back(index: number, params?: Object): void
```

返回指定的页面，会删除当前页面与指定页面之间的所有页面。如果此前调用了\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 开启了返回询问对话框，则在执行返回操作时会先弹出确认对话框，用户确认后才执行返回；用户取消则不执行返回。 > **说明：** > > - 从API version 12开始支持，从API version 18开始废弃，建议使用 > [back]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_替代。back需先通过 > [UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 12开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_对象。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#back](arkts-arkui-arkui-uicontext-router-c.md#back)(index:

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-router-function back(index: number, params?: Object): void--><!--Device-router-function back(index: number, params?: Object): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 返回目标页面的索引值，取值范围[1, 页面栈大小]，页面栈最大数量为32。从栈底到栈顶，index从1开始递增。索引不存在或超出页面栈有效范围时不响应。 |
| params | Object | 否 | 页面返回时携带的参数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：** \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_params参数只能传递可序列化的参数，不能传递方法和系统接口返回的对象（例如，媒体接口定义和返回的PixelMap对象）。建议开发者提取系统接口返回的对象中需要被传递的基础类型属性，自行构造object类型对象进行传递。 |

**示例：**

```TypeScript
this.getUIContext().getRouter().back(1);
```

```TypeScript
this.getUIContext().getRouter().back(1, { info: '来自Home页' }); // 携带参数返回
```

