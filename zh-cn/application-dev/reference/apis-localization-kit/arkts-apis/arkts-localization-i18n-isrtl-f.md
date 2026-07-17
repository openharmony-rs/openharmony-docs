# isRTL

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## isRTL

```TypeScript
export function isRTL(locale: string): boolean
```

判断语言是否为镜像语言。在镜像语言下，UI界面需要[镜像显示](../../../../internationalization/i18n-ui-design.md#界面镜像)。

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function isRTL(locale: string): boolean--><!--Device-i18n-export function isRTL(locale: string): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locale | string | 是 | [表示区域ID的字符串](../../../../internationalization/i18n-locale-culture.md#实现原理)，由语言、脚本、国家地区组成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示该语言是镜像语言，false表示该语言不是镜像语言。 |

