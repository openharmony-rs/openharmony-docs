# postCardAction

## 导入模块

```TypeScript
```

## postCardAction

```TypeScript
declare function postCardAction(component: Object, action: Object): void
```

Post Card Action.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | Object | 是 | indicate the card entry component. |
| action | Object | 是 | indicate the router, message or call event. |

**示例**

```TypeScript
Button('跳转')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'router',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      params: {
        message: 'testForRouter' // 自定义要发送的message
      }
    });
  })

Button('拉至后台')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'call',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      params: {
        method: 'fun', // 自定义调用的方法名，必填
        message: 'testForCall' // 自定义要发送的message
      }
    });
  })

Button('URI跳转')
  .width('40%')
  .height('20%')
  .onClick(() => {
    postCardAction(this, {
      action: 'router',
      uri: 'example://uri.ohos.com/link_page',
      params: {
        message: 'router msg for dynamic uri deeplink' // 自定义要发送的message
      }
    });
  })
```

待跳转应用 [module.json5](../../quick-start/module-configuration-file.md#skills标签) uris 配置示例：

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
          }
        ]
      }
    ]
  }
]
```
