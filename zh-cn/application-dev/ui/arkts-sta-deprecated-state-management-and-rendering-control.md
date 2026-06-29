# UI组件适配（状态管理与渲染控制）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## 状态管理

### Clear

ArkTS-Dyn接口声明：static [Clear](../reference/apis-arkui/arkui-ts/ts-state-management.md#clear10)(): boolean

替代的ArkTS-Sta接口声明：static [clear](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#clear)(): boolean

ArkTS-Dyn示例：

```ts
let res: boolean = AppStorage.Clear();
```

ArkTS-Sta示例：

```ts
let res: boolean = AppStorage.clear();
```

### Delete

ArkTS-Dyn接口声明：static [Delete](../reference/apis-arkui/arkui-ts/ts-state-management.md#delete10)(propName: string): boolean

替代的ArkTS-Sta接口声明：static [delete](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#delete)(propName: string): boolean

ArkTS-Dyn示例：

```ts
let res: boolean = AppStorage.Delete('PropA');
```

ArkTS-Sta示例：

```ts
let res: boolean = AppStorage.delete('PropA');
```

### Get

ArkTS-Dyn接口声明：static [Get](../reference/apis-arkui/arkui-ts/ts-state-management.md#get10)\<T\>(propName: string): T | undefined

替代的ArkTS-Sta接口声明：static [get](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#get)\<T\>(propName: string): T | undefined

ArkTS-Dyn示例：

```ts
let value: number = AppStorage.Get('PropA') as number;
```

ArkTS-Sta示例：

```ts
let value: number = AppStorage.get<number>('PropA') as number;
```

### Has

ArkTS-Dyn接口声明：static [Has](../reference/apis-arkui/arkui-ts/ts-state-management.md#has10)(propName: string): boolean

替代的ArkTS-Sta接口声明：static [has](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#has)(propName: string): boolean

ArkTS-Dyn示例：

```ts
AppStorage.Has('simpleProp');
```

ArkTS-Sta示例：

```ts
AppStorage.has('simpleProp');
```

### IsMutable

ArkTS-Dyn接口声明：static [IsMutable](../reference/apis-arkui/arkui-ts/ts-state-management.md#ismutabledeprecated)(propName: string): boolean，返回值恒为true。

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

ArkTS-Dyn接口声明：static [Keys](../reference/apis-arkui/arkui-ts/ts-state-management.md#keys10)(): IterableIterator\<string\>

替代的ArkTS-Sta接口声明：static [keys](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#keys)(): IterableIterator\<string\>

ArkTS-Dyn示例：

```ts
let keys: IterableIterator<string> = AppStorage.Keys();
```

ArkTS-Sta示例：

```ts
let keys: IterableIterator<string> = AppStorage.keys();
```

### Link

ArkTS-Dyn接口声明：static [Link](../reference/apis-arkui/arkui-ts/ts-state-management.md#link10)(propName: string): any

替代的ArkTS-Sta接口声明：static [link](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#link)\<T\>(propName: string): SubscribedAbstractProperty\<T\>

ArkTS-Dyn示例：

```ts
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.Link('PropA');
```

ArkTS-Sta示例：

```ts
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.link<number>('PropA');
```

### Prop

ArkTS-Dyn接口声明：static [Prop](../reference/apis-arkui/arkui-ts/ts-state-management.md#prop10)(propName: string): any

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用ref替代。

替代的ArkTS-Sta接口声明：static [ref](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#ref)\<T\>(propName: string): AbstractProperty\<T\> | undefined

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

ArkTS-Dyn接口声明：static [Set](../reference/apis-arkui/arkui-ts/ts-state-management.md#set10)\<T\>(propName: string, newValue: T): boolean

替代的ArkTS-Sta接口声明：static [set](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#set)\<T\>(propName: string, newValue: T): boolean

ArkTS-Dyn示例：

```ts
let res: boolean = AppStorage.Set('PropA', 47);
```

ArkTS-Sta示例：

```ts
let res: boolean = AppStorage.set<number>('PropA', 47);
```

### SetAndLink

ArkTS-Dyn接口声明：static [SetAndLink](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandlink10)\<T\>(propName: string, defaultValue: T): SubscribedAbstractProperty\<T\>

替代的ArkTS-Sta接口声明：static [setAndLink](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#setandlink)\<T\>(propName: string, defaultValue: T): SubscribedAbstractProperty\<T\>

ArkTS-Dyn示例：

```ts
let link: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropA', 49);
```

ArkTS-Sta示例：

```ts
let link: SubscribedAbstractProperty<number> = AppStorage.setAndLink<number>('PropA', 49);
```

### SetAndProp

ArkTS-Dyn接口声明：static [SetAndProp](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandprop10)\<S\>(propName: string, defaultValue: S): SubscribedAbstractProperty\<S\>

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用setAndRef替代。

替代的ArkTS-Sta接口声明：static [setAndRef](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#setandref)\<T\>(propName: string, defaultValue: T): AbstractProperty\<T\>

ArkTS-Dyn示例：

```ts
let prop: SubscribedAbstractProperty<number> = AppStorage.SetAndProp('PropA', 49);
```

ArkTS-Sta示例：

```ts
let ref: AbstractProperty<number> = AppStorage.setAndRef<number>('PropA', 49);
```

### SetOrCreate

ArkTS-Dyn接口声明：static [SetOrCreate](../reference/apis-arkui/arkui-ts/ts-state-management.md#setorcreate10)\<T\>(propName: string, newValue: T): void

替代的ArkTS-Sta接口声明：static [setOrCreate](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#setorcreate)\<T\>(propName: string, newValue: T): void

ArkTS-Dyn示例：

```ts
AppStorage.SetOrCreate('simpleProp', 121);
```

ArkTS-Sta示例：

```ts
AppStorage.setOrCreate<number>('simpleProp', 121);
```

### Size

ArkTS-Dyn接口声明：static [Size](../reference/apis-arkui/arkui-ts/ts-state-management.md#size10)(): number

替代的ArkTS-Sta接口声明：static [size](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#size)(): number

ArkTS-Dyn示例：

```ts
let res: number = AppStorage.Size();
```

ArkTS-Sta示例：

```ts
let res: number = AppStorage.size();
```

### prop

ArkTS-Dyn接口声明: static [prop](../reference/apis-arkui/arkui-ts/ts-state-management.md#prop10)\<T\>(propName: string): SubscribedAbstractProperty\<T\>

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用ref替代。

替代的ArkTS-Sta接口声明：static [ref](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#ref)\<T\>(propName: string): AbstractProperty\<T\>

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

ArkTS-Dyn接口声明：static [setAndProp](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandprop10)\<T\>(propName: string, defaultValue: T): SubscribedAbstractProperty\<T\>

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用setAndRef替代。

替代的ArkTS-Sta接口声明：static [setAndRef](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#setandref)\<T\>(propName: string, defaultValue: T): AbstractProperty\<T\>

ArkTS-Dyn示例：

```ts
let prop: SubscribedAbstractProperty<number> = AppStorage.setAndProp('PropA', 49);
```

ArkTS-Sta示例：

```ts
let ref: AbstractProperty<number> = AppStorage.setAndRef<number>('PropA', 49);
```

### staticClear

ArkTS-Dyn接口声明：static [staticClear](../reference/apis-arkui/arkui-ts/ts-state-management.md#staticcleardeprecated)(): boolean

替代的ArkTS-Sta接口声明：static [clear](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#clear)(): boolean

ArkTS-Dyn示例：

```ts
let res = AppStorage.staticClear();
```

ArkTS-Sta示例：

```ts
let res = AppStorage.clear();
```

### EnvProp

ArkTS-Dyn接口声明：static [EnvProp](../reference/apis-arkui/arkui-ts/ts-state-management.md#envprop10)\<S\>(key: string, value: S): boolean

替代的ArkTS-Sta接口声明：static [envProp](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#envprop)\<T\>(key: string, value: T): boolean

ArkTS-Dyn示例：

```ts
Environment.EnvProp<string>('accessibilityEnabled', 'default');
```

ArkTS-Sta示例：

```ts
Environment.envProp<string>('accessibilityEnabled', 'default');
```

### EnvProps

ArkTS-Dyn接口声明：static [EnvProps](../reference/apis-arkui/arkui-ts/ts-state-management.md#envprops10)(props: {key: string; defaultValue: any; }[]): void

替代的ArkTS-Sta接口声明：static [envProps](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#envprops)(props: EnvPropsOptions[]): void

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

ArkTS-Dyn接口声明：static [Keys](../reference/apis-arkui/arkui-ts/ts-state-management.md#keys10-2)(): Array\<string\>

替代的ArkTS-Sta接口声明：static [keys](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#keys)(): Array\<string\>

ArkTS-Dyn示例：

```ts
let keys: Array<string> = Environment.Keys();
```

ArkTS-Sta示例：

```ts
let keys: Array<string> = Environment.keys();
```

### GetShared

ArkTS-Dyn接口声明：static GetShared(): LocalStorage

ArkTS-Sta中，可以通过使用UIContext中的getSharedLocalStorage来获取当前stage共享的LocalStorage实例。

替代的ArkTS-Sta接口声明：getSharedLocalStorage(): LocalStorage | undefined

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

ArkTS-Dyn接口声明：static getShared(): LocalStorage

ArkTS-Sta中，可以通过使用UIContext中的getSharedLocalStorage来获取当前stage共享的LocalStorage实例。

替代的ArkTS-Sta接口声明：getSharedLocalStorage(): LocalStorage | undefined

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

ArkTS-Dyn接口声明: static [prop](../reference/apis-arkui/arkui-ts/ts-state-management.md#prop9)\<S\>(propName: string): SubscribedAbstractProperty\<S\>

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用ref替代。

替代的ArkTS-Sta接口声明：static [ref](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#ref)\<T\>(propName: string): AbstractProperty\<T\>

ArkTS-Dyn示例：

```ts
let storage: LocalStorage = new LocalStorage();
let prop: SubscribedAbstractProperty<number> = storage.prop('PropA');
prop.set(48);
```

ArkTS-Sta示例：

```ts
let storage: LocalStorage = new LocalStorage();
let ref: AbstractProperty<number> | undefined = storage.ref<number>('PropA');
ref?.set(48);
```

### setAndProp

ArkTS-Dyn接口声明：static [setAndProp](../reference/apis-arkui/arkui-ts/ts-state-management.md#setandprop9)\<S\>(propName: string, defaultValue: S): SubscribedAbstractProperty\<S\>

ArkTS-Sta未默认提供类的深拷贝能力，在无需使用深拷贝的场景，可以使用setAndRef替代。

替代的ArkTS-Sta接口声明：static [setAndRef](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#setandref)\<T\>(propName: string, defaultValue: T): AbstractProperty\<T\>

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

ArkTS-Dyn接口声明：static [DeleteProp](../reference/apis-arkui/arkui-ts/ts-state-management.md#deleteprop10)(key: string): void

替代的ArkTS-Sta接口声明：static [deleteProp](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#deleteprop)(key: string): void

ArkTS-Dyn示例：

```ts
PersistentStorage.DeleteProp('highScore');
```

ArkTS-Sta示例：

```ts
PersistentStorage.deleteProp('highScore');
```

### Keys

ArkTS-Dyn接口声明：static [Keys](../reference/apis-arkui/arkui-ts/ts-state-management.md#keys10-1)(): Array\<string\>

替代的ArkTS-Sta接口声明：static [keys](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#keys-1)(): Array\<string\>

ArkTS-Dyn示例：

```ts
let keys: Array<string> = PersistentStorage.Keys();
```

ArkTS-Sta示例：

```ts
let keys: Array<string> = PersistentStorage.keys();
```

### PersistProp

ArkTS-Dyn接口声明：static [PersistProp](../reference/apis-arkui/arkui-ts/ts-state-management.md#persistprop10)\<T\>(key: string, defaultValue: T): void

替代的ArkTS-Sta接口声明：static [persistProp](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#persistprop)\<T\>(key: string, defaultValue: T): void

ArkTS-Dyn示例：

```ts
PersistentStorage.PersistProp<string>('highScore', '0');
```

ArkTS-Sta示例：

```ts
PersistentStorage.persistProp<string>('highScore', '0');
```

### PersistProps

ArkTS-Dyn接口声明：static [PersistProps](../reference/apis-arkui/arkui-ts/ts-state-management.md#persistprops10)(properties: {key: string; defaultValue: any;}[])

替代的ArkTS-Sta接口声明：static [persistProp](../reference/apis-arkui/arkui-ts/ts-state-management-Static.md#persistprop)\<T\>(key: string, defaultValue: T): void

ArkTS-Dyn示例：

```ts
PersistentStorage.PersistProps([
    { key: 'highScore', defaultValue: '0' },
    { key: 'weightScore', defaultValue: '1' }
]);
```

ArkTS-Sta示例：

```ts
PersistentStorage.persistProp<string>('highScore', '0');
PersistentStorage.persistProp<string>('weightScore', '1');
```

## 渲染控制

### onDataAdded

ArkTS-Dyn接口声明：[onDataAdded](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondataaddeddeprecated)(index: number): void

替代的ArkTS-Sta接口声明：[onDataAdd](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondataadd8)(index: number): void

ArkTS-Dyn示例：

```ts
onDataAdded(0)
```

ArkTS-Sta示例：

```ts
onDataAdd(0)
```

### onDataMoved

ArkTS-Dyn接口声明：[onDataMoved](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatamoveddeprecated)(from: number, to: number): void

替代的ArkTS-Sta接口声明：[onDataMove](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatamove8)(from: number, to: number): void

ArkTS-Dyn示例：

```ts
onDataMoved(0, 1)
```

ArkTS-Sta示例：

```ts
onDataMove(0, 1)
```

### onDataDeleted

ArkTS-Dyn接口声明：[onDataDeleted](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatadeleteddeprecated)(index: number): void

替代的ArkTS-Sta接口声明：[onDataDelete](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatadelete8)(index: number): void

ArkTS-Dyn示例：

```ts
onDataDeleted(0)
```

ArkTS-Sta示例：

```ts
onDataDelete(0)
```

### onDataChanged

ArkTS-Dyn接口声明：[onDataChanged](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatachangeddeprecated)(index: number): void

替代的ArkTS-Sta接口声明：[onDataChange](../reference/apis-arkui/arkui-ts/ts-rendering-control-lazyforeach.md#ondatachange8)(index: number): void

ArkTS-Dyn示例：

```ts
onDataChanged(0)
```

ArkTS-Sta示例：

```ts
onDataChange(0)
```