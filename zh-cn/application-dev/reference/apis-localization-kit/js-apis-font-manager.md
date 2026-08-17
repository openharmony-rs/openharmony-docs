# @ohos.fontManager (字体管理)

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @OningO-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

本模块为应用提供第三方字体的安装、卸载、查询以及字体服务死亡监听能力。具体为：
- 安装应用级或会话级字体文件（支持.ttf、.ttc格式）。
- 根据字体路径卸载已安装的字体。
- 查询已安装字体的作用范围。
- 注册字体服务死亡监听器，当字体服务异常退出时通知应用。

>  **说明：**
>
>  - 本模块首批接口从API version 26.1.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  - 应用级字体在应用退出、字体服务退出、账号退出或设备重启时自动清理；会话级字体在账号退出或设备重启时清理。

## 导入模块

```ts
import { fontManager } from '@kit.LocalizationKit';
```

## FontScope

枚举字体作用范围。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Global.FontManager

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| app | 0 | 应用级字体。应用退出、字体服务退出、账号退出或设备重启时清理。 |
| session | 1 | 会话级字体。账号退出或设备重启时清理。 |

## FontClientObserver

字体服务死亡事件观察者，用于接收字体服务异常退出通知。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Global.FontManager

### onServiceDied

onServiceDied(): void

字体服务异常退出时的回调函数。当字体服务意外终止时调用此方法，应用可在此回调中执行资源清理或重新注册等操作。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Global.FontManager

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

installScopeFont(url: string, scope: FontScope): Promise&lt;number&gt;

安装指定路径下的字体文件为应用级或会话级字体。使用Promise异步回调。

安装成功后，应用可以通过字体名称使用该字体。同一字体路径不可重复安装。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| url | string | 是 | 待安装的字体文件路径，仅支持.ttf和.ttc格式的字体文件。 |
| scope | [FontScope](#fontscope) | 是 | 字体作用范围。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象，返回安装结果。<br>- 返回0：安装成功，字体已添加到字体库。<br>- 返回其他值：安装失败，请根据错误码排查原因。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 31100101 | The font does not exist. |
| 31100102 | The font is not supported. |
| 31100103 | Failed to copy the font file. |
| 31100104 | The font file is installed. |
| 31100105 | Exceeded the maximum number of installed files. |
| 31100106 | The system ability works abnormally. |
| 31100503 | Font observer not registered. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function installScopeFont() {
  try {
    let res = await fontManager.installScopeFont('fontPath', fontManager.FontScope.app);
    console.info('installScopeFont suc. res is ' + res);
  } catch (error) {
    console.error('installScopeFont err.' + error.code);
  }
}
```

## uninstallScopeFont

uninstallScopeFont(url: string): Promise&lt;number&gt;

根据字体路径卸载已安装的应用级或会话级字体。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| url | string | 是 | 需要卸载的字体路径。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象，返回卸载结果。<br>- 返回0：卸载成功，字体已从字体库中移除。<br>- 返回其他值：卸载失败，请根据错误码排查原因。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 31100107 | The font file does not exist. |
| 31100108 | Failed to delete the font file. |
| 31100109 | The system ability works abnormally. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function uninstallScopeFont() {
  try {
    let res = await fontManager.uninstallScopeFont('fontPath');
    console.info('uninstallScopeFont suc. res is ' + res);
  } catch (error) {
    console.error('uninstallScopeFont err.' + error.code);
  }
}
```

## getFontScope

getFontScope(url: string): Promise&lt;FontScope | null&gt;

查询指定路径字体的作用范围。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| url | string | 是 | 需要查询的字体路径。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[FontScope](#fontscope) \| null&gt; | Promise对象，返回查询结果。<br>- 返回FontScope枚举值：字体已安装，返回其作用范围。<br>- 返回null：字体未安装。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 31100110 | Call failed due to system error. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

async function getFontScope() {
  try {
    let scope = await fontManager.getFontScope('fontPath');
    if (scope == null) {
      console.info('font not installed');
    } else {
      console.info('font scope is ' + scope);
    }
  } catch (error) {
    console.error('getFontScope err.' + error.code);
  }
}
```

## onFontObserver

onFontObserver(observer: FontClientObserver): void

注册字体服务死亡监听器。当字体服务异常退出时，通过监听器回调通知应用。

每个应用最多可注册一个监听器，重复注册将返回错误。同一设备上最多支持5个不同应用同时注册监听器。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| observer | [FontClientObserver](#fontclientobserver) | 是 | 字体服务死亡监听器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 31100501 | Font observer already registered. |
| 31100502 | Exceeded maximum number of font observers. |

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

offFontObserver(observer: FontClientObserver): void

注销字体服务死亡监听器。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ----- | ------ | ---- | ----- |
| observer | [FontClientObserver](#fontclientobserver) | 是 | 已注册的字体服务死亡监听器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[字体管理错误码](errorcode-font-manager.md)。

| 错误码ID | 错误信息 |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 31100503 | Font observer not registered. |

**示例：**

```ts
import { fontManager } from '@kit.LocalizationKit';

const observer: fontManager.FontClientObserver = {
  onServiceDied: () => {}
};

try {
  fontManager.offFontObserver(observer);
  console.info('offFontObserver suc');
} catch (error) {
  console.error('offFontObserver err.' + error.code);
}
```
