# Migration for Data Object State Variables
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @HelloCrease-->

This document explains how to migrate data object state variables from V1 to V2.
| V1 Decorator               | V2 Decorator                 |
|------------------------|--------------------------|
|[\@ObjectLink](./arkts-observed-and-objectlink.md)/[\@Observed](./arkts-observed-and-objectlink.md) /[\@Track](./arkts-track.md)|[\@ObservedV2](./arkts-new-observedV2-and-trace.md)/[\@Trace](./arkts-new-observedV2-and-trace.md)|

## Migration Examples

### \@ObjectLink/\@Observed/\@Track -> \@ObservedV2/\@Trace
**Migration Rules**

In V1, \@Observed and \@ObjectLink enable observation of objects and their first-level properties. Observing nested properties requires wrapping them in custom components with \@ObjectLink. \@Track provides property-level change tracking for precise updates.

In V2, \@ObservedV2 and \@Trace simplify the observation model. Observation capabilities are embedded directly into class objects and their nested properties. \@Trace combines observation with precise update control, replacing the functionality of \@Track. Key improvements are as follows:

- Nested object observation: \@ObservedV2 and \@Trace enable direct observation of nested properties without wrapper components.
- Precise updates: \@Trace ensures efficient UI updates at the property level.

**Example**

**Observing Nested Object Properties**

In V1, changes to nested object properties are not directly observable; only top-level property changes can be detected. Observation of nested object properties require a custom component with \@ObjectLink. V2 introduces \@ObservedV2 and \@Trace to enable direct observation of nested properties, significantly reducing complexity.

V1:

```ts
@Observed
class Address {
  city: string;

  constructor(city: string) {
    this.city = city;
  }
}

@Observed
class User {
  name: string;
  address: Address;

  constructor(name: string, address: Address) {
    this.name = name;
    this.address = address;
  }
}

@Component
struct AddressView {
  // The @ObjectLink decorated address in the child component is initialized from the parent component and receives the @Observed decorated address instance.
  @ObjectLink address: Address;

  build() {
    Column() {
      Text(`City: ${this.address.city}`)
      Button("city +a")
        .onClick(() => {
          this.address.city += "a";
        })
    }
  }
}

@Entry
@Component
struct UserProfile {
  @State user: User = new User("Alice", new Address("New York"));

  build() {
    Column() {
      Text(`Name: ${this.user.name}`)
      // Changes to nested object properties, such as this.user.address.city, cannot be observed directly.
      // Only top-level object property changes are observable. Therefore, the nested Address object must be extracted into the custom AddressView component.
      AddressView({ address: this.user.address })
    }
  }
}
```

V2 migration policy: Use \@ObservedV2 and \@Trace.

```ts
@ObservedV2
class Address {
  @Trace city: string;

  constructor(city: string) {
    this.city = city;
  }
}

@ObservedV2
class User {
  @Trace name: string;
  @Trace address: Address;

  constructor(name: string, address: Address) {
    this.name = name;
    this.address = address;
  }
}

@Entry
@ComponentV2
struct UserProfile {
  @Local user: User = new User("Alice", new Address("New York"));

  build() {
    Column() {
      Text(`Name: ${this.user.name}`)
      // Use @ObservedV2 and @Trace to directly observe nested object properties.
      Text(`City: ${this.user.address.city}`)
      Button("city +a")
        .onClick(() => {
          this.user.address.city += "a";
        })
    }
  }
}
```
**Observing Class Properties**

In V1, \@Observed decorates a class to enable observation at the object level, while @Track is used for specific property-level observation within that class. V2 simplifies this model: \@Trace handles property-level observation, and \@ObservedV2 is optimized for efficient UI updates at the object level.

V1:

```ts
@Observed
class User {
  @Track name: string;
  @Track age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

@Entry
@Component
struct UserProfile {
  @State user: User = new User('Alice', 30);

  build() {
    Column() {
      Text(`Name: ${this.user.name}`)
      Text(`Age: ${this.user.age}`)
      Button("increase age")
        .onClick(() => {
          this.user.age++;
        })
    }
  }
}
```

V2 migration policy: Use \@ObservedV2 and \@Trace.

```ts
@ObservedV2
class User {
  @Trace name: string;
  @Trace age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

@Entry
@ComponentV2
struct UserProfile {
  @Local user: User = new User('Alice', 30);

  build() {
    Column() {
      Text(`Name: ${this.user.name}`)
      Text(`Age: ${this.user.age}`)
      Button("Increase age")
        .onClick(() => {
          this.user.age++;
        })
    }
  }
}
```
