# UserGrantSetting

描述用户授权的设置信息。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface UserGrantSetting--><!--Device-unnamed-export interface UserGrantSetting-End-->

**系统能力：** SystemCapability.Notification.Notification

## grantedBundleInfos

```TypeScript
readonly grantedBundleInfos?: Array<GrantedBundleInfo>
```

“已获取的本机通知”通知开关开启的应用列表。

**类型：** Array<GrantedBundleInfo>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGrantSetting-readonly grantedBundleInfos?: Array<GrantedBundleInfo>--><!--Device-UserGrantSetting-readonly grantedBundleInfos?: Array<GrantedBundleInfo>-End-->

**系统能力：** SystemCapability.Notification.Notification

## userGrantEnabled

```TypeScript
readonly userGrantEnabled: boolean
```

“允许获取本机通知”的开关状态。 true：表示功能已启用；false：表示功能未启用。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserGrantSetting-readonly userGrantEnabled: boolean--><!--Device-UserGrantSetting-readonly userGrantEnabled: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

