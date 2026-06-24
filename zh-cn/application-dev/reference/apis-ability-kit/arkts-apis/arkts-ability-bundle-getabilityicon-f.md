# getAbilityIcon

## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, abilityName: string, callback: AsyncCallback<image.PixelMap>): void
```

ͨ��bundleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| abilityName | string | 是 | Ҫ��ѯ��Ability������� |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | ����������Ϊ��εĻص�����������ָ��<br/>[PixelMap](@ohos.multimedia.image:image)�� |


## getAbilityIcon

```TypeScript
function getAbilityIcon(bundleName: string, abilityName: string): Promise<image.PixelMap>
```

ͨ��bundleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��Promise�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| abilityName | string | 是 | Ҫ��ѯ��Ability������� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Returns the PixelMap object representing the icon of the specified ability. |

