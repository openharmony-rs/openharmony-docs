# @ohos.fontManager (字体管理)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @OningO-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

本模块为应用提供第三方字体的安装、卸载、查询以及字体服务死亡监听能力。具体为：
- 安装应用级或会话级字体文件，支持`.ttf`、`.ttc`、`.otf` 格式。
- 根据字体路径卸载已安装的字体。
- 查询已安装字体的作用范围。
- 注册字体服务死亡监听器，当字体服务异常退出时通知应用。

>  **说明：**
>
>  - 本模块首批接口从API version 26.0.1开始支持。
>
>  - 应用级字体在应用退出、字体服务退出、账号退出或设备重启时自动清理。会话级字体在账号退出或设备重启时清理。

**起始版本：** 26.0.1

## 导入模块

```ts
import { fontManager } from '@kit.LocalizationKit';
```

## FontScope

表示字体作用范围的枚举。

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 26.0.1

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| APP | 0 | 应用级字体。随应用注册生命周期管理，应用退出、字体服务退出、账号退出或设备重启时自动清理。适用于应用私有字体，需先调用[onFontObserver](#onfontobserver)注册监听后才能安装。 |
| SESSION | 1 | 会话级字体。不随应用退出而清理，仅在账号退出或设备重启时清理。适用于不强依赖安装应用的字体，生命周期独立于安装应用。 |

## FontClientObserver

字体服务状态监听器，当字体服务意外终止时，将调用[onServiceDied](#onServiceDied)回调通知。

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 26.0.1

### onServiceDied

onServiceDied(): void

字体服务异常退出时的回调函数。当字体服务意外终止时调用此方法，应用可在此回调中执行资源清理或重新注册等操作。

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 26.0.1

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

const observer: fontManager.FontClientObserver = {
  onServiceDied: () => {
    console.info('font service died');
  }
};
```

## installScopeFont

installScopeFont(url: string, scope: FontScope): Promise&lt;void&gt;

安装指定路径下的字体文件为应用级或会话级字体。使用Promise异步回调。
> **说明：**
>
> - 安装成功后，应用可以通过字体名称使用该字体。同一字体路径不可重复安装。
>
> - 支持安装的字体文件个数最大数量为200.从26.0.1版本开始，PC/2in1支持安装的字体文件最大数量为800。


**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| url | string | 是 | 待安装的字体文件路径，仅支持.ttf和.ttc格式的字体文件。 |
| scope | [FontScope](#fontscope) | 是 | 字体作用范围。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100101 | The font does not exist. |
| 31100102 | The font is not supported. |
| 31100103 | Failed to copy the font file. |
| 31100104 | The font file is installed. |
| 31100105 | Exceeded the maximum number of installed files. |
| 31100110 | Call failed due to system error. |
| 31100115 | The font observer is not registered. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function installScopeFont() {
  try {
    await fontManager.installScopeFont('fontPath', fontManager.FontScope.APP);
    console.info('installScopeFont suc');
  } catch (error) {
    console.error('installScopeFont err.' + error.code);
  }
}
```

## uninstallScopeFont

uninstallScopeFont(url: string): Promise&lt;void&gt;

根据字体路径卸载已安装的应用级或会话级字体。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| url | string | 是 | 需要卸载的字体路径。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100108 | Failed to delete the font file. |
| 31100110 | Call failed due to system error. |
| 31100112 | The scope font is not found. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function uninstallScopeFont() {
  try {
    await fontManager.uninstallScopeFont('fontPath');
    console.info('uninstallScopeFont suc');
  } catch (error) {
    console.error('uninstallScopeFont err.' + error.code);
  }
}
```

## getFontScope

getFontScope(url: string): Promise&lt;FontScope&gt;

查询指定路径字体的作用范围。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| url | string | 是 | 需要查询的字体路径。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[FontScope](#fontscope)&gt; | Promise对象，返回字体的作用范围。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100112 | The scope font is not found. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function getFontScope() {
  try {
    let scope = await fontManager.getFontScope('fontPath');
    console.info('font scope is ' + scope);
  } catch (error) {
    console.error('getFontScope err.' + error.code);
  }
}
```

## onFontObserver

onFontObserver(observer: FontClientObserver): void

注册字体服务死亡监听器。当字体服务异常退出时，通过监听器回调通知应用。注销监听器请使用[offFontObserver](#offfontobserver)。

> **说明：**
>
> 每个应用最多可注册一个监听器，重复注册将返回错误。同一设备上最多支持5个不同应用同时注册监听器。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| observer | [FontClientObserver](#fontclientobserver) | 是 | 字体服务死亡监听器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100113 | The font observer is already registered. |
| 31100114 | The maximum number of font observers has been reached. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

const observer: fontManager.FontClientObserver = {
  onServiceDied: () => {
    console.info('font service died, please clean up resources');
  }
};

try {
  fontManager.onFontObserver(observer);
  console.info('onFontObserver suc');
} catch (error) {
  console.error('onFontObserver err.' + error.code);
}
```

## offFontObserver

offFontObserver(): void

注销字体服务死亡监听器。如需重新注册，请先注销再调用[onFontObserver](#onfontobserver)。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**模型约束：** 此接口仅可在Stage模型下使用。

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100115 | The font observer is not registered. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

try {
  fontManager.offFontObserver();
  console.info('offFontObserver suc');
} catch (error) {
  console.error('offFontObserver err.' + error.code);
}
```
