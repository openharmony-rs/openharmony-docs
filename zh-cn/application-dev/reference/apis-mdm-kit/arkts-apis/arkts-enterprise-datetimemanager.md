# @ohos.enterprise.dateTimeManager

本模块提供系统时间管理能力。

> **说明**：  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对[设备管理应用](../../../../mdm/mdm-kit-term.md#mdm应用设备管理应用)开放，需将  
> [设备管理应用激活](arkts-mdm-adminmanager-enableadmin-f-sys.md#enableadmin-3)  
> 后调用。  
>  
> 本模块接口均为系统接口。

**起始版本：** 9

<!--Device-unnamed-declare namespace dateTimeManager--><!--Device-unnamed-declare namespace dateTimeManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dateTimeManager } from '@kit.MDMKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disallowModifyDateTime](arkts-mdm-datetimemanager-disallowmodifydatetime-f-sys.md#disallowmodifydatetime-1) | 禁止设备修改系统时间。使用callback异步回调。 |
| [disallowModifyDateTime](arkts-mdm-datetimemanager-disallowmodifydatetime-f-sys.md#disallowmodifydatetime-2) | 禁止设备修改系统时间。使用Promise异步回调。 |
| [isModifyDateTimeDisallowed](arkts-mdm-datetimemanager-ismodifydatetimedisallowed-f-sys.md#ismodifydatetimedisallowed-1) | 查询设备是否允许修改系统时间。使用callback异步回调。 |
| [isModifyDateTimeDisallowed](arkts-mdm-datetimemanager-ismodifydatetimedisallowed-f-sys.md#ismodifydatetimedisallowed-2) | 查询设备是否允许修改系统时间。使用Promise异步回调。 |
| [setDateTime](arkts-mdm-datetimemanager-setdatetime-f-sys.md#setdatetime-1) | 设置系统时间。使用callback异步回调。 |
| [setDateTime](arkts-mdm-datetimemanager-setdatetime-f-sys.md#setdatetime-2) | 设置系统时间。使用Promise异步回调。 |
<!--DelEnd-->

