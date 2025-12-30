# DispatchInfo (系统接口)

免安装结构体和接口版本信息类，通过接口[freeInstall.getDispatchInfo](js-apis-freeInstall-sys.md#getdispatchinfo)获取。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块为系统接口。

## 导入模块

```js
import { freeInstall } from '@kit.AbilityKit';
```

## DispatchInfo

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 名称        | 类型   | 只读 | 可选 | 说明                     |
| ----------- | ------ | ---- | ---- | ------------------------ |
| version     | string | 是   | 否   | dispatchInfo结构体版本信息。 |
| dispatchAPIVersion | string | 是   | 否   | 免安装接口版本信息。     |
