# isFeatureSupported

## 导入模块

```TypeScript
import { common } from '@kit.MDMKit';
```

## isFeatureSupported

```TypeScript
function isFeatureSupported(feature: ManagedFeature): boolean
```

查询是否支持某个管控特性

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| feature | [ManagedFeature](arkts-mdm-common-managedfeature-e.md) | 是 | 管控特性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示支持该特性，fasle表示不支持该特性。 |
