# IDataSourcePrefetching

继承自[IDataSource](../arkts-components/arkts-arkui-idatasource-i.md)。实现该接口，提供具备预取能力的DataSource。

**继承/实现关系：** IDataSourcePrefetching extends [IDataSource](../arkts-components/arkts-arkui-idatasource-i.md)

**起始版本：** 12

<!--Device-unnamed-/* * Copyright (c) 2024 Huawei Device Co., Ltd. * Licensed under the Apache License, Version 2.0 (the "License"); * you may not use this file except in compliance with the License. * You may obtain a copy of the License at * *     http://www.apache.org/licenses/LICENSE-2.0 * * Unless required by applicable law or agreed to in writing, software * distributed under the License is distributed on an "AS IS" BASIS, * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. * See the License for the specific language governing permissions and * limitations under the License. */export interface IDataSourcePrefetching extends IDataSource--><!--Device-unnamed-/* * Copyright (c) 2024 Huawei Device Co., Ltd. * Licensed under the Apache License, Version 2.0 (the "License"); * you may not use this file except in compliance with the License. * You may obtain a copy of the License at * *     http://www.apache.org/licenses/LICENSE-2.0 * * Unless required by applicable law or agreed to in writing, software * distributed under the License is distributed on an "AS IS" BASIS, * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. * See the License for the specific language governing permissions and * limitations under the License. */export interface IDataSourcePrefetching extends IDataSource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IDataSourcePrefetching, BasicPrefetcher, IPrefetcher } from '@kit.ArkUI';
```

<a id="cancel"></a>
## cancel

```TypeScript
cancel?(index: number): Promise<void> | void
```

取消从数据集中预取指定的元素。该方法可以为同步，也可为异步。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSourcePrefetching-cancel?(index: number): Promise<void> | void--><!--Device-IDataSourcePrefetching-cancel?(index: number): Promise<void> | void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 取消预取数据项索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise when this API is executed asynchronously; no return value when this API is executed synchronously. The promise only indicates that the operation is completed and contains no actual return content. |

<a id="prefetch"></a>
## prefetch

```TypeScript
prefetch(index: number): Promise<void> | void
```

从数据集中预取指定的元素。该方法可以为同步，也可为异步。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSourcePrefetching-prefetch(index: number): Promise<void> | void--><!--Device-IDataSourcePrefetching-prefetch(index: number): Promise<void> | void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 预取数据项索引值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise when this API is executed asynchronously; no return value when this API is executed synchronously. The promise only indicates that the operation is completed and contains no actual return content. |

