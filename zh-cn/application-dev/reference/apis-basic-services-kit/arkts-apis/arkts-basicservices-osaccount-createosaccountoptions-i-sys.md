# CreateOsAccountOptions（系统接口）

```TypeScript
interface CreateOsAccountOptions
```

表示用于创建系统账号的可选参数。

**起始版本：** 12

<!--Device-osAccount-interface CreateOsAccountOptions--><!--Device-osAccount-interface CreateOsAccountOptions-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## allowedPreinstalledBundles

```TypeScript
allowedPreinstalledBundles?: Array<string>
```

表示预置应用允许名单，仅名单中的应用可以被安装在设备上，默认为std::nullopt。

**类型：** Array&lt;string&gt;

**起始版本：** 19

<!--Device-CreateOsAccountOptions-allowedPreinstalledBundles?: Array<string>--><!--Device-CreateOsAccountOptions-allowedPreinstalledBundles?: Array<string>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## disallowedPreinstalledBundles

```TypeScript
disallowedPreinstalledBundles?: Array<string>
```

表示预置应用禁止名单，名单中的应用不可被安装在设备上，默认为空列表。

**类型：** Array&lt;string&gt;

**起始版本：** 19

<!--Device-CreateOsAccountOptions-disallowedPreinstalledBundles?: Array<string>--><!--Device-CreateOsAccountOptions-disallowedPreinstalledBundles?: Array<string>-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## localId

```TypeScript
localId?: number
```

要创建的系统帐户ID。如果不指定该参数，系统将自动分配一个ID。取值限定为整数。

**类型：** number

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CreateOsAccountOptions-localId?: int--><!--Device-CreateOsAccountOptions-localId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## shortName

```TypeScript
shortName: string
```

表示账号短名称（用作个人文件夹目录）。

**约束：**

1. 不允许出现的字符：&lt; &gt; | : " * ? / \
2. 不允许独立出现的字符串：.或..
3. 长度不超过255个字符。

**类型：** string

**起始版本：** 12

<!--Device-CreateOsAccountOptions-shortName: string--><!--Device-CreateOsAccountOptions-shortName: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token?: Uint8Array
```

表示从认证管理接口获取的token，默认为空。

**类型：** Uint8Array

**起始版本：** 24

<!--Device-CreateOsAccountOptions-token?: Uint8Array--><!--Device-CreateOsAccountOptions-token?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。
