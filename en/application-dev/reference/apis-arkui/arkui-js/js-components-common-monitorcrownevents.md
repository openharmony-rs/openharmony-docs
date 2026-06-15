# Crown Rotation Event Monitoring

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e41ad85491f873728c46818ffcedb12c55ee2615 translatedAt=2026-06-03T02:47:32.227Z pushedAt=2026-06-03T03:09:48.530Z -->

This module provides the capability of setting a crown rotation event monitor for the current page, supporting the registration of page-level crown rotation event monitors. It is only supported on devices equipped with crown rotation.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## setMonitorForCrownEvents

setMonitorForCrownEvents(handler: Function): void

Sets a crown rotation event monitor for the current page. When a crown rotation event is triggered, the monitor triggers a callback.

This monitor is automatically removed when [page routing](../js-apis-router.md) occurs, and can be manually removed using the [clearMonitorForCrownEvents](#clearmonitorforcrownevents) API.

> **NOTE**
>
> - When page routing occurs, the monitor is automatically removed. Therefore, it is recommended to call this API in the [lifecycle](../../../ui/js-framework-lifecycle.md) callback of onShow on the page.
> - Each page supports only one monitor. A newly registered monitor will overwrite the previous one, and the system will use the monitor passed in the last call to this API.
> - Do not use this API in [app.js](../../../ui/js-framework-js-file.md), because its behavior is undefined.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Model constraint:** This API can only be used in the FA model.

**Parameters**

| Parameter Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| handler | Function | Yes | Callback executed after a crown rotation event occurs, in the format of **(event)=>{ return false/true; }**.<br/>When **true** is returned, the crown rotation event is no longer dispatched to the component that gains a focus.<br/>When **false** is returned, the crown rotation event continues to be dispatched to the component that gains a focus. If the callback's return value is abnormal, for example, **undefined** or no return value, the value **false** is used by default.<br/>The crown rotation event information can be obtained through the input parameter. For the event information, see **Table 1 CrownEvent object attributes**. |

**Table 1** CrownEvent object attributes

| Name | Type | Read-Only | Optional | Description |
| --------------------- | -------- | ------- |--------- |-------------------------------------- |
| timestamp | number | No | No | Timestamp. |
| angularVelocity | number | No | No | Rotation angular velocity, indicating the angle rotated per second.<br/>The rotation angular velocity is a positive number when the crown is rotated counterclockwise, and a negative number when rotated clockwise.<br/>Unit: degree/s |
| degree | number | No | No | Relative rotation angle.<br/>The relative rotation angle is a positive number when the crown is rotated counterclockwise, and a negative number when rotated clockwise.<br/>Unit: degree.<br/>Value range: [-360, 360] |

## clearMonitorForCrownEvents

clearMonitorForCrownEvents(): void

Clears the crown rotation event monitor for the current page.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Model restriction:** This API can be used only in the FA model.

## Example

### Example 1: Setting a crown rotation Event Monitor)

This example describes how to set a crown rotation event monitor for a page through [setMonitorForCrownEvents](#setmonitorforcrownevents), and control whether the **List** component responds to the crown rotation event through the callback's return value of the monitor.

Since API version 24, the [setMonitorForCrownEvents](#setmonitorforcrownevents) and the [clearMonitorForCrownEvents](#clearmonitorforcrownevents) APIs are added.

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
            <text class="text" onclick="toggleShow" show="{{ visible }}">{{ $item.value }}</text>
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
            console.info('event timestamp is: ', event.timeStamp, ', angularVelocity is: ',
                event.angularVelocity);
            console.info('rotate is: ', event.rotate);
            return this.flag;
        })
    },
    flagChange() {
        this.flag = !this.flag;
    },
    clearMonitor() {
        clearMonitorForCrownEvents();
    }
}
```