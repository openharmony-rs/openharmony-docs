# Preferences

Preferences继承自[ISendable](../../../../arkts-utils/arkts-sendable.md#isendable)，可以在ArkTS并发实例间（包括主线程、TaskPool&Worker工作线
程）传递，传递的行为是引用传递，提供获取和修改存储数据的接口。

下列接口都需先使用[sendablePreferences.getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)获取到Preferences实例，再通过此实例调用对应接
口。

**继承/实现关系：** Preferences extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-isendable-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## clear

```TypeScript
clear(): Promise<void>
```

清除缓存的Preferences实例中的所有数据，可通过[flush](arkts-arkdata-preferences-i.md#flush-1)将Preferences实例持久化，使用Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.clear();
promise.then(() => {
  console.info("Succeeded in clearing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to clear. code: ${err.code}, message: ${err.message}`);
});

```

## clearSync

```TypeScript
clearSync(): void
```

清除缓存的Preferences实例中的所有数据，可通过[flush](arkts-arkdata-preferences-i.md#flush-1)将Preferences实例持久化，此为同步接口。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
preferences.clearSync();

```

## delete

```TypeScript
delete(key: string): Promise<void>
```

从缓存的Preferences实例中删除名为给定Key的存储键值对，可通过[flush](arkts-arkdata-preferences-i.md#flush-1)将Preferences实例持久化，使用
Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要删除的存储Key名称，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.delete('startup');
promise.then(() => {
  console.info("Succeeded in deleting the key 'startup'.");
}).catch((err: BusinessError) => {
  console.error(`Failed to delete the key 'startup'. code: ${err.code}, message: ${err.message}`);
});

```

## deleteSync

```TypeScript
deleteSync(key: string): void
```

从缓存的Preferences实例中删除名为给定Key的存储键值对，可通过[flush](arkts-arkdata-preferences-i.md#flush-1)将Preferences实例持久化，此为同步接
口。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要删除的存储Key名称，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
preferences.deleteSync('startup');

```

## flush

```TypeScript
flush(): Promise<void>
```

将缓存的Preferences实例中的数据异步存储到共享用户首选项的持久化文件中，使用Promise异步回调。

> **说明：**
>
> 当数据未修改或修改后的数据与缓存数据一致时，不会刷新持久化文件。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.flush();
promise.then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## flushSync

```TypeScript
flushSync(): void
```

将缓存的Preferences实例中的数据存储到共享用户首选项的持久化文件中。

> **说明：**
>
> 当数据未修改或修改后的数据与缓存数据一致时，不会刷新持久化文件。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
preferences.flushSync();

```

## get

```TypeScript
get(key: string, defValue: lang.ISendable): Promise<lang.ISendable>
```

从缓存的Preferences实例中获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue，使用Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储Key名称，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |
| defValue | lang.ISendable | 是 | 默认返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;lang.ISendable&gt; | Promise对象，返回键对应的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let promise = preferences.get('startup', 'default');
promise.then((data: lang.ISendable) => {
  let dataStr = data as string;
  console.info(`Succeeded in getting value of 'startup'. Data: ${dataStr}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get value of 'startup'. code: ${err.code}, message: ${err.message}`);
});

```

## getAll

```TypeScript
getAll(): Promise<lang.ISendable>
```

获取缓存的Preferences实例中的所有键值数据。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;lang.ISendable&gt; | Promise对象，返回所有包含的键值数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let promise = preferences.getAll();
promise.then((keyValues: lang.ISendable) => {
  for (let value of Object.keys(keyValues)) {
    console.info("getAll " + JSON.stringify(value));
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get all key-values. code: ${err.code}, message: ${err.message}`);
});

```

## getAllSync

```TypeScript
getAllSync(): lang.ISendable
```

获取缓存的Preferences实例中的所有键值数据，此为同步接口。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| lang.ISendable | 返回所有包含的键值数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { lang } from '@kit.ArkTS';

let keyValues: lang.ISendable = preferences.getAllSync();
for (let value of Object.keys(keyValues)) {
  console.info("getAll " + JSON.stringify(value));
}

```

## getSync

```TypeScript
getSync(key: string, defValue: lang.ISendable): lang.ISendable
```

从缓存的Preferences实例中获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue，此为同步接口。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储Key名称，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |
| defValue | lang.ISendable | 是 | 默认返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| lang.ISendable | 返回键对应的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { lang } from '@kit.ArkTS';

let value: lang.ISendable = preferences.getSync('startup', 'default');

```

## has

```TypeScript
has(key: string): Promise<boolean>
```

检查缓存的Preferences实例中是否包含名为给定Key的存储键值对，使用Promise异步回调。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要检查的存储Key名称，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回Preferences实例是否包含给定Key的存储键值对，true表示存在，false表示不存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.has('startup');
promise.then((val: boolean) => {
  if (val) {
    console.info("The key 'startup' is contained.");
  } else {
    console.info("The key 'startup' does not contain.");
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to check the key 'startup'. code: ${err.code}, message: ${err.message}`);
});

```

## hasSync

```TypeScript
hasSync(key: string): boolean
```

检查缓存的Preferences实例中是否包含名为给定Key的存储键值对，此为同步接口。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要检查的存储Key名称，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回Preferences实例是否包含给定Key的存储键值对，true表示存在，false表示不存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
let isExist: boolean = preferences.hasSync('startup');
if (isExist) {
  console.info("The key 'startup' is contained.");
} else {
  console.info("The key 'startup' does not contain.");
}

```

## off('change')

```TypeScript
off(type: 'change', callback?: Callback<string>): void
```

取消订阅数据变更。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;string&gt; | 否 | 需要取消的回调函数，若不填写，表示取消所有已注册的回调函数；若填写，表示只取消指定的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('change', observer);
preferences.putSync('startup', 'auto');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
  preferences.off('change', observer);
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## off('multiProcessChange')

```TypeScript
off(type: 'multiProcessChange', callback?: Callback<string>): void
```

取消订阅进程间数据变更。

本接口提供给申请了[dataGroupId](arkts-arkdata-options-i.md)的应用进行使用，未申请的应用不推荐使用，多进程操作可能会损坏持久化文件，导致数据丢失。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'multiProcessChange' | 是 | 事件类型，固定值'multiProcessChange'，表示多进程间的数据变更。 |
| callback | Callback&lt;string&gt; | 否 | 需要取消的回调函数，若不填写，表示取消所有已注册的回调函数；若填写，表示只取消指定的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('multiProcessChange', observer);
preferences.putSync('startup', 'auto');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
  preferences.off('multiProcessChange', observer);
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## off('dataChange')

```TypeScript
off(type: 'dataChange', keys: Array<string>, callback?: Callback<lang.ISendable>): void
```

取消精确订阅数据变更。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataChange' | 是 | 事件类型，固定值'dataChange'，表示精确的数据变更。 |
| keys | Array&lt;string&gt; | 是 | 需要取消订阅的Key集合，当Keys为空数组时，表示取消订阅全部Key；当Keys为非空数组时，表示只取消订阅Key集合中的Key。 |
| callback | Callback&lt;lang.ISendable&gt; | 否 | 需要取消的回调函数，若不填写，表示取消所有已注册的回调函数；若填写，表示只取消指定的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let observer = (data: lang.ISendable) => {
  console.info(`observer : ${data}`);
};
let keys = ['name', 'age'];
preferences.on('dataChange', keys, observer);
preferences.putSync('name', 'xiaohong');
preferences.putSync('weight', 125);
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
  preferences.off('dataChange', keys, observer);
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## on('change')

```TypeScript
on(type: 'change', callback: Callback<string>): void
```

订阅数据变更，订阅的Key的值发生变更后，在执行flush方法后，触发callback回调。

> **不同订阅方法的对比：**
>
> - on('change')：订阅所有Key变化，适合全局数据变化感知需求。
>
> - on('dataChange')：精确订阅指定Key的变化，适合关注特定数据场景，可回调返回具体值。
>
> **选取建议：** 需要监听所有数据变更时使用on('change')；需要精确知道特定Key变化并获取新值时使用on('dataChange')。
> > **说明：**
>
> 当调用[removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-1)或者
> [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-1)后，订阅的数据变更会主动取消订阅，在重新
> [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)后需要重新订阅数据变更。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;string&gt; | 是 | 回调函数。返回发生变更的Key。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('change', observer);
preferences.putSync('startup', 'manual');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## on('multiProcessChange')

```TypeScript
on(type: 'multiProcessChange', callback: Callback<string>): void
```

订阅进程间数据变更，多个进程持有同一个首选项文件时，在任意一个进程（包括本进程）执行[flush](arkts-arkdata-preferences-i.md#flush-1)方法，持久化文件发生变更后，触发
callback回调。

本接口提供给申请了[dataGroupId](arkts-arkdata-options-i.md)的应用进行使用，未申请的应用不推荐使用，多进程操作可能会损坏持久化文件，导致数据丢失。

> **说明：**
>
> 同一持久化文件在当前进程订阅进程间数据变更的最大数量为50次，超过最大限制后会订阅失败。建议在触发callback回调后及时取消订阅。
>
> 当调用[removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-1)或者
> [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-1)后，订阅的数据变更会主动取消订阅，在重新
> [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)后需要重新订阅数据变更。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'multiProcessChange' | 是 | 事件类型，固定值'multiProcessChange'，表示多进程间的数据变更。 |
| callback | Callback&lt;string&gt; | 是 | 回调函数。返回发生变更的Key。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |
| [15500019](../errorcode-preferences.md#15500019-获取订阅服务失败) | Failed to obtain the subscription service. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let observer = (key: string) => {
  console.info("The key " + key + " changed.");
};
preferences.on('multiProcessChange', observer);
preferences.putSync('startup', 'manual');
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## on('dataChange')

```TypeScript
on(type: 'dataChange', keys: Array<string>, callback: Callback<lang.ISendable>): void
```

精确订阅数据变更，只有被订阅的Key值发生变更后，在执行[flush](arkts-arkdata-preferences-i.md#flush-1)方法后，触发callback回调。

> **说明：**
>
> 当调用[removePreferencesFromCache](arkts-arkdata-removepreferencesfromcache-f.md#removepreferencesfromcache-1)或者
> [deletePreferences](arkts-arkdata-deletepreferences-f.md#deletepreferences-1)后，订阅的数据变更会主动取消订阅，在重新
> [getPreferences](arkts-arkdata-getpreferences-f.md#getpreferences-1)后需要重新订阅数据变更。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataChange' | 是 | 事件类型，固定值'dataChange'，表示精确的数据变更。 |
| keys | Array&lt;string&gt; | 是 | 需要订阅的Key集合。 |
| callback | Callback&lt;lang.ISendable&gt; | 是 | 回调函数。回调支持返回多个键值对，其中键为发生变更的订阅Key，值为变更后的数据：支持number、string、boolean、bigint以及可序列化的object。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { lang } from '@kit.ArkTS';

let observer = (data: lang.ISendable) => {
  console.info(`observer : ${data}`);
};
let keys = ['name', 'age'];
preferences.on('dataChange', keys, observer);
preferences.putSync('name', 'xiaohong');
preferences.putSync('weight', 125);
preferences.flush().then(() => {
  console.info("Succeeded in flushing.");
}).catch((err: BusinessError) => {
  console.error(`Failed to flush. code: ${err.code}, message: ${err.message}`);
});

```

## put

```TypeScript
put(key: string, value: lang.ISendable): Promise<void>
```

将数据写入缓存的Preferences实例中，可通过[flush](arkts-arkdata-preferences-i.md#flush-1)将Preferences实例持久化，使用Promise异步回调。

> **说明：**
>
> 当value中包含非UTF-8格式的字符串时，请使用Uint8Array类型存储，否则会造成持久化文件出现格式错误造成文件损坏。
>
> 当对应的键已经存在时，put()方法会覆盖其值。可以使用hasSync()方法检查是否存在对应键值对。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要修改的存储的Key，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |
| value | lang.ISendable | 是 | 存储的新值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = preferences.put('startup', 'auto');
promise.then(() => {
  console.info("Succeeded in putting value of 'startup'.");
}).catch((err: BusinessError) => {
  console.error(`Failed to put value of 'startup'. code: ${err.code}, message: ${err.message}`);
});

```

## putSync

```TypeScript
putSync(key: string, value: lang.ISendable): void
```

将数据写入缓存的Preferences实例中，可通过[flush](arkts-arkdata-preferences-i.md#flush-1)将Preferences实例持久化，此为同步接口。

> **说明：**
>
> 当value中包含非UTF-8格式的字符串时，请使用Uint8Array类型存储，否则会造成持久化文件出现格式错误造成文件损坏。
>
> 当对应的键已经存在时，putSync()方法会覆盖其值。可以使用hasSync()方法检查是否存在对应键值对。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要修改的存储的Key，不能为空，最大长度限制为[MAX_KEY_LENGTH](../../../../reference/apis-arkdata/js-apis-data-sendablePreferences.md#constants)。 |
| value | lang.ISendable | 是 | 存储的新值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |

**示例：**

```TypeScript
preferences.putSync('startup', 'auto');

```

