# Sharing Configurations Between Applications (ArkTS)

<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @woodenarow-->
<!--Designer: @woodenarow; @xuelei3-->
<!--Tester: @chenwan188; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=deff468b8adbfa4199da5cbe7b6cbc33f2bddb1e translatedAt=2026-06-24T07:38:33.200Z pushedAt=2026-06-25T09:20:12.045Z -->

## When to Use

Sharing configurations between applications allows you to manage common configuration information in a centralized manner, thereby improving collaboration efficiency.

This feature is supported since API version 20.

## Working Principles

The working principles of configuration sharing between applications are as follows:

1. **Configuration publisher (data provider)**: provides default shared configuration items and dynamically modifies them. Currently, the following configuration modes are supported:

   - **Static configuration**: default shared configuration items are provided when the application package is installed. The configuration takes effect immediately without depending on the application startup.

   - **Dynamic configuration**: configuration items can be dynamically added, deleted, or modified via related APIs, without depending on application upgrade.

2. **Configuration accessor (data consumer)**: calls APIs to obtain configuration information or subscribe to or unsubscribe from configuration change notifications.

## Constraints

Before API version 26.0.0, an application can publish up to 32 configuration items. Starting from API version 26.0.0, the limit is increased to 64 configuration items per application. This limit applies to the combined total of static and dynamic configuration items.

## Available APIs

The following APIs are provided for inter-application configuration sharing. For detailed descriptions of these APIs, see [DataProxyHandle](../reference/apis-arkdata/js-apis-data-dataShare.md#dataproxyhandle20).

### Public APIs

| Name                       | Description                                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------------ |
| createDataProxyHandle(): Promise&lt;DataProxyHandle&gt; | Creates a data proxy operation handle, which is used to subscribe to, publish, and obtain configurations.|

### APIs for Configuration Publishers

| Name                                                    | Description              |
| ------------------------------------------------------------ | ------------------ |
| publish(data: ProxyData[], config: DataProxyConfig): Promise<DataProxyResult[]> | Publishes or modifies configuration items.|
| delete(uris: string[], config: DataProxyConfig): Promise<DataProxyResult[]> | Deletes the published configuration items corresponding to the specified URIs. |
| deleteMyPublishedData(config: DataProxyConfig): Promise<DataProxyResult[]> | Deletes all configuration items published by the publisher.<br/>**Since:** 26.0.0 |

### APIs for Configuration Accessors

| Name                                                    | Description                |
| ------------------------------------------------------------ | -------------------- |
| get(uris: string[], config: DataProxyConfig): Promise<DataProxyGetResult[]> | Obtains configuration items.    |
| on(event: 'dataChange', uris: string[], config: DataProxyConfig, callback: AsyncCallback<DataProxyChangeInfo[]>): DataProxyResult[] | Subscribes to configuration item changes.    |
| off(event: 'dataChange', uris: string[], config: DataProxyConfig, callback?: AsyncCallback<DataProxyChangeInfo[]>): DataProxyResult[] | Unsubscribes from configuration item changes.|

## Configuring the Publisher

### Configuration in module.json5

Reference the **shared_config.json** file by configuring the **crossAppSharedConfig** field in the **module.json5** file. The **shared_config.json** file defines the configuration items that can be shared between applications. You should store the file in the **resources/base/profile** directory of the project and reference it using the **$** symbol. 

```json5
{
  "module":{
    "crossAppSharedConfig": "$profile:shared_config"
  }
}
```

The file name **shared_config** of the shared configuration file **shared_config.json** is customizable. The root node, **crossAppSharedConfig**, is an array of objects that defines the shared configuration items.<br/>Before API version 26.0.0, an application can publish up to 32 configuration items. This limit applies to the combined total of static and dynamic configuration items. If more than 32 static configuration items are defined, only the first 32 items that comply with the **crossAppSharedConfig** configuration requirements are parsed. The remaining items are ignored.<br/>Starting from API version 26.0.0, an application can publish up to 64 configuration items. This limit applies to the combined total of static and dynamic configuration items. If more than 64 static configuration items are defined, only the first 64 items that comply with the **crossAppSharedConfig** configuration requirements are parsed. The remaining items are ignored.

The following table describes the parameters in the **crossAppSharedConfig** field.

| Name| Description| Type| Mandatory|
| ------- | ------- | ------- | ------- |
| uri | Unique ID of the shared configuration, fixed at the format of **"datashareproxy://{*bundleName*}/{*path*}"**, in which **bundleName** indicates the bundle name of the publisher application, and **path** can be set to any value but must be unique in the same application. The maximum length is 256 bytes.| String| Yes|
| value | Value of the shared configuration.<br/>Before API version 26.0.0, the maximum length is 4,096 bytes.<br/>Starting from API version 26.0.0, the maximum length is 102,400 bytes. When the value length of a shared configuration exceeds 4,096 bytes, you need to set the **maxValueLength** field to [MAX_LENGTH_100K](../reference/apis-arkdata/js-apis-data-dataShare.md#dataproxymaxvaluelength) in the [DataProxyConfig](../reference/apis-arkdata/js-apis-data-dataShare.md#dataproxyconfig20) parameter of [DataProxyHandle](../reference/apis-arkdata/js-apis-data-dataShare.md#dataproxyhandle20) APIs to extend the length limit to 102,400 bytes. Otherwise, the API results may be unexpected. | String | Yes |
| allowList | List of applications allowed to access the shared configuration item. The array can contain up to 256 elements. Any additional elements are ignored.<br/>Before API version 26.0.0, each element in the array is the [appIdentifier](../quick-start/common-problem-of-application.md#what-is-appidentifier) of an application, which is a numeric string with a maximum length of 128 bytes. Any **appIdentifier** that exceeds 128 bytes is ignored. You can use the [getBundleInfoForSelf](../reference/apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) API to obtain the **appIdentifier** of the current application.<br/>Starting from API version 26.0.0, the array also supports the special string **"all"** (case-sensitive), which allows all applications to access the shared configuration item. | String array | Yes |

```json5
{
    "crossAppSharedConfig": [
        {
            "uri": "datashareproxy://com.example.example/key1",
            "value": "SHARED_CONFIG_DEMO1",
            "allowList": ["6917573629901742292"]
        },
        {
            "uri": "datashareproxy://com.example.example/key2",
            "value": "SHARED_CONFIG_DEMO2",
            "allowList": ["6917573298752100864", "6917573298752100864"]
        },
        {
            "uri": "datashareproxy://com.example.example/key3",
            "value": "ALLOW ALL APP READ",
            "allowList": ["all"]
        }
    ]
}
```

### Static Configuration

Static configuration refers to the default shared configuration items provided during application installation. These predefined configuration items can take effect regardless of whether the application is started.

### Dynamic Configuration

You can call the **publish** or **delete** API to manage configuration items as follows: 

- Call the **publish** API to publish or modify configuration items.

  <!-- @[publish_shared_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/DataShare/ShareConfig/entry/src/main/ets/pages/Index.ets) -->

  ``` TypeScript
  function publishSharedConfig() {
    dataShare.createDataProxyHandle().then((dataProxyHandle) => {
      const newConfigData: dataShare.ProxyData[] = [
        {
          uri: 'datashareproxy://com.samples.shareconfig/config1',
          value: 'Value1',
          allowList: [
            'appIdentifier1',
            'appIdentifier2'
          ]
        },
        {
          uri: 'datashareproxy://com.samples.shareconfig/config2',
          value: 'Value2',
          allowList: [
            'appIdentifier3',
            'appIdentifier4'
          ]
        }
      ];
      const config: dataShare.DataProxyConfig = {
        type: dataShare.DataProxyType.SHARED_CONFIG,
      };
      dataProxyHandle.publish(newConfigData, config).then((results: dataShare.DataProxyResult[]) => {
        results.forEach((result) => {
          console.info(`URI: ${result.uri}, Result: ${result.result}`);
        });
      }).catch((error: BusinessError) => {
        console.error('Error publishing config:', error);
      });
    }).catch((error: BusinessError) => {
      console.error('Error creating DataProxyHandle:', error);
    });
  }
  ```

- Call the **delete** API to delete the configuration items.

  <!-- @[delete_shared_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/DataShare/ShareConfig/entry/src/main/ets/pages/Index.ets) -->

  ``` TypeScript
  function deleteSharedConfig() {
    dataShare.createDataProxyHandle().then((dataProxyHandle) => {
      const urisToDelete: string[] = [
        'datashareproxy://com.samples.shareconfig/config1',
        'datashareproxy://com.samples.shareconfig/config2'
      ];
      const config: dataShare.DataProxyConfig = {
        type: dataShare.DataProxyType.SHARED_CONFIG,
      };
      dataProxyHandle.delete(urisToDelete, config).then((results: dataShare.DataProxyResult[]) => {
        results.forEach((result) => {
          console.info(`URI: ${result.uri}, Result: ${result.result}`);
        });
      }).catch((error: BusinessError) => {
        console.error('Error deleting config:', error);
      });
    }).catch((error: BusinessError) => {
      console.error('Error creating DataProxyHandle:', error);
    });
  }
  ```

## Configuring the Accessor

You can call the **get**, **on**, or **off** API to perform operations as follows:

### Obtaining Configuration Items

Call the **get** API to obtain the configuration information.

<!-- @[get_shared_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/DataShare/ShareConfig/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function getSharedConfig() {
  dataShare.createDataProxyHandle().then((dataProxyHandle) => {
    const urisToGet: string[] = [
      'datashareproxy://com.samples.shareconfig/config1',
      'datashareproxy://com.samples.shareconfig/config2'
    ];
    const config: dataShare.DataProxyConfig = {
      type: dataShare.DataProxyType.SHARED_CONFIG,
    };
    dataProxyHandle.get(urisToGet, config).then((results: dataShare.DataProxyGetResult[]) => {
      results.forEach((result) => {
        console.info(`URI: ${result.uri}, Result: ${result.result}, AllowList: ${result.allowList}`);
      });
    }).catch((error: BusinessError) => {
      console.error('Error getting config:', error);
    });
  }).catch((error: BusinessError) => {
    console.error('Error creating DataProxyHandle:', error);
  });
}

```

### Subscribing to/Unsubscribing from Configuration Changes

Call the **on** API to subscribe to configuration changes or the **off** API to unsubscribe from the configuration changes.

<!-- @[watch_shared_config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/DataShare/ShareConfig/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
function watchConfigChanges() {
  dataShare.createDataProxyHandle().then((dsProxyHelper) => {
    const uris: string[] = [
      'datashareproxy://com.samples.shareconfig/config1',
      'datashareproxy://com.samples.shareconfig/config2'
    ];
    const config: dataShare.DataProxyConfig = {
      type: dataShare.DataProxyType.SHARED_CONFIG,
    };
    const callback = (err: BusinessError<void>, changes: dataShare.DataProxyChangeInfo[]): void => {
      if (err) {
        console.error('err:', err);
      } else {
        changes.forEach((change) => {
          console.info(`Change Type: ${change.type}, URI: ${change.uri}, Value: ${change.value}`);
        });
      }
    };
    // Subscribe to configuration changes.
    const listenResults: dataShare.DataProxyResult[] = dsProxyHelper.on('dataChange', uris, config, callback);
    listenResults.forEach((result) => {
      console.info(`URI: ${result.uri}, Result: ${result.result}`);
    });
    // Unsubscribe from configuration changes.
    const unListenResults: dataShare.DataProxyResult[] = dsProxyHelper.off('dataChange', uris, config, callback);
    unListenResults.forEach((result) => {
      console.info(`URI: ${result.uri}, Result: ${result.result}`);
    });
  }).catch((error: BusinessError) => {
    console.error('Error creating DataProxyHandle:', error);
  });
}

```

<!--no_check-->