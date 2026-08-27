# FormLink

提供静态卡片交互组件，用于静态卡片内部和卡片提供方应用间的交互，当前支持router、message和call三种类型的事件。
> **说明：** > > - 该组件仅可以在静态卡片中使用。 > > - 本文仅提供静态卡片开发指导，其他卡片相关内容请参考[卡片开发指南](../../../form/formkit-overview.md)。

## 权限

无

## 子组件

支持单个子组件。

## FormLink

```TypeScript
FormLink(options: FormLinkOptions)
```

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FormLinkOptions](arkts-arkui-formlinkoptions-i.md) | 是 | 定义卡片信息 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [FormLinkOptions](arkts-arkui-formlinkoptions-i.md) |  |

## 示例

```TypeScript
@Entry
@Component
struct FormLinkDemo {
  build() {
    Column() {
      Text("这是一个静态卡片").fontSize(20).margin(10)

      // router事件用于静态卡片跳转到对应的UIAbility
      FormLink({
        action: "router",
        abilityName: "EntryAbility",
        params: {
          'message': 'testForRouter' // 自定义要发送的message
        }
      }) {
        Button("router event").width(120)
      }.margin(10)


      // message事件触发FormExtensionAbility的onFormEvent生命周期
      FormLink({
        action: "message",
        abilityName: "EntryAbility",
        params: {
          'message': 'messageEvent' // 自定义要发送的message
        }
      }) {
        Button("message event").width(120)
      }.margin(10)


      // call事件用于触发UIAbility中对应的方法
      FormLink({
        action: "call",
        abilityName: "EntryAbility",
        params: {
          'method': 'funA', // 在EntryAbility中调用的方法名
          'num': 1 // 需要传递的其他参数
        }
      }) {
        Button("call event").width(120)
      }.margin(10)

      // router事件用于静态卡片deeplink跳转到对应的UIAbility
      FormLink({
        action: "router",
        uri: 'example://uri.ohos.com/link_page',
        params: {
          message: 'router msg for static uri deeplink' // 自定义要发送的message
        }
      }) {
        Button("deeplink event").width(120)
      }.margin(10)
    }
    .justifyContent(FlexAlign.Center)
    .width('100%').height('100%')
  }
}
```

待跳转应用 [module.json5](../../../quick-start/module-configuration-file.md#skills标签) uris 配置示例：

```TypeScript
"abilities": [
  {
    "skills": [
      {
        "uris": [
          {
            "scheme": "example",
            "host": "uri.ohos.com",
            "path": "link_page"
          },
        ]
      }
    ],
  }
]
```
