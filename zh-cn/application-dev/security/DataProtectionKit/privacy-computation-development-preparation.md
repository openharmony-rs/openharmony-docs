# 开发准备（隐私计算）
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @xling_feng_qing-->
<!--Designer: @Pawn_loading-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 环境要求

在使用隐私计算能力前，请确保满足以下环境要求：

- 设备：支持OpenHarmony API version 26.0.1及以上版本的设备。
- 开发工具：DevEco Studio，并配置对应版本的OpenHarmony SDK。
- 系统能力：设备需支持SystemCapability.Security.Asset。

## 模型约束

本模块接口可在FA模型和Stage模型下使用。

## 导入模块

在使用隐私计算接口前，需要先导入模块。

```TypeScript
import { privacyComputation } from '@kit.DataProtectionKit';
```

## 权限说明

本模块接口无需额外申请权限。

## 支持的协议与数据集大小

在调用接口前，需根据业务场景选择合适的隐私协议与数据集大小。

**表1** 隐私协议类型

| 协议类型 | 说明 |
| -------- | -------- |
| PSI_PROTOCOL | 隐私集合求交（PSI）协议，判断目标元素是否存在于数据集中。 |
| PIR_PROTOCOL | 隐私信息检索（PIR）协议，检索匹配项的附加值。 |

**表2** 数据集大小

| 数据集大小 | 说明 |
| -------- | -------- |
| SIZE_128 | 单个结果密文可以包含128次比较。 |
| SIZE_256 | 单个结果密文可以包含256次比较。 |
| SIZE_512 | 单个结果密文可以包含512次比较。 |

数据集大小决定单个结果密文可以包含的比较次数，结果密文总数由elements.size/dataSetSize决定。请根据隐私搜索中元素的数量与每个结果密文可接受的大小选择合适的取值。
