# HibernateCallback（系统接口）

```TypeScript
interface HibernateCallback
```

定义休眠事件回调接口。

**起始版本：** 26.1.0

<!--Device-power-interface HibernateCallback--><!--Device-power-interface HibernateCallback-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## onHibernate

```TypeScript
onHibernate(): Promise<void>
```

当设备即将进入休眠时调用的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HibernateCallback-onHibernate(): Promise<void>--><!--Device-HibernateCallback-onHibernate(): Promise<void>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## onWakeup

```TypeScript
onWakeup(hibernateResult: boolean): Promise<void>
```

当设备退出休眠时调用的回调。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HibernateCallback-onWakeup(hibernateResult: boolean): Promise<void>--><!--Device-HibernateCallback-onWakeup(hibernateResult: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hibernateResult | boolean | 是 | 表示休眠是否成功。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |
