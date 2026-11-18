# Crown Rotation Event Monitoring
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-12T04:26:48.150Z pushedAt=2026-11-18T02:03:13.794Z nl=1 -->

This module provides the capability of setting a crown rotation event monitor for the current page. It supports registering a page-level crown rotation event monitor, and is applicable to scenarios where crown rotation operations need to be monitored uniformly at the page level and event distribution needs to be controlled. It is supported only on devices equipped with crown rotation.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## setMonitorForCrownEvents

setMonitorForCrownEvents(handler: Function): void

Sets a crown rotation event monitor for the current page. When a crown rotation event is triggered, the monitor triggers a callback.

This monitor is automatically removed when [page routing](../js-apis-router.md) occurs, and can be manually removed using the [clearMonitorForCrownEvents](#clearmonitorforcrownevents) API.

> **NOTE**
>
> - When page routing occurs, the monitor is automatically removed. Therefore, it is recommended to call this API in the [lifecycle](../../../ui/js-framework-lifecycle.md) callback of **onShow** on the page.
> - Each page supports only one monitor. A newly registered monitor will overwrite the previous one, and the system will use the monitor passed in the last call to this API.
> - Do not use this API in [app.js](../../../ui/js-framework-js-file.md), because its behavior is undefined.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Model restriction:** This API can be used only in the FA model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| handler | Function | Yes | Callback invoked when the crown rotation event occurs. The callback format is `(event) => { return true; }` or `(event) => { return false; }`.<br>When **true** is returned, the crown rotation event is no longer distributed to the component that gains focus.<br>When **false** is returned, the crown rotation event continues to be distributed to the component that gains focus. If the callback returns **undefined** or no value, the default value is **false**.<br>The crown rotation event information can be obtained through the input parameter. For details about the event information, see **Table 1 CrownEvent object attributes**. |


**Table 1** CrownEvent

| Name | Type | Read-Only | Optional | Description |
| --------------------- | -------- | ------- |--------- |-------------------------------------- |
| timestamp | number | No | No | Timestamp, indicating the time elapsed since system startup when the event occurs.<br>Unit: ms. |
| angularVelocity | number | No | No | Rotation angular velocity, indicating the angle rotated per second.<br>The rotation angular velocity is a positive number when the crown is rotated counterclockwise, and a negative number when rotated clockwise.<br>Unit: °/s |
| degree | number | No | No | Relative rotation angle.<br>The relative rotation angle is a positive number when the crown is rotated counterclockwise, and a negative number when rotated clockwise.<br>Unit: degree.<br>Value range: [-360, 360] |


## clearMonitorForCrownEvents

clearMonitorForCrownEvents(): void

Clears the crown rotation event monitor for the current page. This API applies to scenarios where the page no longer needs to monitor crown rotation events, or where the default response of the focused component to crown rotation events needs to be restored.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Model restriction:** This API can be used only in the FA model.


## Example

### Example 1: Setting a Crown Rotation Event Monitor

This example describes how to set a crown rotation event monitor for a page through [setMonitorForCrownEvents](#setmonitorforcrownevents), and control whether the **List** component responds to the crown rotation event through the callback's return value of the monitor.

Since API version 24, the [setMonitorForCrownEvents](#setmonitorforcrownevents) and [clearMonitorForCrownEvents](#clearmonitorforcrownevents) APIs are added.
```css
/* xxx.css */
.container {
    flex-direction: column;
    width: 100%;
    margin-top: 10px;
    align-items: center;
}
.title {
    text-align: center;
    font-size: 50px;
    font-weight: 500;
    margin-left: 12px;
}

.text {
    font-size: 50px;
    font-weight: 500;
    margin-left: 200px;
}
.listItem {
    width: 100%;
    height: 100px;
    line-height: 60px;
    border-bottom: 1px solid #DEDEDE;
    font-size: 20px;
}
.btn{
    width: 380px;
    height: 100px;
    font-size: 36px;
    margin: 10px;
}
```

```html
<!-- xxx.hml -->
<div class="container">
    <text class="title">
        {{ title }}
    </text>
    <button class="btn" type="capsule" value="clearMonitor" onclick="clearMonitor"></button>
    <button class="btn" type="capsule" value="flagChange" onclick="flagChange"></button>
    <list class="list" focusable="true" scrollpage="true">
        <list-item for="{{ array }}" class="listItem">
            <text class="text">{{ $item.value }}</text>
        </list-item>
    </list>
</div>
```

```js
// xxx.js
export default {
    data: {
        title: 'TestPage',
        count: 0,
        display: true,
        array: [
            { 'value': 'TestListItem0' },
            { 'value': 'TestListItem1' },
            { 'value': 'TestListItem2' },
            { 'value': 'TestListItem3' },
            { 'value': 'TestListItem4' },
            { 'value': 'TestListItem5' },
            { 'value': 'TestListItem6' },
            { 'value': 'TestListItem7' },
            { 'value': 'TestListItem8' },
            { 'value': 'TestListItem9' },
        ],
        flag: false
    },
    onShow() {
        setMonitorForCrownEvents((event) => {
            console.info('event timestamp is: ', event.timestamp, ', angularVelocity is: ',
                event.angularVelocity);
            console.info('degree is: ', event.degree);
            return this.flag;
        });
    },
    flagChange() {
        this.flag = !this.flag;
    },
    clearMonitor() {
        clearMonitorForCrownEvents();
    }
}
```
