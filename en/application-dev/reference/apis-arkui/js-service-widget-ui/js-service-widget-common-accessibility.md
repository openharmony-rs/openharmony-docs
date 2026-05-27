# Accessibility
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

You can set accessibility attributes and events for components.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## Accessibility

| Name| Type| Default Value| Description|
| -------- | -------- | -------- | -------- |
| accessibilitygroup | boolean | false | Whether to enable accessibility grouping. The value **true** means to enable accessibility grouping, and **false** means the opposite. When accessibility grouping is enabled, the component and all its children are treated as a single selectable unit, and the accessibility service will no longer focus on the individual child components.|
| accessibilitytext | string | - | Accessibility text. If a component does not contain text content, it will not be announced by the screen reader when selected. In this case, the screen reader user cannot know which component is selected. To solve this problem, you can set accessibility text for such components. When such a component is selected, the screen reader announces the specified accessibility text, informing the user which component is selected. If a component has both text content and accessibility text, only the accessibility text is announced.|
| accessibilitydescription | string | - | Accessibility description. You can specify further explanation of the current component, for example, possible operation consequences, especially those that cannot be learned from component attributes and accessibility text. You can set a detailed description text for the attribute of the component to help users understand the operation to be performed. If a component contains both text content and the accessibility description, the screen reader announces the text first, followed by the accessibility description, when the component is selected.|
| accessibilityimportance | string | auto | Accessibility importance, which is used to decide whether a component can be identified by the accessibility service. The value can be **auto**, **yes**, **no**, or **no-hide-descendants**. The last value forces the screen reader to ignore the current component and all its subcomponents. **yes**: The current component is selectable for the accessibility service. **no**: The current component cannot be selected for the barrier-free auxiliary service.|

- accessibilitygroup
  
  ```html
  <div accessibilitygroup="true">
    <text>text1</text>
    <text>text2</text>
  </div>
  ```

- accessibilitytext
  
  ```html
  <image src="common/image/barrierfree.jpg" accessibilitytext=" This is a landscape image. "></image>
  ```

- accessibilitydescription
  
  ```html
  <button accessibilitydescription="Click to open a dialog box." onclick="DialogShow">Show dialog</button>
  ```

- accessibilityimportance

  In the following example, **div** and **text** are not selected by the accessibility service. To select a component that is unselected by default, add **accessibilityimportance="yes"** to the component.

  
  ```html
  <div accessibilityimportance="no-hide-descendants">
    <text>text</text>
  </div>
  ```


## Accessibility Events

| Name| Parameter| Description|
| -------- | -------- | -------- |
| accessibility | AbilityEvent | Event dispatched by the accessibility service|

  **Table 1** AbilityEvent properties

| Name| Type| Description|
| -------- | -------- | -------- |
| eventType | number | Event type.<br>- **0**: custom event<br>- **1**: accessibility focus<br>- **2**: clear accessibility focus<br>For non-focus-related events dispatched by the accessibility system, the **eventType** value is **0**. For onfocus events dispatched by the accessibility system, the **eventType** value is **1**. For onblur events dispatched by the accessibility system, the **eventType** value is **2**.|
| param | Object | Accessibility applications need to pass corresponding parameters when sending custom events.|
