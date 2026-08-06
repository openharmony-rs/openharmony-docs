# Compilation Error Codes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 10905301 @Watch Decorator Callback Function Is Not Defined
**Error Message**<br>
\'@Watch\' cannot be used with \'xxx\'. Apply it only to parameters that correspond to existing methods.  

**Description**<br>
This error code is reported when the callback function for the @Watch decorator is not defined.

**Possible Cause**<br>
The variable decorated with @Watch is defined in the struct, but the corresponding callback function is missing.

**Solution**<br>
Define a callback function with the same name in the struct to handle the watched variable.

## 10905101 @BuilderParam Initialization Error
**Error Message**<br>
\'@BuilderParam\' property can only initialized by \'@Builder\' function or \'@LocalBuilder\' method in struct.

**Description**<br>
This error code is reported when @BuilderParam decorated variables are initialized using methods other than those decorated with @Builder.

**Possible Cause**<br>
The @BuilderParam decorated variable is being initialized using a regular function or variable of another type.

**Solution**<br>
Define functions decorated with @LocalBuilder or @Builder and use them to initialize variables decorated with @BuilderParam.

## 10905302 Mixed Use of Multiple State Management Decorators
**Error Message**<br>
The property \'xxx\' cannot have multiple state management decorators.

**Description**<br>
This error code is reported when a variable is decorated with multiple state management decorators.

**Possible Cause**<br>
The same variable is decorated with multiple state management decorators.

**Solution**<br>
Use only one appropriate state management decorator for the variable.

## 10905303 State Variable Initialization Verification Exception
**Error Message**<br>
The \'xxx\' property \'yyy\' must be specified a default value.

**Description**<br>
This error code is reported when variables decorated with @State, @StorageLink, @StorageProp, @LocalStorageLink, @LocalStorageProp, or @Provide are not initialized.

**Possible Cause**<br>
Variables decorated with @State, @StorageLink, @StorageProp, @LocalStorageLink, @LocalStorageProp, or @Provide are not initialized.

**Solution**<br>
Initialize variables decorated with @State, @StorageLink, @StorageProp, @LocalStorageLink, @LocalStorageProp, and @Provide.

## 10905304 Failed to Verify the Initialization of a Specific Decorated Variable
**Error Message**<br>
The \'xxx\' property cannot be specified a default value.

**Description**<br>
This error code is reported when initialization is performed on variables decorated with decorators such as @Consume, @Link, and @ObjectLink.

**Possible Cause**<br>
Initialization is performed when defining variables decorated with decorators such as @Consume, @Link, and @ObjectLink.

**Solution**<br>
Do not initialize variables decorated with @Consume, @Link, and @ObjectLink. Refer to the correct value assignment rules for decorators.

## 10905305 Variable Type Verification Exception
**Error Message**<br>
The property \'xxx\' must specify a type.

**Description**<br>
This error code is reported when the type is not specified for a variable decorated with a decorator.

**Possible Cause**<br>
The type is not specified for a variable decorated with a decorator.

**Solution**<br>
Specify the type for the variable decorated with the decorator.

## 10905307 Failed to Verify the Specific Decorated Variable Type
**Error Message**<br>
\'@ObjectLink\' cannot be used with this type. Apply it only to classes decorated by \'@Observed\' or initialized using the return value of \'makeV1Observed\'.

**Description**<br>
This error code is reported when the type of a variable decorated with @ObjectLink is not a class or union type decorated with @Observed defined in an .ets file.

**Possible Cause**<br>
The variable decorated with @ObjectLink is initialized using a class that is not decorated with @Observed or another incompatible type.

**Solution**<br>
Ensure that class instances decorated with @Observed are used with @ObjectLink.

## 10905308 Failed to Verify the Decorator of a Specific Variable Type
**Error Message**<br>
The \'xxx\' property \'yyy\' cannot be a \'zzz\' object.

**Description**<br>
This error code is reported when a variable decorated with @State or other state decorators is of type CustomDialogController.

**Possible Cause**<br>
A state variable decorator is used on a variable of type CustomDialogController.

**Solution**<br>
Do not use state variable decorators on variables of type CustomDialogController.

## 10905309 Custom Decorator Name Verification Error
**Error Message**<br>
The decorator \'xxx\' cannot have the same name as the built-in style attribute \'yyy\'. 

**Description**<br>
This error code is reported when a custom decorator has the same name as a built-in property.

**Possible Cause**<br>
The custom decorator name conflicts with a built-in property name.

**Solution**<br>
Rename the custom decorator to avoid conflicts with built-in property names.

## 10905310 @Watch Decorator Verification Error
**Error Message**<br>
Regular variable \'xxx\' can not be decorated with \'@Watch\'. 

**Description**<br>
This error code is reported when a regular variable is decorated with @Watch.

**Possible Cause**<br>
The @Watch decorator is used on a regular variable.

**Solution**<br>
Use @Watch only on state variables decorated with appropriate state variable decorators, such as @State.

## 10905311 @Watch Decorator Parameter Verification Error
**Error Message**<br>
\'@Watch\' cannot be used with \'xxx\'. Apply it only to \'string\' parameters.

**Description**<br>
This error code is reported when the parameter of the @Watch decorator is not a string.

**Possible Cause**<br>
A non-string value is used as the parameter for the @Watch decorator.

**Solution**<br>
Ensure that the parameter of the @Watch decorator is a string.

## 10905312 Custom Decorator Verification Exception
**Error Message**<br>
The inner decorator \'xxx\' cannot be used together with custom decorator.

**Description**<br>
This error code is reported when built-in component decorators such as @State are used together with custom decorators.

**Possible Cause**<br>
A custom decorator is applied to a variable that already has a built-in component decorator, such as @State.

**Solution**<br>
Avoid using both state variable decorators (such as @State) and custom decorators on the same variable.

## 10905201 Parent Component Verification Error
**Error Message**<br>
The \'xxx\' component can only be nested in the \'yyy\' parent component.

**Description**<br>
This error code is reported when a component's parent is not the specified parent component.

**Possible Cause**<br>
The parent component of a component (for example, **Blank**) is not within the allowed range of parent components.

**Solution**<br>
Modify the parent component or add an intermediate component based on the error description.

## 10905202 Failed to Verify the Child Component of the Button Component
**Error Message**<br>
The Button component with a label parameter can not have any child.

**Description**<br>
This error code is reported when a **Button** component with a label contains child components.

**Possible Cause**<br>
The **Button** component includes both a label and child components, which is not allowed.

**Solution**<br>
Remove either the label content or the child component content (including the braces).

## 10905203 .stateStyles Syntax Check Error
**Error Message**<br>
\'.stateStyles\' doesn't conform standard.

**Description**<br>
This error code is reported when the **stateStyles** property does not comply with the syntax.

**Possible Cause**<br>
The **stateStyles** property is incorrectly specified or does not conform to the required syntax.

**Solution**<br>
Ensure that different states in **stateStyles** are correctly specified.

## 10905204 UI Component Syntax Check Error
**Error Message**<br>
\'xxx\' does not meet UI component syntax.

**Description**<br>
This error code is reported when a statement does not comply with the UI component syntax.

**Possible Cause**<br>
The code does not follow the basic UI component syntax.

**Solution**<br>
Modify the syntax according to the correct UI component syntax.

## 10905207 Failed to Verify the then Clause of the if Statement
**Error Message**<br>
Then statement cannot be null in if statement.

**Description**<br>
This error code is reported when the **if** statement is missing a **then** clause.

**Possible Cause**<br>
The **then** statement in the **if** syntax is empty.

**Solution**<br>
Add a valid **then** clause after the **if** statement.

## 10905208 Failed to Verify the Judgment Condition of the if Statement
**Error Message**<br>
Condition expression cannot be null in if statement.

**Description**<br>
This error code is reported when the **if** statement is missing a condition.

**Possible Cause**<br>
The judgment condition of the **if** statement is empty.

**Solution**<br>
Add a valid condition to the **if** statement.

## 10905102 @BuilderParam Tail Closure Scenario Verification Exception
**Error Message**<br>
In the trailing lambda case, \'xxx\' must have one and only one property decorated with \'@BuilderParam\', and its \'@BuilderParam\' expects no parameter.

**Description**<br>
This error code is reported when multiple variables decorated with @BuilderParam are defined in the trailing closure scenario, or a variable decorated with @BuilderParam contains parameters.

**Possible Cause**<br>
In the trailing closure scenario, there can be only one variable decorated with @BuilderParam (excluding parameters).

**Solution**<br>
Remove unnecessary @BuilderParam decorators and retain only one @BuilderParam decorator without parameters.

## 10905209 UI Syntax Verification Error with the build() Method
**Error Message**<br>
Only UI component syntax can be written here.

**Description**<br>
This error code is reported when content other than UI syntax is used.

**Possible Cause**<br>
Non-UI syntax is used.

**Solution**<br>
Modify the syntax according to the correct UI component syntax.

## 10905210 Root Container Verification Error with the build() Method
**Error Message**<br>
In an \'@Entry\' decorated component, the \'build\' method can have only one root node, which must be a container component.

**Description**<br>
This error code is reported when multiple root containers are defined in the **build()** method.

**Possible Cause**<br>
Multiple root containers are defined in the build() method.

**Solution**<br>
Remove redundant root containers to ensure that the **build()** method has only one root container.

## 10905103 Failed to Verify the build() Method
**Error Message**<br>
The struct \'xxx\' must have at least and at most one 'build' method.

**Description**<br>
This error code is reported when multiple **build()** methods are defined in the struct component, or the **build()** method is missing.

**Possible Cause**<br>
Multiple **build()** methods are defined in the struct, or the **build()** method is missing.

**Solution**<br>
Define only one **build()** method in the struct.

## 10905211 Failed to Verify @CustomDialog Member Properties
**Error Message**<br>
The \'@CustomDialog\' decorated custom component must contain a property of the CustomDialogController type.

**Description**<br>
This error code is reported when a custom component decorated with @CustomDialog lacks a member property of the CustomDialogController type.

**Possible Cause**<br>
The custom component decorated with @CustomDialog does not have a member property of the CustomDialogController type.

**Solution**<br>
Add a member property of the CustomDialogController type to the custom component decorated with @CustomDialog.

## 10905212 Struct Verification Error
**Error Message**<br>
Structs are not allowed to inherit from classes or implement interfaces.

**Description**<br>
This error code is reported when a struct is defined as a subclass or implementation of another class or API.

**Possible Cause**<br>
The struct extends another class or implements another API.

**Solution**<br>
Do not use structs to extend other classes or implement other APIs.

## 10905104 Failed to Verify the Static Method Decorator of the Custom Component
**Error Message**<br>
Static methods in custom components cannot be decorated by \'@LocalBuilder\'.

**Description**<br>
This error code is reported when the @LocalBuilder decorator is used on static methods in custom components.

**Possible Cause**<br>
The @LocalBuilder decorator is used on static methods.

**Solution**<br>
Remove the **static** keyword.

## 10905105 @Styles Decorator Verification Error
**Error Message**<br>
\'@Styles\' decorated functions and methods cannot have arguments.

**Description**<br>
This error code is reported when parameters are included in functions decorated with @Styles.

**Possible Cause**<br>
Parameters are included in functions decorated with @Styles.

**Solution**<br>
Remove the parameters from the @Styles decorator.

## 10905106 Failed to Verify the build() Method
**Error Message**<br>
The \'build\' method can not have arguments.

**Description**<br>
This error code is reported when parameters are included in the **build()** method.

**Possible Cause**<br>
Parameters are included in the **build()** method.

**Solution**<br>
Remove the parameters from the **build()** method.

## 10905313 Failed to Verify the Struct Variable
**Error Message**<br>
The static variable of struct cannot be used together with built-in decorators.

**Description**<br>
This error code is reported when a built-in decorator is used to decorate a static variable in the struct.

**Possible Cause**<br>
A built-in decorator is used to decorate a static variable in the struct.

**Solution**<br>
Do not use built-in decorators to decorate static variables in structs.

## 10905314 \$ Use Verification Error
**Error Message**<br>
Property \'xxx\' cannot initialize using \'\$\' to create a reference to a variable.

**Description**<br>
This error code is reported when $ is used incorrectly to decorate a variable. $ can only be used on child component attributes decorated with @Link.

**Possible Cause**<br>
The \$ symbol is used to decorate a property member that is decorated with @Prop or other property members not decorated with @Link in a child component.

**Solution**<br>
Use the @Link decorator to decorate the corresponding variable in the child component, or remove \$.

## 10905315 Parent and Child Component Value Verification Exception
**Error Message**<br>
The \'xxx\' property \'yyy\' cannot be assigned to the \'zzz\' property \'nnn\'.

**Description**<br>
This error code is reported when the value assignment between parent and child components is incorrect.

**Possible Cause**<br>
A regular variable is used to initialize a member variable decorated with @Link in a child component.

**Solution**<br>
Do not use regular variables to initialize member variables decorated with @Link in child components.

## 10905316 @Link Decorator Variable Initialization Verification Exception
**Error Message**<br>
The property \'xxx\' in the custom component \'yyy\' is missing (mandatory to specify).

**Description**<br>
This error code is reported when variables decorated with @Link are not initialized from the parent component.

**Possible Cause**<br>
The member variable decorated with @Link in the child component is not initialized when the parent component calls the child component.

**Solution**<br>
Initialize variables decorated with @Link from the parent component.

## 10905317 Failed to Verify the Initialization of a Decorated Variable
**Error Message**<br>
The property \'xxx\' in the custom component \'yyy\' cannot be initialized here (forbidden to specify).

**Description**<br>
This error code is reported when variables decorated with @StorageProp, @StorageLink, @Consume, or other decorators are initialized when a parent component calls a child component.

**Possible Cause**<br>
Member variables decorated with @StorageProp, @StorageLink, and @Consume are initialized when the parent component calls the child component.

**Solution**<br>
Correctly use variables decorated with the @StorageProp, @StorageLink, or @Consume decorator. For details, see the reference documentation of these decorators.

## 10905318 Verification Error During Parent-to-Child Transfer Using !! with a V2 Component
**Error Message**<br>
When the two-way binding syntax is used, the initial value of property \'xxx\' must be a variable.

**Description**<br>
This error code is reported when non-variables are used for parent-child transfer using **!!** with a V2 component.

**Possible Cause**<br>
Functions, constants, or literals are used for parent-child transfer using **!!** with a V2 component.

**Solution**<br>
When using **!!** with a V2 component for parent-child transfer, make sure only variables are used.

## 10905319 Child Component Variable Verification Error During !! Use with a V2 Component
**Error Message**<br>
When the two-way binding syntax is used, the variable \'xxx\' must be decorated with \'@Param\', and the \'@Event\' variable \'yyy\' must be defined in the \'zzz\'.

**Description**<br>
This error code is reported when @Param is not used together with @Event when **!!** is used with a V2 component.

**Possible Cause**<br>
When a V2 component is used, the child component variable is not decorated with @Param or the @Event decorated callback method is not defined.

**Solution**<br>
Use @Param to decorate child component variables and define the callback method decorated with @Event in the V2 scenario.

## 10905320 @Param Initialization Verification Error in the V2 Scenario
**Error Message**<br>
The optional character can not be used in the initial value of property \'xxx\'.

**Description**<br>
This error code is reported when optional symbols are used to transfer @Param decorated variables defined by child components in the V2 scenario.

**Possible Cause**<br>
In the V2 scenario, an optional symbol is used for initializing an @Param decorated variable in the child component.

**Solution**<br>
Avoid using optional symbols when initializing variables decorated with @Param in the V2 scenario.

## 10905321 Failed to Verify the Initialization of @Prop and @BuilderParam Decorated Variables
**Error Message**<br>
\'@Required\' decorated \'xxx\' must be initialized through the component constructor.

**Description**<br>
This error code is reported when the initialization of the @Prop and @BuilderParam decorated variables is incorrect.

**Possible Cause**<br>
The @Require decorator is used with @Prop and @BuilderParam to decorate child component variables, but these variables fail to be initialized when the parent component calls the child component.

**Solution**<br>
Make sure variables decorated with @Require, @Prop, or @BuilderParam are initialized when the parent component calls the child component.

## 10905213 Incorrect Mixed Use of V1 and V2 Components
**Error Message**<br>
A V2 component cannot be used with any member property decorated by \'@Link\' in a V1 component.

**Description**<br>
This error code is reported when a V2 component is used together with the @Link decorator of a V1 component.

**Possible Cause**<br>
V1 components containing the @Link decorator are used within V2 components.

**Solution**<br>
Avoid using V1 components with the @Link decorator in V2 components.

## 10905323 V2 Decorator Decorated Properties Incorrectly Assigned to V1 Components
**Error Message**<br>
Property \'xxx\' in the \'@ComponentV2\' component \'yyy\' is not allowed to be assigned values here.

**Description**<br>
This error code is reported when a property decorated with a V2 decorator is assigned to a V1 component.

**Possible Cause**<br>
The V1 component called is assigned with a property decorated with a V2 decorator.

**Solution**<br>
Do not assign values of properties decorated with V2 decorators to V1 components.

## 10905324 Incorrect Initialization of a Specific Decorated Variable
**Error Message**<br>
The \'xxx\' property \'yyy\' in the custom component \'zzz\' cannot be initialized here (forbidden to specify).

**Description**<br>
This error code is reported when variables decorated with specific decorators are initialized during parent-child component calls.

**Possible Cause**<br>
A variable decorated with a specific decorator in a child component is not correctly initialized when called in the parent component.

**Solution**<br>
Follow the usage guidelines of the specific decorators.

## 10905325 Incorrect Use of @Require in the V2 Scenario
**Error Message**<br>
In a struct decorated with \'@ComponentV2\', \'@Require\' can only be used with \'@Param\'.

**Description**<br>
This error code is reported when the @Require decorator is used with a decorator other than @Param in the V2 scenario.

**Possible Cause**<br>
The @Require decorator is used with a decorator other than @Param in the V2 scenario.

**Solution**<br>
Use @Require together with @Param.

## 10905326 Incorrect Use of @Once in the V2 Scenario
**Error Message**<br>
When a variable decorated with \'@Once\', it must also be decorated with \'@Param\'.

**Description**<br>
This error code is reported when the @Once decorator is used without the @Param decorator in the V2 scenario.

**Possible Cause**<br>
The variable decorated with @Once is not decorated with @Param in the V2 scenario.

**Solution**<br>
Use @Once together with @Param.

## 10905327 Failed to Verify the Default Value of @Param in the V2 Scenario
**Error Message**<br>
When a variable decorated with \'@Param\' is not assigned a default value, it must also be decorated with \'@Require\'. 

**Description**<br>
This error code is reported when a variable decorated with @Param in a V2 component is not assigned a default value and is not decorated with @Require.

**Possible Cause**<br>
In the V2 scenario, the @Param decorator is used to decorate variables that are not assigned default values or decorated with the @Require decorator.

**Solution**<br>
Assign a default value to the variable decorated with @Param or decorate it with @Require.

## 10905107 @BuilderParam Initialization Error
**Error Message**<br>
\'@BuilderParam\' property can only be initialized by \'@Builder\' function.

**Description**<br>
This error code is reported when @BuilderParam decorated variables are initialized using methods other than those decorated with @Builder.

**Possible Cause**<br>
Other types of variables or regular functions are used to initialize variables decorated with @BuilderParam.

**Solution**<br>
Change the initial value of @BuilderParam to a function decorated with @Builder.

## 10905328 Failed to Verify the Member Type of a State Variable
**Error Message**<br>
The property \'xxx\' must specify a type.

**Description**<br>
This error code is reported when the member property type of a state variable fails verification.

**Possible Cause**<br>
The type of the state variable is not declared.

**Solution**<br>
Declare the type for the state variable. The type must meet the verification requirements.

## 10906217 Failed to verify Service Widget Parameters
**Error Message**<br>
\'@Entry\' doesn't support {} parameter in card. 

**Description**<br>
This error code is reported when @Entry in the service widget does not support the specified input parameter.

**Possible Cause**<br>
An invalid parameter is passed to @Entry in the service widget.

**Solution**<br>
Rectify the issue based on the error message.

## 10905108 @Extend Decorator Parameter Verification Error
**Error Message**<br>
\'xxx\' should have one and only one parameter.

**Description**<br>
This error code is reported when decorators such as @Extend do not have exactly one parameter.

**Possible Cause**<br>
When using decorators such as @Extend, no parameter is provided or multiple parameters are provided.

**Solution**<br>
Make sure decorators such as @Extend have exactly one parameter.

## 10903329 Resource Name Verification Exception
**Error Message**<br>
Unknown resource name \'xxx\'.

**Description**<br>
This error code is reported when the resource name fails verification.

**Possible Cause**<br>
The provided resource name is incorrect.

**Solution**<br>
Make sure the resource name is correct.

## 10903330 Resource Type Verification Exception
**Error Message**<br>
Unknown resource type \'xxx\'.

**Description**<br>
This error code is reported when the resource type fails verification.

**Possible Cause**<br>
The provided resource type is incorrect.

**Solution**<br>
Make sure the resource type is correct.

## 10903331 Resource Source Verification Exception
**Error Message**<br>
Unknown resource source \'xxx\'.

**Description**<br>
This error code is reported when the resource source fails verification.

**Possible Cause**<br>
The provided resource source is incorrect.

**Solution**<br>
Make sure the resource source is correct.

## 10905332 Resource Reference Format Verification Exception
**Error Message**<br>
Invalid resource file parameter. Enter a value in the format of \'xxx.yyy.zzz\'.

**Description**<br>
This error code is reported when the resource is incorrectly referenced.

**Possible Cause**<br>
The format used to reference resources is incorrect.

**Solution**<br>
Make sure the format used to reference resources is correct.

## 10904333 Resource Verification Exception
**Error Message**<br>
No such \'xxx\' resource in current module.

**Description**<br>
This error code is reported when the **\$rawfile\(\)** references a resource that does not exist.

**Possible Cause**<br>
The provided resource does not exist.

**Solution**<br>
Make sure the resource name and path used match those specified using **\$rawfile**.

## 10905109 wrapBuilder Parameter Verification Exception
**Error Message**<br>
The wrapBuilder\'s parameter should be a \'@Builder\' function.

**Description**<br>
This error code is reported when the parameter of **wrapBuilder** is not a global function decorated with @Builder.

**Possible Cause**<br>
The parameter of **wrapBuilder** is not an @Builder decorated function.

**Solution**<br>
Change the parameter of **wrapBuilder** to a global function decorated with @Builder.

## 10905110 @Styles Verification Exception
**Error Message**<br>
\'@Styles\' decorated functions and methods cannot have arguments.

**Description**<br>
This error code is reported when the method decorated with the @Styles decorator contains parameters.

**Possible Cause**<br>
The method decorated with the @Styles decorator contains parameters.

**Solution**<br>
Remove the parameters from the @Styles decorated method.

## 10905111 Incorrect Mixed Use of @AnimatedExtend and @Extend
**Error Message**<br>
The function can not be decorated by \'@Extend\' and \'@AnimatedExtend\' at the same time.

**Description**<br>
This error code is reported when both @AnimatedExtend and @Extend decorators are used to decorate the same API.

**Possible Cause**<br>
Both the @AnimatedExtend and @Extend decorators are used to decorate the same API.

**Solution**<br>
Remove either the @Extend or @AnimatedExtend decorator.

## 10905112 Decorator Verification Error
**Error Message**<br>
\'xxx\' can not decorate the method.

**Description**<br>
This error code is reported when invalid decorators such as @State are used to decorate methods.

**Possible Cause**<br>
Property decorators such as @State are used to decorate methods.

**Solution**<br>
Do not use property decorators such as @State to decorate methods.

## 10905219 Incorrect Use of Child Components
**Error Message**<br>
The component \'xxx\' can only have the child component \'yyy\'.

**Description**<br>
This error code is reported when unsupported child components are used in components such as **ContainerSpan**.

**Possible Cause**<br>
A component such as **ContainerSpan** is used incorrectly with a child component outside the supported range.

**Solution**<br>
Change the child component to one within the specified range.

## 10905220 Incorrect Number of Child Components
**Error Message**<br>
The \'xxx\' component can have only one child component.

**Description**<br>
This error code is reported when components such as **Button** that allows only a single child component contains multiple child components.

**Possible Cause**<br>
Multiple child components are defined in a component that allows only a single child component.

**Solution**<br>
Make sure the component in question has only one child component.

## 10905221 Incorrect Number of Child Components of a Specific Component
**Error Message**<br>
When the component \'xxx\' set \'yyy\' as \'zzz\', it can only have a single child component. 

**Description**<br>
This error code is reported when multiple child components are defined for a specific component attribute that allows only a single child component.

**Possible Cause**<br>
Multiple child components are defined for a specific component attribute that allows only a single child component.

**Solution**<br>
Delete redundant child components of the specific component. Retain a maximum of one child component.

## 10905222 Failed to Verify Components Such as Image
**Error Message**<br>
The component \'xxx\' can't have any child.

**Description**<br>
This error code is reported when components such as **Image** contain braces (child components).

**Possible Cause**<br>
Child components are defined for components that do not allow child components, such as **Image**.

**Solution**<br>
Delete the child components.

## 10905223 Incorrect Number of Child Components of a Specific Component
**Error Message**<br>
When the component \'xxx\' set \'yyy\' as \'zzz\', it can't have any child. 

**Description**<br>
This error code is reported when child components are defined for the target component attribute that does not allow child components.

**Possible Cause**<br>
Child components are defined for the target component attribute that does not allow child components.

**Solution**<br>
Delete the child components from the target component.

## 10905113 Incorrect Use of @Extend
**Error Message**<br>
Use the \'xxx\' decorator only in the global scope.

**Description**<br>
This error code is reported when decorators such as @Extend is used to decorate a member property method of a class or struct.

**Possible Cause**<br>
A decorator such as @Extend is used in a class or struct.

**Solution**<br>
Follow the usage guidelines of decorators.

## 10905337 Incorrect Decorator Use
**Error Message**<br>
The \'xxx\' decorator can only be used with \'struct\'.

**Description**<br>
This error code is reported when a struct decorator is used to decorate non-structs.

**Possible Cause**<br>
Struct decorators such as @Component and @ComponentV2 are used to decorate non-structs, such as functions.

**Solution**<br>
Use the correct decorator based on the error message.

## 10905338 V2 Decorator Verification Error
**Error Message**<br>
The \'xxx\' decorator can only be used in a \'struct\' decorated with \'@ComponentV2\'.

**Description**<br>
This error code is reported when a V2 member decorator is used in a struct not decorated with @ComponentV2.

**Possible Cause**<br>
The V2 member decorator is used in a struct decorated with @Component.

**Solution**<br>
Apply the V2 member decorator according to the instructions provided in the error message.

## 10905339 V1 Decorator Verification Error
**Error Message**<br>
The \'xxx\' decorator can only be used in a \'struct\' decorated with \'@Component\'.

**Description**<br>
This error code is reported when the member decorator of V1 is used in a struct not decorated with @Component.

**Possible Cause**<br>
The V1 member decorator is used in a struct decorated with @ComponentV2.

**Solution**<br>
Apply the V1 member decorator according to the instructions provided in the error message.

## 10905224 An @Observed Decorated Class Cannot Inherit from an @ObservedV2 Decorated Class
**Error Message**<br>
A class decorated by \'@Observed\' cannot inherit from a class decorated by \'@ObservedV2\'.

**Description**<br>
This error code is reported when an @Observed decorated class inherits from an @ObservedV2 decorated class.

**Possible Cause**<br>
An @Observed decorated class inherits from an @ObservedV2 decorated class.

**Solution**<br>
Inherit from a class decorated with @Observed or change the class decorator to @ObservedV2.

## 10905225 An @ObservedV2 Decorated Class Cannot Inherit from an @Observed Decorated Class
**Error Message**<br>
A class decorated by \'@ObservedV2\' cannot inherit from a class decorated by \'@Observed\'.

**Description**<br>
This error code is reported when an @ObservedV2 decorated class inherits from an @Observed decorated class.

**Possible Cause**<br>
An @ObservedV2 decorated class inherits from an @Observed decorated class.

**Solution**<br>
Inherit from a class decorated with @ObservedV2 or change the class decorator to @Observed.

## 10905226 Incorrect Mixed Use of @Observed and @ObservedV2
**Error Message**<br>
A class can not be decorated by \'@Observed\' and \'@ObservedV2\' at the same time.

**Description**<br>
This error code is reported when a class is decorated with both @Observed and @ObservedV2.

**Possible Cause**<br>
Both @Observed and @ObservedV2 are used to decorate the same class.

**Solution**<br>
Retain only one appropriate class decorator.

## 10905340 Incorrect Use of Decorators Designed to Decorate Member Variables in a Class
**Error Message**<br>
The \'xxx\' can decorate only member variables in a \'class\'.

**Description**<br>
This error code is reported when decorators designed to decorate member variables in a class are used to decorate methods instead.

**Possible Cause**<br>
Decorators designed to decorate member variables in a class, such as @Type, are used to decorate methods instead.

**Solution**<br>
Remove the decorators in question from methods in the class.

## 10905341 Incorrect Mixed Use of @Type and @Observed
**Error Message**<br>
The \'xxx\' decorator can not be used in a \'class\' decorated with \'@Observed\'.

**Description**<br>
This error code is reported when the decorator used in an @Observed decorated class is not supported.

**Possible Cause**<br>
The decorator used in an @Observed decorated class is not supported.

**Solution**<br>
Remove the unsupported decorator.

## 10905342 Incorrect Mixed Use of @Type and @Sendable
**Error Message**<br>
The \'xxx\' decorator can not be used in a \'class\' decorated with \'@Sendable\'.

**Description**<br>
This error code is reported when the decorator used in an @Sendable decorated class is not supported.

**Possible Cause**<br>
The decorator used in an @Sendable decorated class is not supported.

**Solution**<br>
Remove the unsupported decorator.

## 10905343 Incorrect Use of Decorators Designed to Decorate Member Methods in an @ObservedV2 Decorated Class
**Error Message**<br>
The \'xxx\' can decorate only member \'yyy\' within a \'class\' decorated with \'@ObservedV2\'.

**Description**<br>
This error code is reported when decorators designed to decorate member methods in an @ObservedV2 decorated class are used to decorate member methods in classes decorated with @Observed.

**Possible Cause**<br>
Decorators designed to decorate member methods in an @ObservedV2 decorated class are used to decorate member methods in classes decorated with @Observed.

**Solution**<br>
Use the decorator in question, such as @Monitor, only in @ObservedV2 decorated classes. In @Observed classes, use the @Watch decorator instead.

## 10905344 Incorrect Use of @Track and a V2 Decorator
**Error Message**<br>
\'xxx\' cannot be used with classes decorated by \'@ObservedV2\'. Use the \'@Trace\' decorator instead.

**Description**<br>
This error code is reported when a decorator designed for V1 is used with an @ObservedV2 decorated class.

**Possible Cause**<br>
A decorator designed for V1, such as @Track, is used with an @ObservedV2 decorated class.

**Solution**<br>
Do not use decorators designed for V1 in @ObservedV2 decorated classes.

## 10905345 Incorrect Use of @Track Outside a Class
**Error Message**<br>
The \'xxx\' decorator can decorate only member variables of a class.

**Description**<br>
This error code is reported when a decorator designed for use within a class is applied outside of a class.

**Possible Cause**<br>
A decorator designed for use within a class, such as @Track, are applied outside of a class.

**Solution**<br>
Make sure the decorators designed for use within a class are applied only within a class.

## 10905346 Incorrect Use of a V2 Decorator
**Error Message**<br>
\'xxx\' can only decorate member property.

**Description**<br>
This error code is reported when decorators such as @Local, @Param, @Once, @Event, @Provider, @Consume, and @BuilderParam are used to decorate non-member properties in @ComponentV2.

**Possible Cause**<br>
The @Local, @Param, @Once, @Event, @Provider, @Consume, or @BuilderParam decorator is used to decorate a non-member property in @ComponentV2.

**Solution**<br>
Use @Local, @Param, @Once, @Event, @Provider, @Consume, and @BuilderParam only to decorate member properties in @ComponentV2.

## 10905115 Incorrect Use of Method Decorators
**Error Message**<br>
\'xxx\' can only decorate method.

**Description**<br>
This error code is reported when method decorators, such as @LocalBuilder and @Monitor, are used to decorate non-methods.

**Possible Cause**<br>
Method decorators, such as @LocalBuilder and @Monitor, are used to decorate property variables, global functions, or methods in classes.

**Solution**<br>
Use the method decorators only to decorate methods.

## 10905116 Incorrect Use of the @Computed Decorator
**Error Message**<br>
\'@Computed\' can only decorate 'GetAccessor'.

**Description**<br>
This error code is reported when @Computed is used to decorate a method that is not a getter.

**Possible Cause**<br>
The @Computed decorator is used to decorate a non-getter method.

**Solution**<br>
Use @Computed only to decorate getter methods.

## 10905117 Incorrect Mixed Use of Method Decorators
**Error Message**<br>
A function can only be decorated with one of the \'@AnimatedExtend\', \'@Builder\', \'@Extend\', \'@Styles\', \'@Concurrent\' and \'@Sendable\''.

**Description**<br>
This error code is reported when two different method decorators are defined on the same method.

**Possible Cause**<br>
Multiple method decorators are defined on the same method.

**Solution**<br>
Select a single appropriate method decorator to use.

## 10905119 Duplicate Decorators
**Error Message**<br>
Duplicate \'xxx\' decorators for method are not allowed.

**Description**<br>
This error code is reported when the same decorator is applied to the same method multiple times.

**Possible Cause**<br>
The same decorator is used repeatedly for a method.

**Solution**<br>
Avoid using the same decorator multiple times on the same method.

## 10905121 Incorrect Mixed Use of Built-in Decorators
**Error Message**<br>
The member property or method can not be decorated by multiple built-in decorators.

**Description**<br>
This error code is reported when multiple built-in decorators are used to decorate the same member property or method.

**Possible Cause**<br>
Multiple built-in decorators are used on the same member property or method.

**Solution**<br>
Select a single appropriate built-in decorator to use.

## 10905348 Invalid State Variable Type
**Error Message**<br>
The type of the \'xxx\' property can not be a class decorated with \'@ObservedV2\'.

**Description**<br>
This error code is reported when a class decorated with @ObservedV2 is used as the type of a state variable.

**Possible Cause**<br>
A class decorated with @ObservedV2 is used as the type of a state variable.

**Solution**<br>
Avoid using classes decorated with @ObservedV2 as the type for state variables.

## 10905122 Incorrect Use of the @Concurrent Decorator
**Error Message**<br> 
\'@Concurrent\' can not be used on \'xxx\' function declaration.

**Description**<br>
This error code is reported when @Concurrent is used to decorate a specific function.

**Possible Cause**<br>
The @Concurrent decorator is used to decorate a specific function.

**Solution**<br>
Do not use the @Concurrent decorator on specific functions.

## 10905123 Incorrect Use of @Concurrent on Methods
**Error Message**<br>
\'@Concurrent\' can not be used on method, please use it on function declaration.

**Description**<br>
This error code is reported when @Concurrent is used to decorate methods.

**Possible Cause**<br>
The @Concurrent decorator is used to decorate methods.

**Solution**<br>
Use the @Concurrent decorator only on function declarations, not on methods.

## 10905227 The Name of a Custom Component Cannot Be the Same as That of a Built-in Component
**Error Message**<br>
The struct \'xxx\' cannot have the same name as the built-in component \'xxx\'.

**Description**<br>
This error code is reported when the name of a custom component matches the name of a built-in component.

**Possible Cause**<br>
The custom component has the same name as a built-in component.

**Solution**<br>
Rename the custom component to a name that is different from any built-in component names.

## 10905228 The Name of a Custom Component Cannot Be the Same as That of a Built-in Component Attribute Method
**Error Message**<br>
The struct \'xxx\' cannot have the same name as the built-in attribute \'xxx\'.

**Description**<br>
This error code is reported when the name of a custom component matches the name of a built-in component attribute method.

**Possible Cause**<br>
The custom component has the same name as an attribute method of a built-in component.

**Solution**<br>
Rename the custom component to a name that is different from any built-in component attribute method names.

## 10905229 Invalid Struct Decorator
**Error Message**<br>
The struct \'xxx\' can not be decorated with \'@ComponentV2\' and \'@Component\', \'@Reusable\', \'@CustomDialog\' at the same time.

**Description**<br>
This error code is reported when a struct is decorated with multiple incompatible decorators such as @ComponentV2, @Component, @Reusable, and @CustomDialog.

**Possible Cause**<br>
Multiple decorators that are not compatible with each other are used on the same struct.

**Solution**<br>
Avoid using incompatible decorators on the same struct. Use only one appropriate decorator for the struct.

## 10905230 Lack of Required Decorators for Child Components
**Error Message**<br>
Decorator \'@Component\', \'@ComponentV2\', or \'@CustomDialog\' is missing for struct \'xxx\'.

**Description**<br>
This error code is reported when a child component is not decorated with @Component, @ComponentV2, or @CustomDialog.

**Possible Cause**<br>
The child component is not decorated with @Component, @ComponentV2, or @CustomDialog.

**Solution**<br>
Make sure the child component is decorated with @Component, @ComponentV2, or @CustomDialog.

## 10905402 Invalid Use of the @Entry Decorator
**Error Message**<br>
A page configured in \'main_pages.json\' or \'build-profile.json5\' must have one and only one \'@Entry\' decorator.

**Description**<br>
This error code is reported when the @Entry decorator is missing or incorrectly used on the home page.

**Possible Cause**<br>
The home page is not decorated with the @Entry decorator.

**Solution**<br>
Make sure the home page has exactly one @Entry decorator.

## 10905231 Invalid Number of the @Entry Decorators
**Error Message**<br>
A page can't contain more than one \'@Entry\' decorator.

**Description**<br>
This error code is reported when multiple @Entry decorators are used on a single page.

**Possible Cause**<br>
Multiple @Entry decorators are used on a single page.

**Solution**<br>
Remove unnecessary @Entry decorators, making sure only one @Entry decorator is used on a page.

## 10905404 Invalid Number of the @Preview Decorators
**Error Message**<br>
A page can contain at most 10 \'@Preview\' decorators.

**Description**<br>
This error code is reported when more than 10 @Preview decorators are used on a single page.

**Possible Cause**<br>
More than 10 @Preview decorators are used on the same page.

**Solution**<br>
Remove unnecessary @Preview decorators, making sure a maximum of 10 @Preview decorators are used on a page.

## 10905232 Invalid Struct Name
**Error Message**<br>
A struct must have a name.

**Description**<br>
This error code is reported when a struct is not named.

**Possible Cause**<br>
No name is provided for the struct.

**Solution**<br>
Define a name for the struct.

## 10905233 Lack of Required Decorators for Child Components
**Error Message**<br>
Decorator \'@Component\', \'@ComponentV2\', or \'@CustomDialog\' is missing for struct \'xxx\'.

**Description**<br>
This error code is reported when a child component is not decorated with @Component, @ComponentV2, or @CustomDialog and is called by the parent component.

**Possible Cause**<br>
The child component is not decorated with @Component, @ComponentV2, or @CustomDialog.

**Solution**<br>
Make sure the child component is decorated with @Component, @ComponentV2, or @CustomDialog before calling it.

## 10905125 Incorrect Use of Multiple Decorators on the Same Member Property or Method
**Error Message**<br>
The member property or method can not be decorated by multiple decorators.

**Description**<br>
This error code is reported when multiple decorators are used on the same member property or method.

**Possible Cause**<br>
Multiple decorators are used on the same member property or method.

**Solution**<br>
Remove redundant decorators and retain only one appropriate decorator.

## 10905235 Invalid Component Name
**Error Message**<br>
The module name \'xxx\' can not be the same as the inner component name.

**Description**<br>
This error code is reported when the name of a custom component matches the name of a built-in component.

**Possible Cause**<br>
The custom component has the same name as a built-in component.

**Solution**<br>
Change the name of the custom component to a name that is different from any built-in component names.

## 10905236 Incorrect Component Use
**Error Message**<br>
UI component \'xxx\' cannot be used in this place.

**Description**<br>
This error code is reported when the ArkUI built-in component is used outside the allowed context, such as outside the @Builder or build() method.

**Possible Cause**<br>
The built-in component is used outside the @Builder or build() method, which does not meet the usage restrictions.

**Solution**<br>
Use the built-in component within the @Builder method, build() method, or page transition method.

## 10905237 Invalid Component Name
**Error Message**<br>
The struct name cannot contain reserved tag name: \'xxx\'.

**Description**<br>
This error code is reported when the name of a custom component matches the name of an existing component.

**Possible Cause**<br>
The custom component has the same name as an existing component.

**Solution**<br>
Change the name of the custom component to a valid component name that is different from the existing component name.

## 10905127 Invalid @Styles Declaration
**Error Message**<br>
Should not add return type to the function that is decorated by Styles.

**Description**<br>
This error code is reported when functions decorated with @Styles return function types.

**Possible Cause**<br>
The return value of the function decorated with @Styles is of the function type.

**Solution**<br>
Do not declare the return value of a function decorated with @Styles as a function type.

## 10905238 Invalid Struct Declaration
**Error Message**<br>
A struct declaration without the \'default\' modifier must have a name.

**Description**<br>
This error code is reported when a struct declaration without the default modifier is not named.

**Possible Cause**<br>
The struct is declared without the default modifier and is not named.

**Solution**<br>
Name the struct correctly.

## 10905128 Invalid @Extend Declaration
**Error Message**<br>
Should not add return type to the function that is decorated by Extend.

**Description**<br>
This error code is reported when functions decorated with @Extend return function types.

**Possible Cause**<br>
The return value of the function decorated with @Extend is of the function type.

**Solution**<br>
Do not declare the return value of a function decorated with @Extend as a function type.

## 10905129 Incorrect Mixed Use of @Computed and !!
**Error Message**<br>
A property decorated by \'xxx\' cannot be used with two-bind syntax.

**Description**<br>
This error code is reported when the @Computed decorator is incorrectly used with two-way binding syntax.

**Possible Cause**<br>
The @Computed decorator and two-way binding syntax are used together.

**Solution**<br>
Do not use the @Computed decorator and two-way binding syntax together.

## 10905130 Incorrect Use of @Computed on a Setter Method
**Error Message**<br>
A property decorated by \'xxx\' cannot define a set method.

**Description**<br>
This error code is reported when the @Computed decorator is used on a setter method.

**Possible Cause**<br>
The setter method is decorated using the @Computed decorator.

**Solution**<br>
Use the @Computed decorator only on a getter method.

## 10905358 !! Syntax Error
**Error Message**<br>
When the two-way binding syntax is used, do not assign a value to \'xxx\' variable \'yyy\' because the framework generates the default assignment.

**Description**<br>
This error code is reported when a value is assigned to the variable in an @Event decorated method while two-way binding syntax is used.

**Possible Cause**<br>
Two-way binding syntax is used and a value is passed to the @Event method.

**Solution**<br>
When using two-way binding syntax, do not pass values to the @Event method. The ArkUI framework will handle the default assignment.

## 10905241 Incorrect Mixed Use of @Reusable and @ReusableV2
**Error Message**<br>
The \'@Reusable\' and \'@ReusableV2\' decorators cannot be applied simultaneously.

**Description**<br>
This error code is reported when @Reusable and @ReusableV2 are used together.

**Possible Cause**<br>
Both @Reusable and @ReusableV2 are used to decorate a component.

**Solution**<br>
Do not use @Reusable and @ReusableV2 together. Choose one appropriate decorator.

## 10905242 Incorrect Use of @ReusableV2
**Error Message**<br>
\'@ReusableV2\' is only applicable to custom components decorated by \'@ComponentV2\'.

**Description**<br>
This error code is reported when @ReusableV2 is used to decorate custom components that are not decorated with @ComponentV2.

**Possible Cause**<br>
The @ReusableV2 decorator is used to decorate components that are not decorated with @ComponentV2.

**Solution**<br>
Use @ReusableV2 only with custom components decorated with @ComponentV2.

## 10905244 Incorrect Use of @ReusableV2
**Error Message**<br>
A custom component decorated with \'@Component\' cannot contain child components decorated with \'@ReusableV2\'.

**Description**<br>
This error code is reported when components decorated with @Component contain child components decorated with @ReusableV2.

**Possible Cause**<br>
A component decorated with @Component calls a child component decorated with @ReusableV2.

**Solution**<br>
Do not call components decorated with @ReusableV2 within components decorated with @Component.

## 10905245 Incorrect Use of @ReusableV2
**Error Message**<br>
A custom component decorated with \'@Reusable\' cannot contain any child components decorated with \'@ReusableV2\'.

**Description**<br>
This error code is reported when components decorated with @Reusable contain child components decorated with @ReusableV2.

**Possible Cause**<br>
A component decorated with @Reusable calls a child component decorated with @ReusableV2.

**Solution**<br>
Do not call components decorated with @ReusableV2 within components decorated with @Reusable.

## 10905246 Incorrect Use of @Reusable
**Error Message**<br>
A custom component decorated with \'@ReusableV2\' cannot contain child components decorated with \'@Reusable\'.

**Description**<br>
This error code is reported when components decorated with @ReusableV2 contain child components decorated with @Reusable.

**Possible Cause**<br>
A component decorated with @ReusableV2 calls a child component decorated with @Reusable.

**Solution**<br>
Do not call components decorated with @Reusable within components decorated with @ReusableV2.

## 10905359 Component Initialization Error
**Error Message**<br>
Property \'xxx\' must be initialized through the component constructor.

**Description**<br>
This error code is reported when the variable decorated with @Require is not initialized during parent component construction.

**Possible Cause**<br>
The variable decorated with @Require is not initialized during parent component construction.

**Solution**<br>
Initialize variables decorated with @Require when constructing the parent component.

## 10905247 Incorrect Use of @ReusableV2
**Error Message**<br>
The template attribute of the Repeat component cannot contain any custom component decorated with \'@ReusableV2\'.

**Description**<br>
This error code is reported when **Repeat.template** contains custom components decorated with @ReusableV2.

**Possible Cause**<br>
The **template** property of **Repeat** contains a custom component decorated with @ReusableV2.

**Solution**<br>
Remove the component decorated with @ReusableV2 from the template property.

## 10905248 Incorrect Use of the reuse Attribute
**Error Message**<br>
The reuse attribute is only applicable to custom components decorated with both \'@ComponentV2\' and \'@ReusableV2\'.

**Description**<br>
This error code is reported when the **reuse** attribute is incorrectly applied to components that are not properly decorated for reuse functionality.

**Possible Cause**<br>
The **reuse** attribute is not used with custom components that are decorated with both @ComponentV2 and @ReusableV2.

**Solution**<br>
Use the **reuse** attribute only for custom components decorated with both @ComponentV2 and @ReusableV2.

## 10905249 Incorrect Use of the reuseId Attribute
**Error Message**<br>
The reuseId attribute is not applicable to custom components decorated with both \'@ComponentV2\' and \'@ReusableV2\'.

**Description**<br>
This error code is reported when **reuseId** is used for custom components decorated with @ComponentV2 and @ReusableV2.

**Possible Cause**<br>
**reuseId** is used for custom components decorated with @ComponentV2 and @ReusableV2.

**Solution**<br>
Use the **reuseId** attribute in the correct scenario.

## 10905363 V1 Decorator Cannot Decorate Variables of the Function or () => void Type
**Error Message**<br>
The V1 decorator \'xxx\' cannot be applied to a Function-type variable \'yyy\'.

**Description**<br>
This error code is reported at runtime when the ArkUI state management V1 decorator is used for variables of the **Function** or **() => void** type. Since API version 23, this issue is intercepted in the compilation phase to avoid potential runtime exceptions. The ArkUI state management V1 decorators include [\@State](../../../application-dev/ui/state-management/arkts-state.md), [\@Prop](../../../application-dev/ui/state-management/arkts-prop.md), [\@Link](../../../application-dev/ui/state-management/arkts-link.md), [\@Provide](../../../application-dev/ui/state-management/arkts-provide-and-consume.md), [\@Consume](../../../application-dev/ui/state-management/arkts-provide-and-consume.md), [\@StorageLink](../../../application-dev/ui/state-management/arkts-appstorage.md#storagelink), [\@StorageProp](../../../application-dev/ui/state-management/arkts-appstorage.md#storageprop), [\@LocalStorageLink](../../../application-dev/ui/state-management/arkts-localstorage.md#localstoragelink), [\@LocalStorageProp](../../../application-dev/ui/state-management/arkts-localstorage.md#localstorageprop), [\@ObjectLink](../../../application-dev/ui/state-management/arkts-observed-and-objectlink.md).

**Possible Cause**<br>
The V1 decorator is used for a variable of the **Function** or **() => void** type.

**Solution**<br>
Delete the V1 decorator used for the variable of the **Function** or **() => void** type based on the error description.

## 10905360 Name of the @Extend Decorated Function Cannot Be the Same as an Attribute Name
**Error Message**<br>
The \'@Extend\' function cannot have the same name as the built-in style attribute \'xxx\' of the component \'yyy\'.

**Description**<br>
This error code is reported when the name of the [\@Extend](../../../application-dev/ui/state-management/arkts-extend.md) decorated function is the same as the name of a built-in attribute of the corresponding component.

**Possible Cause**<br>
You name the \@Extend decorated function of the component the same as a built-in attribute of the component.

**Solution**<br>
Modify the name of the \@Extend decorated function to ensure that it is different from the name of any built-in attribute of the component.

## 10905361 Variables Decorated with \@Env Cannot Have Initial Values
**Error Message**<br>
The \'@Env\' property cannot be specified a default value.

**Description**<br>
This error code is reported when variables decorated with [\@Env](../../../application-dev/ui/state-management/arkts-environment.md) are assigned initial values.

**Possible Cause**<br>
You assign initial values to variables decorated with \@Env.

**Solution**<br>
Avoid assigning initial values to variables decorated with \@Env.

##  10905250 \@Env Decorator Can Be Used Only in Structs Decorated with \@Component and \@ComponentV2
**Error Message**<br>
The \'@Env\' decorator can only be used in structs decorated by \'@Component\' or \'@ComponentV2\'.

**Description**<br>
This error code is reported when the \@Env decorator is used in structs other than those decorated with \@Component and \@ComponentV2.

**Possible Cause**<br>
You use the @Env decorator in a class or globally.

**Solution**<br>
Ensure that the \@Env decorator is used only in structs decorated with \@Component and \@ComponentV2.

##  10905251 \@Env Decorator Can Be Used Only to Decorate Instances of a Specific Class or Its Child Classes
**Error Message**<br>
The \'@Env\' decorator can only decorate \'WindowSizeLayoutBreakpointInfo\', \'SizeInVP\', \'Size\', \'UIEnvWindowAvoidAreaInfoPX\', \'UIEnvWindowAvoidAreaInfoVP\' classes or their child classes.

**Description**<br>
This error code is reported when the \@Env decorator is used to decorate instances of classes other than a specific class or its child classes.

**Possible Cause**<br>
You use the \@Env decorator to decorate instances of classes other than the specified type and its child classes.

**Solution**<br>
Use the \@Env decorator to decorate only instances of the specific class and its child classes.

##  10905252 Variables Decorated with \@Env Can Only Initialize the State Variables Decorated with \@Param When a Struct Decorated with \@ComponentV2 Is Constructed
**Error Message**<br>
Within structs decorated with \'@ComponentV2\', \'@Env\' can only initialize variables decorated with \'@Param\'.

**Description**<br>
This error code is reported in the following scenario: When a struct decorated with \@ComponentV2 is constructed, variables decorated with \@Env initialize state variables decorated with decorators other than \@Param.

**Possible Cause**<br>
When constructing a struct decorated with \@ComponentV2, you use variables decorated with \@Env to initialize state variables decorated with decorators other than \@Param.

**Solution**<br>
Do not use variables decorated with \@Env to initialize state variables decorated with V2 decorators other than \@Param.

## 10905253 Variables Decorated with \@Env Can Only Initialize Common Variables When a Struct Decorated with \@Component Is Constructed
**Error Message**<br>
Within structs decorated with \'@Component\', \'@Env\' can only initialize regular (non-decorated) variables.

**Description**<br>
This error code is reported in the following scenario: When a struct decorated with \@Component is constructed, variables decorated with \@Env initialize variables other than common variables.

**Possible Cause**<br>
When constructing a struct decorated with \@Component, you use variables decorated with \@Env to initialize state variables.

**Solution**<br>
When constructing a struct decorated with \@Component, do not use variables decorated with \@Env to initialize state variables.

## 10905364 Enhanced Verification on the Data Source of State Variables Decorated with \@Link
**Error Message**<br>
The type of the parent component's state variable initializing the \'@Link\' variable \'xxx\' must match the \'@Link\' variable's declared type.

**Description**<br>
This error code is reported when the data source used by the parent component to initialize the state variable decorated with \@Link in the child component is not a state variable of the corresponding type.

**Possible Cause**<br>
You use the properties of a state variable or a state variable of an incorrect type to initialize the state variables decorated with \@Link.

**Solution**<br>
Use the state variable of the corresponding type to initialize the state variables decorated with \@Link.

## 10905365 \@SyncMonitor Decorator Accepts Only Constant Strings as Parameters and Does Not Allow Variables to Be Passed
**Error Message**<br>
Only constant expressions are supported as parameters in \'@SyncMonitor\'. Variables are not allowed.

**Description**<br>
This error code is reported when the following condition is not met: The [\@SyncMonitor](../../../application-dev/ui/state-management/arkts-new-syncmonitor.md) decorator accepts only constant strings as parameters and does not allow variables to be passed.

**Possible Cause**<br>
You pass a variable, constant, or function's return value as the parameter of the \@SyncMonitor decorator.

**Solution**<br>
To ensure the certainty of the input value, pass a constant string as the parameter of the \@SyncMonitor decorator.

## 10905366 \@SyncMonitor Cannot Observe Non-existent Variables or Non-state Variables (Except in Wildcard Mode)
**Error Message**<br>
\'@SyncMonitor\' cannot observe non-existent variables or non-state variables, except in wildcard-based monitoring scenarios.

**Description**<br>
This error code is reported when the following condition is not met: \@SyncMonitor cannot observe non-existent variables or non-state variables (except in wildcard mode).

**Possible Cause**<br>
You pass a non-existent variable or a non-state variable in the parameters of the \@SyncMonitor decorator.

**Solution**<br>
Pass an existing state variable in the parameters of the \@SyncMonitor decorator.

## 10905367 Symbol '.*' Must Be Placed at the End of the String in the Wildcard-based Observation Scenario of \@SyncMonitor and \@Monitor
**Error Message**<br>
In wildcard-based monitoring scenarios with \'xxx\', the .* pattern must be placed at the end of the string.

**Description**<br>
This error code is reported when symbol '.*' is not placed at the end of the string in the wildcard-based observation scenario of \@SyncMonitor and \@Monitor.

**Possible Cause**<br>
You place symbol '.*' in an incorrect position in the wildcard-based observation scenario of \@SyncMonitor or \@Monitor.

**Solution**<br>
Place symbol '.*' at the end of the string.

## 10905368 Strict Key-Value Matching Between Parameters of the \@Env Decorator and Decorated Variable Types
**Error Message**<br>
Invalid parameter. State variables decorated with \'@Env\' of type \'xxx\' can only accept \'yyy\'.

**Description**<br>
This error code is reported when the strict key-value matching between parameters of the \@Env decorator and decorated variable types is not met.

**Possible Cause**<br>
You do pass values based on the strict key-value matching between parameters of the \@Env decorator and decorated variable types.

**Solution**<br>
Pass the correct decorator parameters based on the matching.

## 10905369 \@ComponentReuse Decorated Function Must Define Specific Parameter Types in the Struct Decorated with \@Component
**Error Message**<br>
In a struct decorated with \'@Component\', the function decorated with \'@ComponentReuse\' has the following input parameter: params : Record\<string, Object | null | undefined\>.

**Description**<br>
This error code is reported when the \@ComponentReuse decorated function does not define specific parameter types in the struct decorated with \@Component.

**Possible Cause**<br>
No parameter is defined or the parameter type is incorrect in the function decorated with \@ComponentReuse in the struct decorated with \@Component.

**Solution**<br>
Define the corresponding parameter type in the function decorated with \@ComponentReuse.

## 10905370 \@ComponentReuse Decorated Function Cannot Have Input Parameters in the Struct Decorated with \@ComponentV2
**Error Message**<br>
Methods decorated with \'@ComponentReuse\' in \'@ComponentV2\' cannot have input parameters.

**Description**<br>
This error code is reported when the \@ComponentReuse decorated function has input parameters in the struct decorated with \@ComponentV2.

**Possible Cause**<br>
You define parameters in the function decorated with \@ComponentReuse in the struct decorated with \@ComponentV2.

**Solution**<br>
Delete the defined parameters from the function decorated with \@ComponentReuse.

## 10905371 Method Decorated with a Specific Lifecycle Decorator Cannot Have Input Parameters
**Error Message**<br>
Methods decorated with \'xxx\' cannot have input parameters.

**Description**<br>
This error code is reported when the method decorated with a specific lifecycle decorator (for example, [\@ComponentRecycle](../../../application-dev/ui/state-management/arkts-custom-components-new-lifecycle.md)) has input parameters.

**Possible Cause**<br>
You define parameters in the method decorated with a specific lifecycle decorator.

**Solution**<br>
Delete the defined parameters from the function decorated with a specific lifecycle decorator.

## 10905372 Value Passed to enableWildcard Must Be a Boolean Keyword When \@Monitor Uses Wildcards
**Error Message**<br>
The value of 'enableWildcard' must be a Boolean keyword.

**Description**<br>
This error code is reported when the value passed to **enableWildcard** is not a Boolean keyword.

**Possible Cause**<br>
When \@Monitor uses wildcards, you pass a non-Boolean keyword value to the **enableWildcard** attribute.

**Solution**<br>
Use the true or false keyword for the **enableWildcard** attribute.

## 10905373 poolAccepts Cannot Accept a Non-reusable Component After Global Reuse Is Enabled
**Error Message**<br>
\'xxx\' is not a \'@Reusable\' or \'@ReusableV2\' component and cannot be added to poolAccepts.

**Description**<br>
This error code is reported when the **poolAccepts** attribute cannot accept a non-reuse component after global reuse is enabled.

**Possible Cause**<br>
After global reuse is enabled, a non-reusable component is passed to the **poolAccepts** attribute.

**Solution**<br>
When global reuse is used, only reused components can be passed to **poolAccepts**.

## 10905374 Component Itself Cannot Be Passed in poolAccepts After Global Reuse Is Enabled
**Error Message**<br>
\'xxx\' cannot list itself in poolAccepts. The pool is not yet ready when \'xxx\' is being constructed.

**Description**<br>
This error code is reported when a component itself cannot be passed in the **poolAccepts** attribute after global reuse is enabled because the reuse pool is not ready during component build.

**Possible Cause**<br>
After global reuse is enabled, the component itself is passed in the **poolAccepts** attribute.

**Solution**<br>
When global reuse is used, do not pass the component itself in **poolAccepts**.

## 10905375 reusePool and poolAccepts Must Be Passed When Global Reuse Is Enabled for the Component
**Error Message**<br>
\'xxx\' must provide both reusePool and poolAccepts. Neither can be omitted when using the global reuse pool.

**Description**<br>
This error code is reported when **reusePool** and **poolAccepts** are not both passed at the same time for the global reuse pool.

**Possible Cause**<br>
Only one of the **reusePool** and **poolAccepts** attributes is passed when you use the global reuse pool.

**Solution**<br>
Pass both **reusePool** and **poolAccepts** when using the global reuse pool.

## 10905376 poolAccepts Cannot Be an Empty Array for the Global Reuse Pool
**Error Message**<br>
PoolAccepts cannot be an empty array. Provide at least one \'@Reusable\' or \'@ReusableV2\' component.

**Description**<br>
This error code is reported when **poolAccepts** is an empty array for the global reuse pool. (At least one reusable component must be passed.)

**Possible Cause**<br>
You pass an empty array to the **poolAccepts** attribute for the global reuse pool.

**Solution**<br>
Pass at least one reusable component in **poolAccepts** for the global reuse pool.

## 10905377 reusePool of the Global Reuse Pool Must Be of the Correct Type
**Error Message**<br>
ReusePool must be either \'shared\' or \'perInstance\'. The value \'xxx\' is not valid.

**Description**<br>
This error code is reported when an invalid value (such as \'xxx\') is passed in **reusePool** for the global reuse pool.

**Possible Cause**<br>
You pass an invalid value other than \'shared\' or \'perInstance\' in the **reusePool** attribute for the global reuse pool.

**Solution**<br>
Pass \'shared\' or \'perInstance\' in the **reusePool** attribute for the global reuse pool.

## 10905378 reusePool of the Global Reuse Pool Must Be a String
**Error Message**<br>
ReusePool can only accept string literal.

**Description**<br>
This error code is reported when the **reusePool** attribute of the global reuse pool is not a string.

**Possible Cause**<br>
You pass a variable, constant, or function's return value in the **reusePool** attribute of the global reuse pool.

**Solution**<br>
Ensure that the **reusePool** attribute of the global reuse pool is a string.

## 10905381 Variable Type Decorated with \@CustomEnv or \@Env Decorator Must Be Consistent with the Generic Type of the Decorator Parameter
**Error Message**<br>
The type of the property decorated with \'xxx\' must be consistent with the generic type of the key.

**Description**<br>
This error code is reported when the variable type decorated with \@CustomEnv or \@Env Decorator is inconsistent with the generic type of the decorator parameter.

**Possible Cause**<br>
The variable type decorated with the \@CustomEnv or \@Env Decorator is inconsistent with the generic type of the decorator parameter.

**Solution**<br>
Ensure that the variable type is consistent with the generic type of the decorator parameter.

## 10905382 Parameter in \@CustomEnv Must Comply with a Specific Syntax Format
**Error Message**<br>
Invalid key for \'@CustomEnv\', \'@CustomEnv\' key must be global const and created from CustomEnvKey.create\<T\>().

**Description**<br>
This error code is reported when the parameter in the \@CustomEnv decorator does not comply with a specific syntax format (constants initialized by **CustomEnvKey.create\<T\>()**).

**Possible Cause**<br>
The parameter passed in the \@CustomEnv decorator does not comply with a specific syntax format.

**Solution**<br>
Modify the parameter passed in the \@CustomEnv decorator based on the requirements of constants initialized by **CustomEnvKey.create\<T\>()**.
