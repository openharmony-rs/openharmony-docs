# getBundleInstaller（系统接口）

## getBundleInstaller

```TypeScript
function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void
```

��ȡ���ڰ�װ���Ľӿڣ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;BundleInstaller&gt; | 是 | �ص����������ذ�װ�ӿڶ��� |


## getBundleInstaller

```TypeScript
function getBundleInstaller(): Promise<BundleInstaller>
```

��ȡ���ڰ�װ���Ľӿڣ�ʹ��Promise�첽�ص������ذ�װ�ӿڶ���

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInstaller&gt; | Promise���󣬷��ذ�װ�ӿڶ��� |

