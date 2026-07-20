# QueryCustomContentEvent

```TypeScript
type QueryCustomContentEvent = (queryType: CustomType[]) => Promise<CustomElement>
```

自定义内容查询事件。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type QueryCustomContentEvent = (queryType: CustomType[]) => Promise<CustomElement>--><!--Device-avMusicTemplate-type QueryCustomContentEvent = (queryType: CustomType[]) => Promise<CustomElement>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryType | [CustomType](arkts-avsession-avmusictemplate-customtype-t.md)[] | 是 | 自定义类型：包含用户基本信息、界面选项卡配置、代码编译选项和系统设置项。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CustomElement&gt; | Promise对象，返回我的页面的自定义元素。  |

