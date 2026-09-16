# @system.router(页面路由)

通过不同的uri访问不同的页面。

> **说明：**
 >
 > - 从API version 8 开始，该接口不再维护，推荐使用新接口[@ohos.router](../../../reference/apis-arkui/js-apis-md)。



## 导入模块

```TypeScript
import { SystemRouter, BackRouterOptions, DisableAlertBeforeBackPageOptions, EnableAlertBeforeBackPageOptions, RouterOptions, RouterState } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Router](arkts-arkui-system-router-router-c.md) | 通过不同的uri访问不同的页面。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BackRouterOptions](arkts-arkui-system-router-backrouteroptions-i.md) | 定义路由器返回的选项。 |
| [DisableAlertBeforeBackPageOptions](arkts-arkui-system-router-disablealertbeforebackpageoptions-i.md) | 定义DisableAlertBeforeBackPage参数选项。 |
| [EnableAlertBeforeBackPageOptions](arkts-arkui-system-router-enablealertbeforebackpageoptions-i.md) | 定义EnableAlertBeforeBackPage选项。 |
| [RouterOptions](arkts-arkui-system-router-routeroptions-i.md) | 定义路由器的选项。 |
| [RouterState](arkts-arkui-system-router-routerstate-i.md) | 定义路由器的状态。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ParamsInterface](arkts-arkui-paramsinterface-t.md) | 路由参数列表。 |

## 示例

```TypeScript
该示例展示了类Web范式下router.replace接口的跳转功能。

示例树状结构如下：
```

```TypeScript
/* index.css */
.page {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #050816;
}

.page-name {
  width: 78%;
  margin-top: 10px;
  font-size: 14px;
  text-align: center;
  color: #f8fafc;
}

.tips {
  width: 82%;
  margin-top: 12px;
  font-size: 12px;
  text-align: center;
  color: #cbd5e1;
}

.status {
  width: 82%;
  margin-top: 8px;
  font-size: 12px;
  text-align: center;
  color: #94a3b8;
}

.action-button {
  width: 190px;
  height: 42px;
  margin-top: 22px;
  border-radius: 21px;
  background-color: #2563eb;
  color: #ffffff;
  font-size: 14px;
  text-align: center;
}
```

```TypeScript
<!--index.hml-->
<div class="page">
    <text class="page-name">{{ pageName }}</text>
    <text class="tips">{{ tips }}</text>
    <text class="status">{{ statusText }}</text>
    <input class="action-button" type="button" value="Replace to routerPage" onclick="replaceToRouterPage"></input>
</div>
```

```TypeScript
// index.js
import router from '@system.router';

export default {
    data: {
        pageName: 'Index Page',
        tips: 'Tap the button to replace this page.',
        statusText: 'Current page: index'
    },
    replaceToRouterPage: function() {
        router.replace({
            uri: 'pages/routerPages/routerPage',
            params: {
                data1: 'This page was opened by router.replace().'
            }
        });
    }
}
```

```TypeScript
/* routerPage.css */
.page {
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #050816;
}

.page-name {
  width: 78%;
  margin-top: 10px;
  font-size: 14px;
  text-align: center;
  color: #f8fafc;
}

.tips {
  width: 82%;
  margin-top: 12px;
  font-size: 12px;
  text-align: center;
  color: #cbd5e1;
}

.status {
  width: 82%;
  margin-top: 8px;
  font-size: 12px;
  text-align: center;
  color: #94a3b8;
}

.action-button {
  width: 190px;
  height: 42px;
  margin-top: 22px;
  border-radius: 21px;
  background-color: #16a34a;
  color: #ffffff;
  font-size: 14px;
  text-align: center;
}
```

```TypeScript
<!--routerPage.hml-->
<div class="page">
    <text class="page-name">{{ pageName }}</text>
    <text class="tips">{{ tips }}</text>
    <text class="status">{{ statusText }}</text>
    <input class="action-button" type="button" value="Replace to index" onclick="replaceToIndex"></input>
</div>
```

```TypeScript
// routerPage.js
import router from '@system.router';

export default {
    data: {
        pageName: 'Router Page',
        tips: 'Tap the button to replace this page and return home.',
        statusText: 'Current page: routerPage',
        data1: 'Waiting for router.replace params.'
    },
    onInit: function() {
        if (this.data1) {
            this.statusText = this.data1;
        }
    },
    replaceToIndex: function() {
        router.replace({
            uri: 'pages/index/index'
        });
    }
}
```
