# VisibilityType

卡片当前可见类型枚举。表示卡片在宿主界面上的可见状态，当卡片从桌面移入/移出屏幕或切换应用时状态会发生变化，开发者可据此优化卡片刷新策略。

**起始版本：** 23

<!--Device-formInfo-enum VisibilityType--><!--Device-formInfo-enum VisibilityType-End-->

**系统能力：** SystemCapability.Ability.Form

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

表示卡片为未知。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VisibilityType-UNKNOWN = 0--><!--Device-VisibilityType-UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Ability.Form

## FORM_VISIBLE

```TypeScript
FORM_VISIBLE = 1
```

表示卡片为可见。卡片在前台显示，会正常接收更新和可见性通知。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VisibilityType-FORM_VISIBLE = 1--><!--Device-VisibilityType-FORM_VISIBLE = 1-End-->

**系统能力：** SystemCapability.Ability.Form

## FORM_INVISIBLE

```TypeScript
FORM_INVISIBLE = 2
```

表示卡片为不可见。卡片不在前台显示，系统可能暂停更新以节省资源。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VisibilityType-FORM_INVISIBLE = 2--><!--Device-VisibilityType-FORM_INVISIBLE = 2-End-->

**系统能力：** SystemCapability.Ability.Form

