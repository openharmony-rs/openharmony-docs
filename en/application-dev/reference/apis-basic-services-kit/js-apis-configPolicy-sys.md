# @ohos.configPolicy (Configuration Policy) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Customization-->
<!--Owner: @liule_123-->
<!--Designer: @sunshine_1984-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

The **configPolicy** module provides APIs for obtaining the corresponding directory and file path based on the predefined custom configuration level.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { configPolicy } from '@kit.BasicServicesKit';
```

## getOneCfgFile

getOneCfgFile(relPath: string, callback: AsyncCallback&lt;string&gt;)

Obtains the path of the configuration file with the highest priority. This API uses an asynchronous callback to return the result.
For example, if the paths of **config.xml** on the device are **/system/etc/config.xml** and **/sys_pod/etc/config.xml** in ascending order of priority, **/sys_pod/etc/config.xml** is returned.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name   | Type                        | Mandatory| Description                                 |
| -------- | --------------------------- | ---- | ------------------------------------ |
| relPath  | string                      | Yes  | Name of the configuration file.                          |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the configuration file path is successfully obtained, **err** is **undefined**, and **data** is the path of the configuration file with the highest priority. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  let relpath: string = 'etc/config.xml';
  configPolicy.getOneCfgFile(relpath, (err: BusinessError, data: string) => {
    if (err == null) {
      console.info('data is ' + data);
    } else {
      console.error('err: ' + err.code + ', ' + err.message);
    }
  });
  ```

## getOneCfgFile

getOneCfgFile(relPath: string): Promise&lt;string&gt;

Obtains the path of the configuration file with the highest priority. This API uses a promise to return the result.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name | Type  | Mandatory| Description      |
| ------- | ------ | ---- | ---------- |
| relPath | string | Yes  | Name of the configuration file.|

**Return value**

| Type                  | Description                    |
| ---------------------- | ------------------------ |
| Promise&lt;string&gt;  | Promise used to return the path of the configuration file with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  async function fetchConfigFile() {
    try {
      let relpath: string = 'etc/config.xml';
      let value: string = await configPolicy.getOneCfgFile(relpath);
      console.info('value is ' + value);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error:' + code + ', ' + message);
    }
  }

  fetchConfigFile();
  ```

## getCfgFiles

getCfgFiles(relPath: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;)

Obtains a list of all files with the specified names, in ascending order of priority. This API uses an asynchronous callback to return the result.
For example, if the paths of **config.xml** on the device are **/system/etc/config.xml** and **/sys_pod/etc/config.xml** in ascending order of priority, **/system/etc/config.xml, /sys_pod/etc/config.xml** is returned.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name  | Type                                    | Mandatory| Description                      |
| -------- | ---------------------------------------- | ---- | -------------------------- |
| relPath  | string                                   | Yes  | Name of the configuration file.                |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes  | Callback used to return the result. If the file list is successfully obtained, **err** is **undefined**, and **data** is the obtained file list. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  configPolicy.getCfgFiles('etc/config.xml', (err: BusinessError, data: Array<string>) => {
    if (err == null) {
      console.info('data is ' + data);
    } else {
      console.error('err: ' + err.code + ', ' + err.message);
    }
  });
  ```

## getCfgFiles

getCfgFiles(relPath: string): Promise&lt;Array&lt;string&gt;&gt;

Obtains a list of all files with the specified names, in ascending order of priority. This API uses a promise to return the result.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name | Type  | Mandatory| Description      |
| ------- | ------ | ---- | ---------- |
| relPath | string | Yes  | Name of the configuration file.|

**Return value**

| Type                              | Description    |
| ---------------------------------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the file list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  async function fetchCfgFiles() {
    try {
      let relpath: string = 'etc/config.xml';
      let value: Array<string> = await configPolicy.getCfgFiles(relpath);
      console.info('value is ' + value);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error:' + code + ', ' + message);
    }
  }

  fetchCfgFiles();
  ```

## getCfgDirList

getCfgDirList(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;)

Obtains a list of configuration level directories, in ascending order of priority. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name  | Type                                    | Mandatory| Description                              |
| -------- | ---------------------------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes  | Callback used to return the result. If the list of configuration level directories is successfully obtained, **err** is **undefined**, and **data** is the obtained list. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  configPolicy.getCfgDirList((err: BusinessError, data: Array<string>) => {
    if (err == null) {
      console.info('data is ' + data);
    } else {
      console.error('err: ' + err.code + ', ' + err.message);
    }
  });
  ```

## getCfgDirList

getCfgDirList(): Promise&lt;Array&lt;string&gt;&gt;

Obtains a list of configuration level directories, in ascending order of priority. This API uses a promise to return the result.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Return value**

| Type                              | Description            |
| ---------------------------------- | ---------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the list of configuration level directories.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  async function fetchCfgDirList() {
    try {
      let value: Array<string> = await configPolicy.getCfgDirList();
      console.info('value is ' + value);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error:' + code + ', ' + message);
    }
  }

  fetchCfgDirList();
  ```

## getOneCfgFile<sup>11+</sup>

getOneCfgFile(relPath: string, followMode: FollowXMode, callback: AsyncCallback&lt;string&gt;)

Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses an asynchronous callback to return the result.
For example, if the paths of **config.xml** on the device are **/system/etc/config.xml**, **/sys_pod/etc/config.xml**, and **/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the default opkey of the device is **46060**, and **followMode** is set to **configPolicy.FollowXMode.SIM_DEFAULT**, the final return value is **/sys_pod/etc/carrier/46060/etc/config.xml**.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                         | Mandatory| Description                                      |
| ---------- | ----------------------------- | ---- | ------------------------------------------ |
| relPath    | string                        | Yes  | Name of the configuration file.                                |
| followMode | [FollowXMode](#followxmode11) | Yes  | Follow mode.                                  |
| callback   | AsyncCallback&lt;string&gt;   | Yes  | Callback used to return the result. If the configuration file path is successfully obtained, **err** is **undefined**, and **data** is the path of the configuration file with the highest priority. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  let relpath: string = 'etc/config.xml';
  configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.SIM_DEFAULT,
    (err: BusinessError, data: string) => {
      if (err == null) {
        console.info('data is ' + data);
      } else {
        console.error('err: ' + err.code + ', ' + err.message);
      }
    });

  ```

## getOneCfgFile<sup>11+</sup>

getOneCfgFile(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback&lt;string&gt;)

Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses an asynchronous callback to return the result.
For example, if the paths of **config.xml** on the device are **/system/etc/config.xml**, **/sys_pod/etc/config.xml**, and **/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the opkey of the device card 1 is **46060**, **followMode** is set to **configPolicy.FollowXMode.USER_DEFINED**, and the custom follow rule is **"etc/carrier/${telephony.sim.opkey0}"**, the final return value is **/sys_pod/etc/carrier/46060/etc/config.xml**.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                         | Mandatory| Description                                                  |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | Yes  | Name of the configuration file.                                            |
| followMode | [FollowXMode](#followxmode11) | Yes  | Follow mode.                                              |
| extra      | string                        | Yes  | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](#followxmode11).|
| callback   | AsyncCallback&lt;string&gt;   | Yes  | Callback used to return the result. If the configuration file path is successfully obtained, **err** is **undefined**, and **data** is the path of the configuration file with the highest priority. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  let relpath: string = 'etc/config.xml';
  let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
  configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.USER_DEFINED, extra,
    (err: BusinessError, data: string) => {
      if (err == null) {
        console.info('data is ' + data);
      } else {
        console.error('err: ' + err.code + ', ' + err.message);
      }
    });
  ```

## getOneCfgFile<sup>11+</sup>

getOneCfgFile(relPath: string, followMode: FollowXMode, extra?: string): Promise&lt;string&gt;

Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses a promise to return the result.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                         | Mandatory| Description                                                  |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | Yes  | Name of the configuration file.                                            |
| followMode | [FollowXMode](#followxmode11) | Yes  | Follow mode.                                              |
| extra      | string                        | No  | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](#followxmode11).|

**Return value**

| Type                  | Description                    |
| ---------------------- | ------------------------ |
| Promise&lt;string&gt;  | Promise used to return the path of the configuration file with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  async function fetchOneCfgFile() {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      let value: string = await configPolicy.getOneCfgFile(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra);
      console.info('value is ' + value);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error:' + code + ', ' + message);
    }
  }

  fetchOneCfgFile();
  ```

## getOneCfgFileSync<sup>11+</sup>

getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string

Obtains the path of the configuration file with the highest priority based on the provided follow mode.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                         | Mandatory| Description                                                |
| ---------- | ----------------------------- | ---- | ----------------------------------------------------|
| relPath    | string                        | Yes  | Name of the configuration file.                                          |
| followMode | [FollowXMode](#followxmode11) | No  | Follow mode. The default value is [DEFAULT](#followxmode11) if this parameter is not set.                   |
| extra      | string                        | No  | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](#followxmode11).|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| string | The path of the configuration file with the highest priority obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  try {
    let relpath: string = 'etc/config.xml';
    let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
    let result: string = configPolicy.getOneCfgFileSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
    console.info('result is ' + result);
  } catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error('error:' + code + ', ' + message);
  }
  ```

## getCfgFiles<sup>11+</sup>

getCfgFiles(relPath: string, followMode: FollowXMode, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;)

Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. This API uses an asynchronous callback to return the result.
For example, if the paths of **config.xml** on the device are **/system/etc/config.xml**, **/sys_pod/etc/config.xml**, and **/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the default opkey of the device is **46060**, and **followMode** is set to **configPolicy.FollowXMode.SIM_DEFAULT**, the return value is **/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml**.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                                    | Mandatory| Description                      |
| ---------- | ---------------------------------------- | ---- | -------------------------- |
| relPath    | string                                   | Yes  | Name of the configuration file.                |
| followMode | [FollowXMode](#followxmode11)            | Yes  | Follow mode.                  |
| callback   | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes  | Callback used to return the result. If the file list is successfully obtained, **err** is **undefined**, and **data** is the obtained file list. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  let relpath: string = 'etc/config.xml';
  configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT,
    (err: BusinessError, data: Array<string>) => {
      if (err == null) {
        console.info('data is ' + data);
      } else {
        console.error('err: ' + err.code + ', ' + err.message);
      }
    });
  ```

## getCfgFiles<sup>11+</sup>

getCfgFiles(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;)

Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. This API uses an asynchronous callback to return the result.
For example, if the paths of **config.xml** on the device are **/system/etc/config.xml**, **/sys_pod/etc/config.xml**, and **/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the opkey of the device card 1 is **46060**, **followMode** is set to **configPolicy.FollowXMode.USER_DEFINED**, and the custom follow rule is **"etc/carrier/${telephony.sim.opkey0}"**, the return value is **/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml**.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                                    | Mandatory| Description                                                  |
| ---------- | ---------------------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                                   | Yes  | Name of the configuration file.                                            |
| followMode | [FollowXMode](#followxmode11)            | Yes  | Follow mode.                                              |
| extra      | string                                   | Yes  | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](#followxmode11).|
| callback   | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes  | Callback used to return the result. If the file list is successfully obtained, **err** is **undefined**, and **data** is the obtained file list. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  let relpath: string = 'etc/config.xml';
  let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
  configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra,
    (err: BusinessError, data: Array<string>) => {
      if (err == null) {
        console.info('data is ' + data);
      } else {
        console.error('err: ' + err.code + ', ' + err.message);
      }
    });
  ```

## getCfgFiles<sup>11+</sup>

getCfgFiles(relPath: string, followMode: FollowXMode, extra?: string): Promise&lt;Array&lt;string&gt;&gt;

Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority. This API uses a promise to return the result.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                         | Mandatory| Description                                                  |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | Yes  | Name of the configuration file.                                            |
| followMode | [FollowXMode](#followxmode11) | Yes  | Follow mode.                                              |
| extra      | string                        | No  | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](#followxmode11).|

**Return value**

| Type                              | Description    |
| ---------------------------------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the file list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  async function fetchCfgFiles() {
    try {
      let relpath: string = 'etc/config.xml';
      let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
      let value: Array<string> = await configPolicy.getCfgFiles(relpath, configPolicy.FollowXMode.SIM_DEFAULT, extra);
      console.info('value is ' + value);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error('error:' + code + ', ' + message);
    }
  }

  fetchCfgFiles();
  ```

## getCfgFilesSync<sup>11+</sup>

getCfgFilesSync(relPath: string, followMode?: FollowXMode, extra?: string): Array&lt;string&gt;

Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Parameters**

| Name    | Type                         | Mandatory| Description                                                  |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------ |
| relPath    | string                        | Yes  | Name of the configuration file.                                            |
| followMode | [FollowXMode](#followxmode11) | No  | Follow mode. The default value is [DEFAULT](#followxmode11) if this parameter is not set.                   |
| extra      | string                        | No  | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](#followxmode11).|

**Return value**

| Type               | Description    |
| ------------------- | -------- |
| Array&lt;string&gt; | List of configuration files obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed.|

**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  try {
    let relpath: string = 'etc/config.xml';
    let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
    let result: Array<string> = configPolicy.getCfgFilesSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
    console.info('result is ' + result);
  } catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error('error:' + code + ', ' + message);
  }
  ```

## getCfgDirListSync<sup>11+</sup>

getCfgDirListSync(): Array&lt;string&gt;

Obtains a list of configuration level directories, in ascending order of priority.

**System capability**: SystemCapability.Customization.ConfigPolicy

**Return value**

| Type               | Description            |
| ------------------- | ---------------- |
| Array&lt;string&gt; | Obtains the list of configuration level directories. This API returns the result synchronously.|


**Example**

  ```ts
  import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

  try {
    let result: Array<string> = configPolicy.getCfgDirListSync();
    console.info('result is ' + result);
  } catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error('error:' + code + ', ' + message);
  }
  ```

## FollowXMode<sup>11+</sup>

**System capability**: SystemCapability.Customization.ConfigPolicy

| Name                          | Value | Description                                                                                           |
| ----------------------------- | --- | ----------------------------------------------------------------------------------------------- |
| DEFAULT                       | 0   | Files are searched based on the follow rules configured in the **followx_file_list.cfg** file at each configuration level.                  |
| NO_RULE_FOLLOWED              | 1   | No follow rule is used even if the **followx_file_list.cfg** file exists.                               |
| SIM_DEFAULT                   | 10  | Files are searched in **etc/carrier/${opkey}** at each configuration level based on the opkey of the default card.                  |
| SIM_1                         | 11  | Files are searched in **etc/carrier/${opkey}** at each configuration level based on the opkey of card 1.                       |
| SIM_2                         | 12  | Files are searched in **etc/carrier/${opkey}** at each configuration level based on the opkey of card 2.                       |
| USER_DEFINED                  | 100 | In user-defined mode, configuration files are obtained based on the follow rule provided by **extra**, and the **followx_file_list.cfg** file at each configuration level is ignored.| 
