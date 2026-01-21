# Differences Between State Management V1 and V2 Update Mechanisms
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @s10021109-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

## Background of the Evolution from V1 State Management to V2 State Management

State management V1 uses a proxy-based observation mechanism, where a proxy wrapper is created for each state variable. The observer can detect proxy changes but cannot accurately observe actual data changes. V1 state management has the following restrictions:

- State variables cannot exist independently of the UI. Changes in one view are not automatically synchronized to other views sharing the same data.
- Only changes to top-level object properties can be detected; deep observation and listening are unsupported.
- Redundant updates exist in the scenario where the attributes of an object are changed.
- Decorator usage is restrictive. The input and output of state variables are not specified in components, complicating componentization design.

Based on the preceding reasons, the state management V2 enhances the data observation capability so that the data can be observed. Changes to data automatically trigger view re-renders. Compared with state management V1, state management V2 offers the following advantages:

- State variables are independent of the UI. Data changes automatically trigger updates to associated views.

- Deep observation and listening of objects are supported, with no performance impact from the deep observation mechanism.

- Precise attribute-level update of objects.

- Decorators are more user-friendly and scalable. Components explicitly define inputs and outputs, simplifying componentization.

## State Variable Changes Automatically Triggering UI Updates

When the state management framework detects a state change, it triggers a UI update. The state variable changes include the changes of observed object attributes or observed array (or other built-in types) items.
- For V1, the layer-1 observation capability is provided to observe the changes of object attributes and data items at the first layer.
- V2 has the in-depth observation capability and can observe the changes of nested object attributes or array items.

The following uses an example to describe the differences between V1 and V2 when the state variable is modified in [@Component](./arkts-create-custom-components.md#component) or [@ComponentV2](./arkts-create-custom-components.md#componentv2) and UI refresh is triggered.

```typescript
// The following code uses @ObservedV2 as an example. If V1 is used, @Observed and @Track are used.
@ObservedV2 
class ObsObjA {
  @Trace propA: string = 'propA';
  @Trace obsObjB: ObsObjB = new ObsObjB();
  constructor(propA: string) {
    this.propA = propA;
  }
}

@ObservedV2 
class ObsObjB {
  @Trace propB: string = 'propB';
}

@ObservedV2 
class ObsObjC {
  @Trace propC: string = 'propC';
  constructor(propC: string) {
    this.propC = propC;
  }
}

// The following code is written in @Component or @ComponentV2.
// simple is the state variable decorated by the V1 or V2 decorator, obsObjA is the complex state variable decorated by the V1 or V2 decorator, and arr is the array state variable decorated by the V1 or V2 decorator.
build() {
  Column() {
    Text(this.simple);  // The first line uses a simple state variable to bind the Text component.
    Text(JSON.stringify(this.obsObjA));  // The second line uses the complex object type state variable to bind the Text component.
    Text(this.obsObjA.propA); // The third line uses the complex object attribute state variable to bind the Text component.
    Text(this.obsObjA.obsObjB.propB); // The fourth line uses the nested complex object attribute state variable to bind the Text component.
    Text(JSON.stringify(this.arr)); // The fifth line uses the state variable of the array type to bind the Text component.
    Text(JSON.stringify(this.arr[0])); // The sixth line uses the state variable of item 0 in the array to bind the Text component.
    Text(JSON.stringify(this.arr[0].propC)); // The seventh line uses the state variable attribute of the element 0 in the array to bind the Text component.
  }
}
```

The V1 and V2 state management frameworks trigger the corresponding UI update by observing the value assignment of the state variable. The following code is used to describe the difference between the V1 and V2 state variable update:

```typescript
Button('Change state variable')
  .onClick(() => {
    // this.simple is a simple variable decorated by the V1 or V2 decorator. Assigning a value to this variable will trigger the update of the text in line 1 regardless of the V1 or V2 decorator variable.
    this.simple = 'Welcome';
    // this.obsObjA is a complex object variable decorated by the V1 or V2 decorator. Assigning a value to this variable will trigger the update of the text in lines 2, 3, and 4 regardless of the V1 or V2 decorator variable.
    this.obsObjA = new ObsObjA('obsObjA++');
    // this.arr is an array variable decorated by the V1 or V2 decorator. Assigning a value to this variable will trigger the update of the text in lines 5, 6, and 7 regardless of the V1 or V2 decorator variable.
    this.arr = [new ObsObjC('propC1'), new ObsObjC('propC2')];
    // For V1, if this.obsObjA is a variable decorated by the V1 decorator (the attribute in obsObjA is not decorated by @Track or this.obsObjA.propA is decorated by @Track).
    // If a value is assigned to the variable, the text in line 3 will be updated. For V2, this.obsObjA.propA must be decorated by a V2 decorator (such as @Trace) to assign a value to the variable so that the text in line 3 will be updated.
    this.obsObjA.propA = 'propA3';
    // For V1, only one layer of changes can be observed. Even if this.obsObjA.obsObjB.propB is decorated by the V1 decorator (@Track), the text in line 4 is not updated.
    // For V2, the text in line 4 can be updated as long as this.obsObjA.obsObjB.propB is decorated by the V2 decorator (@Trace).
    this.obsObjA.obsObjB.propB = 'propB3';
    // This.arr is decorated by the V1 or V2 decorator. A value is assigned to this variable. Both the V1 and V2 decorator variables trigger the text update in lines 5 and 6.
    this.arr[0] = new ObsObjC('propC3');
    // For V1, this.arr is decorated by the V1 decorator. Because V1 can observe only one layer of changes, the attribute value assignment of the array item is the modification of the second layer, and the text in line 7 is not updated.
    // For V2, this.arr is decorated by the V2 decorator, and propC is decorated by the V2 decorator (@Trace). Assign a value to this variable. The text in line 7 is updated.
    this.arr[0].propC = 'propC4';
  })
```

## Differences Between @Watch in V1 and @Monitor in V2

For details about the differences between @Watch of V1 and @Monitor of V2, see [Comparing @Monitor with @Watch](./arkts-new-monitor.md#comparing-monitor-with-watch). The following uses an example to describe the differences.

### @Watch Synchronous Execution
Assign values to V1 decorative variables. If an object attribute or array (Map or Set) item changes, the synchronous execution of @Watch is triggered. If the state variable is modified for multiple times, the @Watch function is executed for multiple times.

```typescript
@State @Watch('onVarNameChange') obsObjA: ObsObjA = new ObsObjA('propANew');

onVarNameChange() {  // The @Watch function is executed synchronously when the listened V1 decorative variable obsObjA changes.
  console.info('obsObjA.propA change callback'); // Execution sequence 3
}

Button('Change state variable')
  .onClick(() => {
    console.info('1'); // Execution sequence 1
    this.obsObjA.propA = 'propA3'; // Execution sequence 2
    console.info('2'); // Execution sequence 4
  })
```
In the preceding code, assign a value to this.obsObjA.propA. The execution sequence is as follows: print log '1', assign a value to the state variable, print log 'obsObjA.propA change callback', and print log '2'.

### @Monitor Asynchronous Execution
Assign values to V2 decorative variables. If an object attribute or array (Map or Set) item changes, the asynchronous execution of @Monitor is triggered. If the state variable is modified multiple times, the @Monitor function is executed only once.

```typescript
@Local arr: Array<ObsObjC> = [new ObsObjC('propC1')];

@Monitor('obsObjA.propA') onChange(mon : IMonitor) { // The @Monitor function is executed abnormally when the monitored V2 decoration variable obsObjA changes.
  console.info(`${mon.dirty[0]}`); // Execution sequence 4 (The onChange callback is executed only after the onClick logic is executed.)
}

Button('Change state variable')
  .onClick(() => {
    console.info('1'); // Execution sequence 1
    this.obsObjA.propA = 'propA3'; // Execution sequence 2
    console.info('2'); // Execution sequence 3
  })
```
In the preceding code, the @Monitor function is executed only after the current event logic is executed, for example, after onClick is executed. Assign a value to this.obsObjA.propA. The execution sequence is as follows: Print log '1', assign values to state variables, print log '2', execute 'onChange' of @Monitor, and print 'obsObjA.propA'.


## Differences Between V1 State Variable Update and V2 State Variable Update

The following figure shows the flowchart of V1 component and V2 state variable update differences. Compared with V1 state management, V2 state management asynchronously marks components dirty when state variables change.

![v1v2updatedifference](figures/v1v2update.PNG)

### Updating V1 Components

Step 1: Trigger an event to modify the V1 state variable and observe the change of the V1 state variable.

Step 2: Execute the @Watch callback to execute other logic in the event, for example, modifying other variables.

Step 3: The execution node is marked as dirty, the dirty node is placed in the dirty node list, and a Vsync signal is requested.

Step 4: Update the dirty node list. The update sequence is as follows: Update the parent component and then the child component.

Step 5: If the state variable changes again, step 4 is performed. In step 4, a quantity of iterations in a Vsync period does not exceed 3. After the third iteration, a node marked as dirty is added to the dirty node list, dirty nodes are updated when the next Vsync arrives.

### Updating V2 Components

Compared with V1 state management, V2 state management supports asynchronous execution of @Computed, @Monitor, and node dirty marking.

Step 1: The event triggers the modification of the V2 state variable and throws the [Promise](../../arkts-utils/async-concurrency-overview.md#promise) asynchronous task.

Step 2: Execute other remaining logic in the event, for example, modifying other variables. After the event logic (for example, the onClick event) is executed, execute the Promise callback.

Step 3: Update the @Computed variable.

Step 4: When the @Computed variable is updated, if the @Computed variable changes, go to step 3. Otherwise, go to step 5.

Step 5: Execute the @Monitor callback function.

Step 6: If a state variable changes in the @Monitor function callback, go to step 3. Otherwise, go to step 7.

Step 7: The execution node is marked as dirty, the dirty node is placed in the dirty node list, and a Vsync signal is requested.

Step 8: Update the dirty node list. The parent component is updated first, and then the child component is updated.

Step 9: In the update process, if the state variable changes again, step 8 is performed. In step 8, a quantity of iterations in a Vsync period does not exceed 3. After the third iteration, a dirty node is added to the dirty node list, dirty nodes are updated when the next Vsync arrives.
