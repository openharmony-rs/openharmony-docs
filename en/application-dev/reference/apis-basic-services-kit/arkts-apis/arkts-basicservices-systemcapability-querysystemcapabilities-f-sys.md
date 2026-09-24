# querySystemCapabilities (System API)

## Modules to Import

```TypeScript
import { systemCapability } from '@kit.BasicServicesKit';
```

## querySystemCapabilities

```TypeScript
function querySystemCapabilities(callback: AsyncCallback<string>): void
```

Get System Capability.

**Since:** 9

**System capability:** SystemCapability.Developtools.Syscap

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | indicates the system capability string result. |

**Examples**

```TypeScript
try {
    systemCapability.querySystemCapabilities((err:Error, data:string) => {
    if (err == undefined) {
        console.info("get system capabilities:" + data);
    } else {
        console.error(" get system capabilities err:" + err);
    }});
}catch(e){
    console.error("get unexpected error: " + e);
}
```


<a id="querysystemcapabilities-1"></a>

## querySystemCapabilities

```TypeScript
function querySystemCapabilities(): Promise<string>
```

Get System Capability.

**Since:** 9

**System capability:** SystemCapability.Developtools.Syscap

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | system capability string. |

**Examples**

```TypeScript
try {
    systemCapability.querySystemCapabilities().then((value:string) => {
        console.info("get system capabilities: " + value);
    }).catch((err:Error) => {
        console.error("get system capabilities error: " + err);
    });
}catch(e){
    console.error("get unexpected error: " + e);
}
```
