# IMonitor

```TypeScript
declare interface IMonitor
```

When the monitored state variable changes, the state management framework will call the registered function and pass the change information of the **IMonitor** type.

**Since:** 12

<!--Device-unnamed-declare interface IMonitor--><!--Device-unnamed-declare interface IMonitor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value<T>(path?: string): IMonitorValue<T> | undefined
```

Obtains the change information for the specified path.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-IMonitor-value<T>(path?: string): IMonitorValue<T> | undefined--><!--Device-IMonitor-value<T>(path?: string): IMonitorValue<T> | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | No | Path name of the monitored state variable. If it is not specified, the first path in the **dirty** array is used by default. Since API version 26.0.0, the first non-wildcard path in **dirty** is used by default. If the specified path is a wildcard path, **undefined** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [IMonitorValue](arkts-arkui-common-comp-imonitorvalue-i.md)&lt;T&gt; &#124; undefined | Path and change information for the variable monitored by **\@Monitor**.<br>**T** is the type of the monitored state variable. <br>If the monitored path does not exist, **undefined** is returned. <br>Prior to API version 26.0.0, if no path is specified, this parameter returns information corresponding to the first path in the **dirty** array of changed paths by default. <br>Since API version 26.0.0, if no path is specified, this parameter returns the first non-wildcard path in the **dirty** array of changed paths by default. <br>If the specified path is a wildcard path, **undefined** is returned. <br>If no path is specified and all paths in the **dirty** array are wildcard paths, **undefined** is returned. |

**Examples**

```TypeScript
@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 25;
  @Trace height: number = 175;

  // Listen for one variable.
  @Monitor('name')
  onNameChange(monitor: IMonitor) {
    // If no path is specified for value, the first path in the dirty array is used by default.
    console.info(`path: ${monitor.value()?.path} change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  // Listen for multiple state variables.
  @Monitor('age', 'height')
  onRecordChange(monitor: IMonitor) {
    // If a path is specified for value, the change information for the specified path is returned.
    monitor.dirty.forEach((path: string) => {
      console.info(`path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    });
  }
}

@Entry
@ComponentV2
struct Index {
  @Local info: Info = new Info();

  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick(() => {
          this.info.name = 'Bob'; // Output log: path: name change from Tom to Bob
        })
      Text(`info.age: ${this.info.age}, info.height: ${this.info.height}`)
        .onClick(() => {
          this.info.age++; // Output log: path: age change from 25 to 26
          this.info.height++; // Output log: path: height change from 175 to 176.
        })
    }
  }
}
```

## dirty

```TypeScript
dirty: Array<string>
```

Array of paths where properties have changed in the monitored state variable. The path format is the same as that of the variable name path specified by **\@Monitor**. Nested property paths separated by periods (.) are supported, for example, **'a.b.c'**. Since API version 26.0.0, when the wildcard capability is enabled, this array may contain wildcard paths, and querying wildcard paths through [value](#value)() will return **undefined**.

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-IMonitor-dirty: Array<string>--><!--Device-IMonitor-dirty: Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
