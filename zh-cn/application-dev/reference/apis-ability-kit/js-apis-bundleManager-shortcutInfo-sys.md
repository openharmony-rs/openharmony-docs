# ShortcutInfo (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->

系统应用使用的快捷方式类型定义。

> **说明：**
>
> 当前页面仅包含本模块的系统接口参数，其他公共参数定义可参考[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md)。

**起始版本：** 26.1.0

## 导入模块

```ts
import { shortcutManager } from '@kit.AbilityKit';
```

## ShortcutWant

快捷方式内定义的目标信息集合。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称               | 类型                                    | 只读 | 可选 | 说明                 |
| ------------------ | --------------------------------------- | --- | --- | -------------------- |
| action            | string                                  | 否   | 是  | 拉起快捷方式时要执行的操作。 |
| uri               | string                                  | 否   | 是  | 拉起快捷方式时要匹配的URI。 |
| flags             | number                                  | 否   | 是  | 拉起快捷方式时Want对象的处理方式，取值为枚举类型[Flags](js-apis-app-ability-wantConstant.md#flags)。 |
