# getAbilityIcon（系统接口）

## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void
```

ͨ��bundleName��moduleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��callback�첽�ص���

��ȡ���÷���Ϣʱ����ҪȨ�ޡ�

> **˵����**
>
> ��API version 9��ʼ֧�֣���API version 10��ʼ����������ʹ��
> [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getMediaContent-5)
> �����

**起始版本：** 9

**废弃版本：** 10

**替代接口：** getMediaContent

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| moduleName | string | 是 | Ҫ��ѯ��Ӧ��Module���ơ� |
| abilityName | string | 是 | Ҫ��ѯ��Ability������� |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | �ص�����������ָ��[PixelMap](@ohos.multimedia.image:image)����Ϊ��������<br/>ʱ����Ρ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |


## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, moduleName: string, abilityName: string): Promise<image.PixelMap>
```

ͨ��bundleName��moduleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��Promise�첽�ص���

��ȡ���÷���Ϣʱ����ҪȨ�ޡ�

> **˵����**
>
> ��API version 9��ʼ֧�֣���API version 10��ʼ����������ʹ��
> [getMediaContent](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getMediaContent-5)
> �����

**起始版本：** 9

**废弃版本：** 10

**替代接口：** getMediaContent

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| moduleName | string | 是 | Ҫ��ѯ��Ӧ��Module���ơ� |
| abilityName | string | 是 | Ҫ��ѯ��Ability������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return PixelMap. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified module is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified ability is not found. |
| [17700026](../../errorcode-universal.md#17700026-The) | The specified bundle is disabled. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 需要替换为要查询的应用Bundle名称、Module名称和Ability组件名
let bundleName: string = "com.example.myapplication";
let moduleName: string = "entry";
let abilityName: string = "EntryAbility";

try {
  bundleManager.getAbilityIcon(bundleName, moduleName, abilityName).then((data) => {
    hilog.info(0x0000,'testTag', 'getAbilityIcon successful. Data: %{public}s',JSON.stringify(data));
  }).catch((error: BusinessError) => {
    hilog.error(0x0000,'testTag', 'getAbilityIcon failed. Cause: %{public}s',error.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityIcon failed. Cause: %{public}s', message);
}

```

