# Migration for Component State Variables
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @HelloCrease-->

This topic provides migration guidance for component state variables across different scenarios.
| V1 Decorator               | V2 Decorator                 |
|------------------------|--------------------------|
| [\@State](./arkts-state.md)                 | No external initialization: [\@Local](./arkts-new-local.md)<br>One-time external initialization: [\@Param](./arkts-new-param.md) + [\@Once](./arkts-new-once.md)|
| [\@Prop](./arkts-prop.md)                   | [\@Param](./arkts-new-param.md)                   |
| [\@Link](./arkts-link.md)                  | [\@Param](./arkts-new-param.md)[\@Event](./arkts-new-event.md)    |
|  [\@ObjectLink](./arkts-observed-and-objectlink.md)           |[\@Param](./arkts-new-param.md)[\@Event](./arkts-new-event.md)                   |
|  [\@Provide](./arkts-provide-and-consume.md)               |[\@Provider](./arkts-new-provider-and-consumer.md)                | 
| [\@Consume](./arkts-provide-and-consume.md)               |[\@Consumer](./arkts-new-provider-and-consumer.md)                |
| [\@Watch](./arkts-watch.md)               |[\@Monitor](./arkts-new-monitor.md)                |
| No computed property capability (manual recalculation required)| [\@Computed](./arkts-new-computed.md)                |

## Migration Examples

### \@State->\@Local

**Migration Rules**

In V1, \@State decorates internal component state variables. V2 provides \@Local as its replacement, but with significant differences in observation capabilities and initialization rules. The migration strategies for different use scenarios are as follows:

- Primitive types: For primitive type variables, directly replace \@State with \@Local.
- Complex types: In V1, @State can observe the top-level property changes of a complex object. In V2, \@Local can observe only the changes of the object itself. To listen for the internal property changes of an object, you can use \@ObservedV2 and \@Trace together.
- External initialization: \@State in V1 supports initialization from external values, while \@Local in V2 prohibits external initialization. If an initial value needs to be passed in externally, you can use the \@Param and \@Once decorators.

**Example**

**Primitive Types**

For primitive type variables, \@State in V1 can be replaced with \@Local in V2.

V1:

```ts
@Entry
@Component
struct Child {
  @State val: number = 10;

  build() {
    Text(this.val.toString())
  }
}
```

V2:

```ts
@Entry
@ComponentV2
struct Child {
  @Local val: number = 10;

  build() {
    Text(this.val.toString())
  }
}
```

**Complex Types**

In V1, \@State can observe changes in the top-level properties of complex objects. In V2, however, \@Local can only observe changes to the object itself, not its internal properties. To solve this issue, you need to add \@ObservedV2 to the class and add \@Trace to target properties.  

V1:

```ts
class Child {
  value: number = 10;
}

@Component
@Entry
struct example {
  @State child: Child = new Child();

  build() {
    Column() {
      Text(this.child.value.toString())
      // @State can observe the top-level changes.
      Button('value+1')
        .onClick(() => {
          this.child.value++;
        })
    }
  }
}
```

V2 migration policy: Use \@ObservedV2 and \@Trace.

```ts
@ObservedV2
class Child {
  @Trace public value: number = 10;
}

@ComponentV2
@Entry
struct example {
  @Local child: Child = new Child();

  build() {
    Column() {
      Text(this.child.value.toString())
      // @Local can only observe the object itself. Add @ObservedV2 and @Trace to Child to enable observation of internal properties.
      Button('value+1')
        .onClick(() => {
          this.child.value++;
        })
    }
  }
}
```

**External Initialization**

In V1, \@State enables variables to be initialized from outside the component. In V2, however, \@Local explicitly prohibits external initialization. To implement similar functionality, replace \@State with \@Param and \@Once in V2 to allow passing an initial value from outside and ensure that it is only synchronized once during initialization.

V1:

```ts
@Component
struct Child {
  @State value: number = 0;

  build() {
    Text(this.value.toString())
  }
}

@Entry
@Component
struct Parent {
  build() {
    Column() {
      // @State supports external initialization.
      Child({ value: 30 })
    }
  }
}
```

V2 migration policy: Use \@Param and \@Once.

```ts
@ComponentV2
struct Child {
  @Param @Once value: number = 0;

  build() {
    Text(this.value.toString())
  }
}

@Entry
@ComponentV2
struct Parent {
  build() {
    Column() {
      // @Local does not support external initialization. Use @Param and @Once instead.
      Child({ value: 30 })
    }
  }
}
```

### \@Link -> \@Param/\@Event

**Migration Rules**

In V1, \@Link allows two-way binding between parent and child components. For migration to V2, you can use \@Param and \@Event to simulate two-way synchronization: \@Param for one-way, parent-to-child data flow, and \@Event callbacks for child-triggered parent updates.

**Example**

V1:

```ts
@Component
struct Child {
  // @Link enables two-way data synchronization.
  @Link val: number;

  build() {
    Column() {
      Text('child: ' + this.val.toString())
      Button('+1')
        .onClick(() => {
          this.val++;
        })
    }
  }
}

@Entry
@Component
struct Parent {
  @State myVal: number = 10;

  build() {
    Column() {
      Text('parent: ' + this.myVal.toString())
      Child({ val: this.myVal })
    }
  }
}
```

V2 migration policy: Use \@Param and \@Event.

```ts
@ComponentV2
struct Child {
  // Combining @Param with @Event enables two-way data synchronization.
  @Param val: number = 0;
  @Event addOne: () => void;

  build() {
    Column() {
      Text('child: ' + this.val.toString())
      Button('+1')
        .onClick(() => {
          this.addOne();
        })
    }
  }
}

@Entry
@ComponentV2
struct Parent {
  @Local myVal: number = 10

  build() {
    Column() {
      Text('parent: ' + this.myVal.toString())
      Child({ val: this.myVal, addOne: () => this.myVal++ })
    }
  }
}
```

### \@Prop -> \@Param

**Migration Rules**

In V1, the \@Prop decorator allows child components to receive and modify parent-passed parameters. In V2, \@Param replaces \@Prop. However, \@Param decorated parameters are read-only and cannot be modified in the child component. Depending on the scenario, there are several migration strategies:

- Primitive types: For primitive type parameters, replace \@Prop with \@Param.
- Complex types: For complex objects requiring strict one-way data flow, perform a deep copy to prevent the child component from modifying the parent's data.
- Variable modification by the child component: Use \@Once to allow one-time local modification. Note that if \@Once is used, the current child component is initialized only once, and changes from the parent component cannot be synchronized to the child component.

**Example**

**Primitive Types**

For primitive type variables, \@Prop in V1 can be replaced with \@Param in V2.

V1:

```ts
@Component
struct Child {
  @Prop value: number;

  build() {
    Text(this.value.toString())
  }
}

@Entry
@Component
struct Parent {
  build() {
    Column() {
      Child({ value: 30 })
    }
  }
}
```

V2:

```ts
@ComponentV2
struct Child {
  @Param value: number = 0;

  build() {
    Text(this.value.toString())
  }
}

@Entry
@ComponentV2
struct Parent {
  build() {
    Column() {
      Child({ value: 30 })
    }
  }
}
```
**Complex Types**

In V2, to enforce strict one-way data flow and prevent child components from modifying parent data, you must use a deep copy when passing complex objects with \@Param. This prevents the transfer of object references.

V1:

```ts
class Fruit {
  apple: number = 5;
  orange: number = 10;
}

@Component
struct Child {
  // @Prop passes the Fruit class. When the properties of the child class are changed, the parent class is not affected.
  @Prop fruit: Fruit;

  build() {
    Column() {
      Text('child apple: ' + this.fruit.apple.toString())
      Text('child orange: ' + this.fruit.orange.toString())
      Button('apple+1')
        .onClick(() => {
          this.fruit.apple++;
        })
      Button('orange+1')
        .onClick(() => {
          this.fruit.orange++;
        })
    }
  }
}

@Entry
@Component
struct Parent {
  @State parentFruit: Fruit = new Fruit();

  build() {
    Column() {
      Text('parent apple: ' + this.parentFruit.apple.toString())
      Text('parent orange: ' + this.parentFruit.orange.toString())
      Child({ fruit: this.parentFruit })
    }
  }
}
```

V2:

```ts
@ObservedV2
class Fruit {
  @Trace apple: number = 5;
  @Trace orange: number = 10;

  // Use a deep copy to prevent the child component from modifying parent data.
  clone(): Fruit {
    let newFruit: Fruit = new Fruit();
    newFruit.apple = this.apple;
    newFruit.orange = this.orange;
    return newFruit;
  }
}

@ComponentV2
struct Child {
  @Param fruit: Fruit = new Fruit();

  build() {
    Column() {
      Text('child')
      Text(this.fruit.apple.toString())
      Text(this.fruit.orange.toString())
      Button('apple+1')
        .onClick(() => {
          this.fruit.apple++;
        })
      Button('orange+1')
        .onClick(() => {
          this.fruit.orange++;
        })
    }
  }
}

@Entry
@ComponentV2
struct Parent {
  @Local parentFruit: Fruit = new Fruit();

  build() {
    Column() {
      Text('parent')
      Text(this.parentFruit.apple.toString())
      Text(this.parentFruit.orange.toString())
      Child({ fruit: this.parentFruit.clone() })
    }
  }
}
```

**Variable Modification in Child Components**

In V1, child components can modify \@Prop decorated variables. However, in V2, \@Param is read-only. If a child component needs to modify a passed value, it can use \@Param together with \@Once to make local changes.

V1:

```ts
@Component
struct Child {
  // @Prop allows direct modification of the variable.
  @Prop value: number;

  build() {
    Column() {
      Text(this.value.toString())
      Button('+1')
        .onClick(() => {
          this.value++;
        })
    }
  }
}

@Entry
@Component
struct Parent {
  build() {
    Column() {
      Child({ value: 30 })
    }
  }
}
```

V2 migration policy: Use \@Param and \@Once.

```ts
@ComponentV2
struct Child {
  // @Param used together with @Once enables local modification.
  @Param @Once value: number = 0;

  build() {
    Column() {
      Text(this.value.toString())
      Button('+1')
        .onClick(() => {
          this.value++;
        })
    }
  }
}

@Entry
@ComponentV2
struct Parent {
  build() {
    Column() {
      Child({ value: 30 })
    }
  }
}
```

In V1, a child component can modify its @Prop decorated variables. These changes are applied locally and are not synced to the parent component. When the parent's data source updates, the child component receives the update and its local \@Prop values are overwritten.

V1:
- Changes to **localValue** in the child component **Child** are not synchronized to the parent component **Parent**.
- When **Parent** updates **value**, **Child** is notified and its **localValue** is overwritten.

```ts
@Component
struct Child {
  @Prop localValue: number = 0;

  build() {
    Column() {
      Text(`${this.localValue}`).fontSize(25)
      Button('Child +100')
        .onClick(() => {
          // Changes to localValue are not synchronized to Parent.
          this.localValue += 100;
        })
    }
  }
}

@Entry
@Component
struct Parent {
  @State value: number = 10;

  build() {
    Column() {
      Button('Parent +1')
        .onClick(() => {
          // When value is updated, Child is notified.
          this.value += 1;
        })
      Child({ localValue: this.value })
    }
  }
}
```
In V2, \@Param cannot be modified locally. When used with \@Once, the value is synchronized only once. In contrast, \@Monitor enables a writable local copy in the child component while still receiving updates from the parent component.

V2:
- When **Parent** is updated, it notifies the child component and triggers the **onValueChange** callback decorated with \@Monitor. This callback assigns the new value to **localValue** in the child component.
- Modifications to **localValue** remain local and are not propagated to **Parent**.
- Subsequent updates from **Parent** will overwrite **localValue** in the child component.

```ts
@ComponentV2
struct Child {
  @Local localValue: number = 0;
  @Param value: number = 0;

  @Monitor('value')
  onValueChange(mon: IMonitor) {
    console.info(`value has been changed from ${mon.value()?.before} to ${mon.value()?.now}`);
    // When the parent component's value changes, the child component receives an update notification, triggering the @Monitor decorated callback, which overwrites the local value with the new value from the parent.
    this.localValue = this.value;
  }

  build() {
    Column() {
      Text(`${this.localValue}`).fontSize(25)
      Button('Child +100')
        .onClick(() => {
          // Changes to localValue are not synchronized to Parent.
          this.localValue += 100;
        })
    }
  }
}

@Entry
@ComponentV2
struct Parent {
  @Local value: number = 10;

  build() {
    Column() {
      Button('Parent +1')
        .onClick(() => {
          // When value is updated, Child is notified.
          this.value += 1;
        })
      Child({ value: this.value })
    }
  }
}
```

### \@Provide/\@Consume -> \@Provider/\@Consumer
**Migration Rules**

The functionality of \@Provide and \@Consume in V1 is largely similar to \@Provider and \@Consumer in V2, making them generally interchangeable. However, several key differences may require adjustments depending on your implementation.
Key differences:

- Syntax requirement: In V1, \@Provide and \@Consume can be used without parentheses () if no alias is specified. In V2, \@Provider and \@Consumer must always be followed by parentheses (), whether or not an alias is specified.
- Matching rules: In V1, \@Provide and \@Consume can be matched by alias or variable name. In V2, matching is performed only by alias. Once an alias is specified, it becomes the exclusive matching key.
- Local initialization: In V1, \@Consume depends on the parent component's @Provide and does not support local initialization before API version 20. Since API version 20, local default values are used if no matching @Provide is found. For details, see [Setting Default Values for @Consume Decorated Variables](./arkts-provide-and-consume.md#setting-default-values-for-consume-decorated-variables). In V2, \@Consumer supports local initialization by default, using the local value if no matching \@Provider is available.
- Initialization from the parent component: In V1, \@Provide can be directly initialized from the parent component. In V2, \@Provider does not support external initialization. You must use @Param with @Once to receive the initial value from the parent and assign it to \@Provider.
- Overriding support: In V1, \@Provide requires explicit **allowOverride** to support overriding. In V2, \@Provider supports overriding by default. \@Consumer automatically resolves to the nearest \@Provider in the component tree.

**Example**

**Matching Rules**

In V1, \@Provide and \@Consume can be matched by alias or variable name. In V2, matching is performed only by alias (not variable name). Once an alias is specified, it becomes the exclusive matching key.

V1:

```ts
@Component
struct Child {
  // Both alias and variable name can be used as matching keys.
  @Consume('text') childMessage: string;
  @Consume message: string;

  build() {
    Column() {
      Text(this.childMessage)
      Text(this.message) // The value of Text is "Hello World."
    }
  }
}

@Entry
@Component
struct Parent {
  @Provide('text') message: string = 'Hello World';

  build() {
    Column() {
      Child()
    }
  }
}
```

V2:

```ts
@ComponentV2
struct Child {
  // The alias is the exclusive matching key. If the alias exists, the variable name cannot be used for matching.
  @Consumer('text') childMessage: string = 'default';
  @Consumer() message: string = 'default';

  build() {
    Column() {
      Text(this.childMessage)
      Text(this.message) // The value of Text is "default."
    }
  }
}

@Entry
@ComponentV2
struct Parent {
  @Provider('text') message: string = 'Hello World';

  build() {
    Column() {
      Child()
    }
  }
}
```

**Local Initialization**

In V1 prior to API version 20, \@Consume decorated variables cannot be locally initialized. They must rely on a matching \@Provide from a parent component. Failure to find a corresponding \@Provide results in a runtime exception. After migration to V2, @Consumer allows local initialization. If the matching @Provider is found, the local default value is used.

V1:

```ts
@Component
struct Child {
  // @Consume prohibits local initialization. If no matching @Provide is found, an exception is thrown.
  @Consume message: string;

  build() {
    Text(this.message)
  }
}

@Entry
@Component
struct Parent {
  @Provide message: string = 'Hello World';

  build() {
    Column() {
      Child()
    }
  }
}
```

V2:

```ts
@ComponentV2
struct Child {
  // @Consumer allows local initialization. The local default value will be used when \@Provider is not found.
  @Consumer() message: string = 'Hello World';

  build() {
    Text(this.message)
  }
}

@Entry
@ComponentV2
struct Parent {
  build() {
    Column() {
      Child()
    }
  }
}
```

**Initialization from the Parent Component**

In V1, \@Provide allows initialization from the parent component, and initial values can be passed directly through component parameters. In V2, \@Provider prohibits external initialization. To achieve equivalent functionality, use \@Param with \@Once in the child component to receive the initial value from the parent, and then assign it to the \@Provider variable.

V1:

```ts
@Entry
@Component
struct Parent {
  @State parentValue: number = 42;

  build() {
    Column() {
      // @Provide supports initialization from the parent component.
      Child({ childValue: this.parentValue })
    }
  }
}

@Component
struct Child {
  @Provide childValue: number = 0;

  build() {
    Column() {
      Text(this.childValue.toString())
    }
  }
}
```

V2:

```ts
@Entry
@ComponentV2
struct Parent {
  @Local parentValue: number = 42;

  build() {
    Column() {
      // @Provider prohibits localization from the parent component. To work around this, you can use @Param to receive the initial value and then assign it to @Provider.
      Child({ initialValue: this.parentValue })
    }
  }
}

@ComponentV2
struct Child {
  @Param @Once initialValue: number = 0;
  @Provider() childValue: number = this.initialValue;

  build() {
    Column() {
      Text(this.childValue.toString())
    }
  }
}
```

**Overriding Support**

In V1, \@Provide requires explicit **allowOverride** to support overriding. In V2, \@Provider supports overriding by default. \@Consumer automatically resolves to the nearest \@Provider in the component tree.

V1:

```ts
@Entry
@Component
struct GrandParent {
  @Provide('reviewVotes') reviewVotes: number = 40;

  build() {
    Column() {
      Parent()
    }
  }
}

@Component
struct Parent {
  // @Provide does not support overriding by default. To enable overriding, use **allowOverride**.
  @Provide({ allowOverride: 'reviewVotes' }) reviewVotes: number = 20;

  build() {
    Child()
  }
}

@Component
struct Child {
  @Consume('reviewVotes') reviewVotes: number;

  build() {
    Text(this.reviewVotes.toString ()) // The value of Text is 20.
  }
}
```

V2:

```ts
@Entry
@ComponentV2
struct GrandParent {
  @Provider('reviewVotes') reviewVotes: number = 40;

  build() {
    Column() {
      Parent()
    }
  }
}

@ComponentV2
struct Parent {
  // @Provider supports overriding by default. @Consumer searches for the nearest @Provider upwards.
  @Provider() reviewVotes: number = 20;

  build() {
    Child()
  }
}

@ComponentV2
struct Child {
  @Consumer() reviewVotes: number = 0;

  build() {
    Text(this.reviewVotes.toString ()) // The value of Text is 20.
  }
}
```

### \@Watch -> \@Monitor
**Migration Rules**

In V1, \@Watch observes state variable changes and triggers specified callbacks. In V2, \@Monitor replaces \@Watch, offering more flexible change detection with access to both previous and current variable values. The migration policies for different use scenarios are as follows:

- Single-variable listening: Directly replace \@Watch with \@Monitor.
- Multi-variable listening: In V1, \@Watch cannot access the previous value of the variable before the change. In V2, \@Monitor can listen for multiple variables at the same time and can access the values of the variables before and after the change.
**Example**

**Single-Variable Listening**

Use \@Monitor of V2 instead of \@Watch of V1.

V1:

```ts
@Entry
@Component
struct watchExample {
  @State @Watch('onAppleChange') apple: number = 0;

  onAppleChange(): void {
    console.info('apple count changed to ' + this.apple);
  }

  build() {
    Column() {
      Text(`apple count: ${this.apple}`)
      Button('add apple')
        .onClick(() => {
          this.apple++;
        })
    }
  }
}
```

V2:

```ts
@Entry
@ComponentV2
struct monitorExample {
  @Local apple: number = 0;

  @Monitor('apple')
  onFruitChange(monitor: IMonitor) {
    console.info(`apple changed from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  build() {
    Column() {
      Text(`apple count: ${this.apple}`)
      Button('add apple')
        .onClick(() => {
          this.apple++;
        })
    }
  }
}
```

**Multi-Variable Listening**

In V1, each \@Watch callback function can monitor only one variable and cannot obtain the value before the change. After migration to V2, you can use one \@Monitor to listen for multiple variables at the same time and obtain the values of the variables before and after the change.

V1:

```ts
@Entry
@Component
struct watchExample {
  @State @Watch('onAppleChange') apple: number = 0;
  @State @Watch('onOrangeChange') orange: number = 0;

  // @Watch callback, which is used to listen for only a single variable but cannot obtain the value before change.
  onAppleChange(): void {
    console.info('apple count changed to ' + this.apple);
  }

  onOrangeChange(): void {
    console.info('orange count changed to ' + this.orange);
  }

  build() {
    Column() {
      Text(`apple count: ${this.apple}`)
      Text(`orange count: ${this.orange}`)
      Button('add apple')
        .onClick(() => {
          this.apple++;
        })
      Button('add orange')
        .onClick(() => {
          this.orange++;
        })
    }
  }
}
```

V2:

```ts
@Entry
@ComponentV2
struct monitorExample {
  @Local apple: number = 0;
  @Local orange: number = 0;

  // @Monitor callback, which is used to listen for multiple variables and obtain the value before change.
  @Monitor('apple','orange')
  onFruitChange(monitor: IMonitor) {
    monitor.dirty.forEach((name: string) => {
      console.info(`${name} changed from ${monitor.value(name)?.before} to ${monitor.value(name)?.now}`);
    });
  }

  build() {
    Column() {
      Text(`apple count: ${this.apple}`)
      Text(`orange count: ${this.orange}`)
      Button('add apple')
        .onClick(() => {
          this.apple++;
        })
      Button('add orange')
        .onClick(() => {
          this.orange++;
        })
    }
  }
}
```
### \@Computed
**Migration Rules**

V1 lacks computed property support, leading to redundant calculations during UI re-renders. To address this, V2 introduces the \@Computed decorator, allowing you to optimize and cache expensive computations.

V1:

In the following example, each time the **lastName** value changes, the **Text** component is re-rendered and **this.lastName +' ' + this.firstName** needs to be computed repeatedly.

```ts
@Entry
@Component
struct Index {
  @State firstName: string = 'Li';
  @State lastName: string = 'Hua';

  build() {
    Column() {
      Text(this.lastName + ' ' + this.firstName)
      Text(this.lastName + ' ' + this.firstName)
      Button('changed lastName').onClick(() => {
        this.lastName += 'a';
      })

    }
  }
}
```

V2:

When \@Computed is used, the computation is triggered only once each time the **lastName** value changes.

```ts
@Entry
@ComponentV2
struct Index {
  @Local firstName: string = 'Li';
  @Local lastName: string = 'Hua';

  @Computed
  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  build() {
    Column() {
      Text(this.fullName)
      Text(this.fullName)
      Button('changed lastName').onClick(() => {
        this.lastName += 'a';
      })
    }
  }
}
```
