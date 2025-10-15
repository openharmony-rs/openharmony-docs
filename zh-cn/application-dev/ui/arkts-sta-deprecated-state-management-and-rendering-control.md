# UI组件适配（状态管理与渲染控制）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## 状态管理

### Clear

ArkTS-Dyn接口声明：[static Clear(): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#cleardeprecated)

替代的ArkTS-Sta接口声明：[static clear(): boolean](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#clear)



ArkTS-Dyn示例：

```
let res: boolean = AppStorage.Clear();
```

ArkTS-Sta示例：

```
let res: boolean = AppStorage.clear();
```

### Delete

ArkTS-Dyn接口声明：[static Delete(propName: string): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#deletedeprecated)

替代的ArkTS-Sta接口声明：[static delete(propName: string): boolean](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#delete)



ArkTS-Dyn示例：

```
let res: boolean = AppStorage.Delete('PropA');
```

ArkTS-Sta示例：

```
let res: boolean = AppStorage.delete('PropA');
```

### Get

ArkTS-Dyn接口声明：[static Get\<T\>(propName: string): T | undefined](../reference/apis-arkui/arkui-ts/ts-state-management.md#getdeprecated)

替代的ArkTS-Sta接口声明：[static get\<T\>(propName: string): T | undefined](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#get)



ArkTS-Dyn示例：

```ts
let value: number = AppStorage.Get('PropA') as number;
```

ArkTS-Sta示例：

```ts
let value: number = AppStorage.get<number>('PropA') as number;
```

### Has

ArkTS-Dyn接口声明：[static Has(propName: string): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#hasdeprecated)

替代的ArkTS-Sta接口声明：[static has(propName: string): boolean](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#has)



ArkTS-Dyn示例：

```ts
AppStorage.Has('simpleProp');
```

ArkTS-Sta示例：

```ts
AppStorage.has('simpleProp');
```

### IsMutable

ArkTS-Dyn接口声明：[static IsMutable(propName: string): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#ismutabledeprecated)，返回值恒为true。

ArkTS-Sta未提供该接口。



ArkTS-Dyn示例：

```ts
let mutable: boolean = AppStorage.IsMutable('simpleProp'); // 返回值恒为true
```

ArkTS-Sta示例：

```ts
let mutable: boolean = true;
```

### Keys

ArkTS-Dyn接口声明：[static Keys(): IterableIterator\<string\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#keysdeprecated)

替代的ArkTS-Sta接口声明：[static keys(): IterableIterator\<string\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#keys)



ArkTS-Dyn示例：

```ts
let keys: IterableIterator<string> = AppStorage.Keys();
```

ArkTS-Sta示例：

```ts
let keys: IterableIterator<string> = AppStorage.keys();
```

### Link

ArkTS-Dyn接口声明：[static Link(propName: string): any](../reference/apis-arkui/arkui-ts/ts-state-management.md#linkdeprecated)

替代的ArkTS-Sta接口声明：[static link\<T\>(propName: string): SubscribedAbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#link)



ArkTS-Dyn示例：

```ts
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.Link('PropA');
```

ArkTS-Sta示例：

```ts
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.link<number>('PropA');
```

### Prop

ArkTS-Dyn接口声明：[static Prop(propName: string): any](../reference/apis-arkui/arkui-ts/ts-state-management.md#propdeprecated)

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用ref替代。

替代的ArkTS-Sta接口声明：[static ref\<T\>(propName: string): AbstractProperty\<T\> | undefined](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#ref)



ArkTS-Dyn示例：

```ts
let prop: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
prop.set(48);
```

ArkTS-Sta示例：

```ts
let ref: AbstractProperty<number> | undefined = AppStorage.ref<number>('PropA');
ref?.set(48);
```

### Set

ArkTS-Dyn接口声明：[static Set\<T\>(propName: string, newValue: T): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#setdeprecated)

替代的ArkTS-Sta接口声明：[static set\<T\>(propName: string, newValue: T): boolean](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#set)



ArkTS-Dyn示例：

```ts
let res: boolean = AppStorage.Set('PropA', 47);
```

ArkTS-Sta示例：

```ts
let res: boolean = AppStorage.set<number>('PropA', 47);
```

### SetAndLink

ArkTS-Dyn接口声明：[static SetAndLink\<T\>(propName: string, defaultValue: T): SubscribedAbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandlinkdeprecated)

替代的ArkTS-Sta接口声明：[static setAndLink\<T\>(propName: string, defaultValue: T): SubscribedAbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#setandlink)



ArkTS-Dyn示例：

```ts
let link: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropA', 49);
```

ArkTS-Sta示例：

```ts
let link: SubscribedAbstractProperty<number> = AppStorage.setAndLink<number>('PropA', 49);
```

### SetAndProp

ArkTS-Dyn接口声明：[static SetAndProp\<S\>(propName: string, defaultValue: S): SubscribedAbstractProperty\<S\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandpropdeprecated)

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用setAndRef替代。

替代的ArkTS-Sta接口声明：[static setAndRef\<T\>(propName: string, defaultValue: T): AbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#setandref)



ArkTS-Dyn示例：

```ts
let prop: SubscribedAbstractProperty<number> = AppStorage.SetAndProp('PropA', 49);
```

ArkTS-Sta示例：

```ts
let ref: AbstractProperty<number> = AppStorage.setAndRef<number>('PropA', 49);
```

### SetOrCreate

ArkTS-Dyn接口声明：[static SetOrCreate\<T\>(propName: string, newValue: T): void](../reference/apis-arkui/arkui-ts/ts-state-management.md#setorcreatedeprecated)

替代的ArkTS-Sta接口声明：[static setOrCreate\<T\>(propName: string, newValue: T): void](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#setorcreate)



ArkTS-Dyn示例：

```ts
AppStorage.SetOrCreate('simpleProp', 121);
```

ArkTS-Sta示例：

```ts
AppStorage.setOrCreate<number>('simpleProp', 121);
```

### Size

ArkTS-Dyn接口声明：[static Size(): number](../reference/apis-arkui/arkui-ts/ts-state-management.md#sizedeprecated)

替代的ArkTS-Sta接口声明：[static size(): number](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#size)



ArkTS-Dyn示例：

```ts
let res: number = AppStorage.Size();
```

ArkTS-Sta示例：

```ts
let res: number = AppStorage.size();
```

### prop

ArkTS-Dyn接口声明: [static prop\<T\>(propName: string): SubscribedAbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#prop10)

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用ref替代。

替代的ArkTS-Sta接口声明：[static ref\<T\>(propName: string): AbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#ref)

ArkTS-Dyn示例：

```ts
let prop: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop.set(48);
```

ArkTS-Sta示例：

```ts
let ref: AbstractProperty<number> | undefined = AppStorage.ref<number>('PropA');
ref?.set(48);
```

### setAndProp

ArkTS-Dyn接口声明：[static setAndProp\<T\>(propName: string, defaultValue: T): SubscribedAbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandprop10)

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用setAndRef替代。

替代的ArkTS-Sta接口声明：[static setAndRef\<T\>(propName: string, defaultValue: T): AbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#setandref)

ArkTS-Dyn示例：

```ts
let prop: SubscribedAbstractProperty<number> = AppStorage.setAndProp('PropA', 49);
```

ArkTS-Sta示例：

```ts
let ref: AbstractProperty<number> = AppStorage.setAndRef<number>('PropA', 49);
```

### staticClear

ArkTS-Dyn接口声明：[static staticClear(): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#staticcleardeprecated)

替代的ArkTS-Sta接口声明：[static clear(): boolean](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#clear)



ArkTS-Dyn示例：

```ts
let res = AppStorage.staticClear();
```

ArkTS-Sta示例：

```ts
let res = AppStorage.clear();
```

### EnvProp

ArkTS-Dyn接口声明：[static EnvProp\<S\>(key: string, value: S): boolean](../reference/apis-arkui/arkui-ts/ts-state-management.md#envpropdeprecated)

替代的ArkTS-Sta接口声明：[static envProp\<T\>(key: string, value: T): boolean](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#envprop)



ArkTS-Dyn示例：

```ts
Environment.EnvProp<string>('accessibilityEnabled', 'default');
```

ArkTS-Sta示例：

```ts
Environment.envProp<string>('accessibilityEnabled', 'default');
```

### EnvProps

ArkTS-Dyn接口声明：[static EnvProps(props: {key: string; defaultValue: any; }[]): void](../reference/apis-arkui/arkui-ts/ts-state-management.md#envpropsdeprecated)

替代的ArkTS-Sta接口声明：[static envProps(props: EnvPropsOptions[]): void](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#envprops)



ArkTS-Dyn示例：

```ts
Environment.EnvProps([
    { key: 'accessibilityEnabled', defaultValue: 'default' },
    { key: 'languageCode', defaultValue: 'en' },
    { key: 'prop', defaultValue: 'hhhh' }
]);
```

ArkTS-Sta示例：

```ts
Environment.envProps([
    { key: 'accessibilityEnabled', defaultValue: 'default' },
    { key: 'languageCode', defaultValue: 'en' },
    { key: 'prop', defaultValue: 'hhhh' }
]);
```

### Keys

ArkTS-Dyn接口声明：[static Keys(): Array\<string\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#keysdeprecated-2)

替代的ArkTS-Sta接口声明：[static keys(): Array\<string\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#keys)

ArkTS-Dyn示例：

```ts
let keys: Array<string> = Environment.Keys();
```

ArkTS-Sta示例：

```ts
let keys: Array<string> = Environment.keys();
```

### GetShared

ArkTS-Dyn接口声明：[static GetShared(): LocalStorage](../reference/apis-arkui/arkui-ts/ts-state-management.md#getshareddeprecated-1)

ArkTS-Sta中，可以通过使用UIContext中的getSharedLocalStorage来获取当前stage共享的LocalStorage实例。

替代的ArkTS-Sta接口声明：[getSharedLocalStorage(): LocalStorage | undefined](../reference/apis-arkui/js-apis-arkui-UIContext.md#getsharedlocalstorage12)



ArkTS-Dyn示例：

```ts
let storage: LocalStorage = LocalStorage.GetShared();
```

ArkTS-Sta示例：

```ts
struct SharedLocalStorage {
    localStorage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
}
```

### getShared

ArkTS-Dyn接口声明：[static getShared(): LocalStorage](../reference/apis-arkui/arkui-ts/ts-state-management.md#getshareddeprecated)

ArkTS-Sta中，可以通过使用UIContext中的getSharedLocalStorage来获取当前stage共享的LocalStorage实例。

替代的ArkTS-Sta接口声明：[getSharedLocalStorage(): LocalStorage | undefined](../reference/apis-arkui/js-apis-arkui-UIContext.md#getsharedlocalstorage12)



ArkTS-Dyn示例：

```ts
let storage: LocalStorage = LocalStorage.getShared();
```

ArkTS-Sta示例：

```ts
struct SharedLocalStorage {
    localStorage: LocalStorage | undefined = this.getUIContext().getSharedLocalStorage();
}
```

### prop

ArkTS-Dyn接口声明: [static prop\<S\>(propName: string): SubscribedAbstractProperty\<S\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#prop9)

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用ref替代。

替代的ArkTS-Sta接口声明：[static ref\<T\>(propName: string): AbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#ref)

ArkTS-Dyn示例：

```ts
let stoarge: LocalStorage = new LocalStorage();
let prop: SubscribedAbstractProperty<number> = storage.prop('PropA');
prop.set(48);
```

ArkTS-Sta示例：

```ts
let stoarge: LocalStorage = new LocalStorage();
let ref: AbstractProperty<number> | undefined = storage.ref<number>('PropA');
ref?.set(48);
```

### setAndProp

ArkTS-Dyn接口声明：[static setAndProp\<S\>(propName: string, defaultValue: S): SubscribedAbstractProperty\<S\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandprop9)

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用setAndRef替代。

替代的ArkTS-Sta接口声明：[static setAndRef\<T\>(propName: string, defaultValue: T): AbstractProperty\<T\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#setandref)

ArkTS-Dyn示例：

```ts
let storage: LocalStorage = new LocalStorage();
let prop: SubscribedAbstractProperty<number> = storage.setAndProp('PropA', 49);
```

ArkTS-Sta示例：

```ts
let storage: LocalStorage = new LocalStorage();
let ref: AbstractProperty<number> = storage.setAndRef<number>('PropA', 49);
```

### DeleteProp

ArkTS-Dyn接口声明：[static DeleteProp(key: string): void](../reference/apis-arkui/arkui-ts/ts-state-management.md#deletepropdeprecated)

替代的ArkTS-Sta接口声明：[static deleteProp(key: string): void](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#deleteprop)



ArkTS-Dyn示例：

```ts
PersistentStorage.DeleteProp('highScore');
```

ArkTS-Sta示例：

```ts
PersistentStorage.deleteProp('highScore');
```

### Keys

ArkTS-Dyn接口声明：[static Keys(): Array\<string\>](../reference/apis-arkui/arkui-ts/ts-state-management.md#keysdeprecated-1)

替代的ArkTS-Sta接口声明：[static keys(): Array\<string\>](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#keys)



ArkTS-Dyn示例：

```ts
let keys: Array<string> = PersistentStorage.Keys();
```

ArkTS-Sta示例：

```ts
let keys: Array<string> = PersistentStorage.keys();
```

### PersistProp

ArkTS-Dyn接口声明：[static PersistProp\<T\>(key: string, defaultValue: T): void](../reference/apis-arkui/arkui-ts/ts-state-management.md#persistpropdeprecated)

替代的ArkTS-Sta接口声明：[static persistProp\<T\>(key: string, defaultValue: T): void](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#persistprop)



ArkTS-Dyn示例：

```ts
PersistentStorage.PersistProp<string>('highScore', '0');
```

ArkTS-Sta示例：

```ts
PersistentStorage.persistProp<string>('highScore', '0');
```

### PersistProps

ArkTS-Dyn接口声明：[static PersistProps(properties: {key: string; defaultValue: any;}[])](../reference/apis-arkui/arkui-ts/ts-state-management.md#persistpropsdeprecated)

替代的ArkTS-Sta接口声明：[static persistProp\<T\>(key: string, defaultValue: T): void](../reference/apis-arkui/arkui-ts/ts-state-management-1.2.md#persistprop)



ArkTS-Dyn示例：

```ts
PersistentStorage.PersistProps([
    { key: 'highScore', defaultValue: '0' },
    { key: 'wightScore', defaultValue: '1' }
]);
```

ArkTS-Sta示例：

```ts
PersistentStorage.persistProp<string>('highScore', '0');
PersistentStorage.persistProp<string>('wightScore', '1');
```

## 渲染控制

### onDataAdded

ArkTS-Dyn接口声明：[onDataAdded(index: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondataaddeddeprecated)

替代的ArkTS-Sta接口声明：[onDataAdd(index: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondataadd8)



ArkTS-Dyn示例：

```ts
onDataAdded(0)
```

ArkTS-Sta示例：

```ts
onDataAdd(0)
```

### onDataMoved

ArkTS-Dyn接口声明：[onDataMoved(from: number, to: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatamoveddeprecated)

替代的ArkTS-Sta接口声明：[onDataMove(from: number, to: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatamove8)



ArkTS-Dyn示例：

```ts
onDataMoved(0, 1)
```

ArkTS-Sta示例：

```ts
onDataMove(0, 1)
```

### onDataDeleted

ArkTS-Dyn接口声明：[onDataDeleted(index: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatadeleteddeprecated)

替代的ArkTS-Sta接口声明：[onDataDelete(index: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatadelete8)



ArkTS-Dyn示例：

```ts
onDataDeleted(0)
```

ArkTS-Sta示例：

```ts
onDataDelete(0)
```

### onDataChanged

ArkTS-Dyn接口声明：[onDataChanged(index: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatachangeddeprecated)

替代的ArkTS-Sta接口声明：[onDataChange(index: number): void](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatachange8)



ArkTS-Dyn示例：

```ts
onDataChanged(0)
```

ArkTS-Sta示例：

```ts
onDataChange(0)
```