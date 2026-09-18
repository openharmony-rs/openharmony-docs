# getCfgDirList (System API)

## Modules to Import

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getCfgDirList

```TypeScript
function getCfgDirList(callback: AsyncCallback<Array<string>>): void
```

Obtains a list of configuration level directories, in ascending order of priority. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the list of configuration level directories is successfully obtained, &lt;strong&gt;err&lt;/strong&gt; is &lt;strong&gt;undefined&lt;/strong&gt;, and &lt;strong&gt;data&lt;/strong&gt; is the obtained list. Otherwise, &lt;strong&gt;err&lt;/strong&gt; is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |


## getCfgDirList

```TypeScript
function getCfgDirList(): Promise<Array<string>>
```

Obtains a list of configuration level directories, in ascending order of priority. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the list of configuration level directories. |
