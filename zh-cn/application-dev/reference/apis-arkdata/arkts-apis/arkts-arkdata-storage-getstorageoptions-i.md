# GetStorageOptions

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-/* * Copyright (c) 2022 Huawei Device Co., Ltd. * Licensed under the Apache License, Version 2.0 (the "License"); * you may not use this file except in compliance with the License. * You may obtain a copy of the License at * *     http://www.apache.org/licenses/LICENSE-2.0 * * Unless required by applicable law or agreed to in writing, software * distributed under the License is distributed on an "AS IS" BASIS, * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. * See the License for the specific language governing permissions and * limitations under the License. */export interface GetStorageOptions--><!--Device-unnamed-/* * Copyright (c) 2022 Huawei Device Co., Ltd. * Licensed under the Apache License, Version 2.0 (the "License"); * you may not use this file except in compliance with the License. * You may obtain a copy of the License at * *     http://www.apache.org/licenses/LICENSE-2.0 * * Unless required by applicable law or agreed to in writing, software * distributed under the License is distributed on an "AS IS" BASIS, * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. * See the License for the specific language governing permissions and * limitations under the License. */export interface GetStorageOptions-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetStorageOptions-complete?: () => void--><!--Device-GetStorageOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## default

```TypeScript
default?: string
```

key不存在则返回的默认值。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetStorageOptions-default?: string--><!--Device-GetStorageOptions-default?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数，data为错误信息，code为错误码。

**类型：** (data: string, code: number) => void

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetStorageOptions-fail?: (data: string, code: number) => void--><!--Device-GetStorageOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## key

```TypeScript
key: string
```

内容索引。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetStorageOptions-key: string--><!--Device-GetStorageOptions-key: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

## success

```TypeScript
success?: (data: any) => void
```

接口调用成功的回调函数，data为返回key对应的value。

**类型：** (data: any) => void

**起始版本：** 3

**废弃版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-GetStorageOptions-success?: (data: any) => void--><!--Device-GetStorageOptions-success?: (data: any) => void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core.Lite

