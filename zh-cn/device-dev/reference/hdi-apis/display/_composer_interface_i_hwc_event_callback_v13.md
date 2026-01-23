# IHwcEventCallback

## 概述

**相关模块：**  [Display](_composer_display_v13.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [OnHwcEvent](#onhwcevent) ([in] unsigned int devId, [in] unsigned int eventId, [in] int[] eventData) | 环境变化回调接口。 |

## 成员函数说明

### OnHwcEvent()

```idl
IHwcEventCallback::OnHwcEvent([in] unsigned int devId, [in] unsigned int eventId, [in] int[] eventData)
```

**描述**

环境变化回调接口

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| devId | 显示设备ID。 |
| eventId | 环境ID。 |
| eventData | 环境数据。 |

**返回：**

0表示执行成功。

其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。