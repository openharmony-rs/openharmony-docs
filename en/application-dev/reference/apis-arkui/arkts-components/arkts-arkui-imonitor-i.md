# IMonitor

Define IMonitor interface

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value<T>(path?: string): IMonitorValue<T> | undefined
```

Return the pair of the value before the most recent change and current value for given path. If path does not exist, return undefined; If path is not specified, return the value pair corresponding to the first path in dirty.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| [IMonitorValue](arkts-arkui-imonitorvalue-i.md)&lt;T&gt; &#124; undefined |  |

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

Array of changed paths(keys)

**Type:** Array&lt;string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
