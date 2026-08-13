# @system.storage(数据存储)

/*
 Copyright (c) 2022 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /
 > **说明：**
 >
 > - 模块维护策略：
 >
 > - 对于Lite Wearable设备类型，该模块长期维护，可正常使用。
 >
 > - 对于支持该模块的其他设备类型，该模块从API version 6开始不再维护，可以使用模块[`@ohos.data.storage`](arkts-data-storage.md#@ohos.data.storage)。在API
 > version 9后，推荐使用新模块[`@ohos.data.preferences`](arkts-data-preferences.md#@ohos.data.preferences)。
 >
 > - 本模块接口仅可在FA模型下使用。
 >
 > - 在以下内容中，对于Lite Wearable设备类型，请参考“JS示例”；对于支持该模块的其他设备类型，请参考“ArkTS示例”。
 ###### storage.get
 get(options: GetStorageOptions): void
 通过索引读取缓存中存储的值。
 **系统能力：**  SystemCapability.DistributedDataManager.Preferences.Core.Lite
 **参数：**
 | 参数名  | 类型                    | 必填 | 说明       |
 | ------- | -------------------- | ---- | ---------- |
 | options | [GetStorageOptions](arkts-arkdata-system-storage-getstorageoptions-i.md#GetStorageOptions) | 是   | 接口配置信息。 |
 **示例：**
 ArkTS示例：
 ```js
 export default {
 storageGet() {
 storage.get({
 key: 'storage_key',
 success: function(data) {
 console.info('call storage.get success: ' + data);
 },
 fail: function(data, code) {
 console.error('call storage.get fail, code: ' + code + ', data: ' + data);
 },
 complete: function() {
 console.info('call complete');
 },
 });
 }
 }
 ```
 JS示例：
 ```xml
 <!-- xxx.hml -->
 <div class="container">
 <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
 Get Data
 </text>
 <input type="button" value="Get Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageGet"></input>
 </div>
 ```
 ```css
 /* xxx.css *\/
 .container {
 display: flex;
 flex-direction: column;
 align-items: center;
 left: 0px;
 top: 0px;
 width: 454px;
 height: 454px;
 }
 .title {
 font-size: 100px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 .button {
 font-size: 30px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 ```
 ```js
 // xxx.js
 import storage from '@system.storage';
 export default {
 data: {
 fontSize: '30px',
 fontColor: '#FF1AFF00',
 },
 storageGet() {
 storage.get({
 key: 'storage_key',
 success: function(data) {
 console.info('call storage.get success: ' + data);
 },
 fail: function(data, code) {
 console.error('call storage.get fail, code: ' + code + ', data: ' + data);
 }
 });
 },
 }
 ```
 ###### storage.set
 set(options: SetStorageOptions): void
 修改缓存中索引对应的值。
 **系统能力：**  SystemCapability.DistributedDataManager.Preferences.Core.Lite
 **参数：**
 | 参数名  | 类型                   | 必填 | 说明       |
 | ------- | ------------------- | ---- | ---------- |
 | options | [SetStorageOptions](arkts-arkdata-system-storage-setstorageoptions-i.md#SetStorageOptions) | 是   | 接口配置信息。 |
 **示例：**
 ArkTS示例：
 ```js
 export default {
 storageSet() {
 storage.set({
 key: 'storage_key',
 value: 'storage value',
 success: function() {
 console.info('call storage.set success.');
 },
 fail: function(data, code) {
 console.error('call storage.set fail, code: ' + code + ', data: ' + data);
 },
 });
 }
 }
 ```
 JS示例：
 ```xml
 <!-- xxx.hml -->
 <div class="container">
 <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
 Set Data
 </text>
 <input type="button" value="Set Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageSet"></input>
 </div>
 ```
 ```css
 /* xxx.css *\/
 .container {
 display: flex;
 flex-direction: column;
 align-items: center;
 left: 0px;
 top: 0px;
 width: 454px;
 height: 454px;
 }
 .title {
 font-size: 100px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 .button {
 font-size: 30px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 ```
 ```js
 // xxx.js
 import storage from '@system.storage';
 export default {
 data: {
 fontSize: '30px',
 fontColor: '#FF1AFF00',
 },
 storageSet() {
 storage.set({
 key: 'storage_key',
 value: 'test_storage_value',
 success: function() {
 console.info('call storage.set success.');
 },
 fail: function(data, code) {
 console.error('call storage.set fail, code: ' + code + ', data: ' + data);
 },
 });
 }
 }
 ```
 ###### storage.clear
 clear(options?: ClearStorageOptions): void
 清空缓存中存储的键值对。
 **系统能力：**  SystemCapability.DistributedDataManager.Preferences.Core.Lite
 **参数：**
 | 参数名  | 类型                                        | 必填 | 说明           |
 | ------- | ------------------------------------------- | ---- | -------------- |
 | options | [ClearStorageOptions](arkts-arkdata-system-storage-clearstorageoptions-i.md#ClearStorageOptions) | 否   | 接口配置信息。 |
 **示例：**
 ArkTS示例：
 ```js
 export default {
 storageClear() {
 storage.clear({
 success: function() {
 console.info('call storage.clear success.');
 },
 fail: function(data, code) {
 console.error('call storage.clear fail, code: ' + code + ', data: ' + data);
 },
 });
 }
 }
 ```
 JS示例：
 ```xml
 <!-- xxx.hml -->
 <div class="container">
 <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
 Clear Data
 </text>
 <input type="button" value="Clear Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageClear"></input>
 </div>
 ```
 ```css
 /* xxx.css *\/
 .container {
 display: flex;
 flex-direction: column;
 align-items: center;
 left: 0px;
 top: 0px;
 width: 454px;
 height: 454px;
 }
 .title {
 font-size: 100px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 .button {
 font-size: 30px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 ```
 ```js
 // xxx.js
 import storage from '@system.storage';
 export default {
 data: {
 fontSize: '30px',
 fontColor: '#FF1AFF00',
 },
 storageClear() {
 storage.clear({
 success: function() {
 console.info('call storage.clear success.');
 },
 fail: function(data, code) {
 console.error('call storage.clear fail, code: ' + code + ', data: ' + data);
 },
 });
 }
 }
 ```
 ###### storage.get
 get(options: GetStorageOptions): void
 ###### storage.delete
 delete(options: DeleteStorageOptions): void
 删除缓存中索引对应的键值对。
 **系统能力：**  SystemCapability.DistributedDataManager.Preferences.Core.Lite
 **参数：**
 | 参数名  | 类型                                          | 必填 | 说明           |
 | ------- | --------------------------------------------- | ---- | -------------- |
 | options | [DeleteStorageOptions](arkts-arkdata-system-storage-deletestorageoptions-i.md#DeleteStorageOptions) | 是   | 接口配置信息。 |
 **示例：**
 ArkTS示例：
 ```js
 export default {
 storageDelete() {
 storage.delete({
 key: 'Storage1',
 success: function() {
 console.info('call storage.delete success.');
 },
 fail: function(data, code) {
 console.error('call storage.delete fail, code: ' + code + ', data: ' + data);
 },
 });
 }
 }
 ```
 JS示例：
 ```xml
 <!-- xxx.hml -->
 <div class="container">
 <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
 Delete Data
 </text>
 <input type="button" value="Delete Data" style="width: 240px; height: 50px; margin: 5px;" onclick="storageDelete"></input>
 </div>
 ```
 ```css
 /* xxx.css *\/
 .container {
 display: flex;
 flex-direction: column;
 align-items: center;
 left: 0px;
 top: 0px;
 width: 454px;
 height: 454px;
 }
 .title {
 font-size: 100px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 .button {
 font-size: 30px;
 text-align: center;
 width: 200px;
 height: 100px;
 }
 ```
 ```js
 // xxx.js
 import storage from '@system.storage';
 export default {
 data: {
 fontSize: '30px',
 fontColor: '#FF1AFF00',
 },
 storageDelete() {
 storage.delete({
 key: 'storage_key',
 success: function() {
 console.info('call storage.delete success.');
 },
 fail: function(data, code) {
 console.error('call storage.delete fail, code: ' + code + ', data: ' + data);
 },
 });
 }
 }
 ```


## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Storage](arkts-arkdata-system-storage-storage-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ClearStorageOptions](arkts-arkdata-system-storage-clearstorageoptions-i.md) |  |
| [DeleteStorageOptions](arkts-arkdata-system-storage-deletestorageoptions-i.md) |  |
| [GetStorageOptions](arkts-arkdata-system-storage-getstorageoptions-i.md) |  |
| [SetStorageOptions](arkts-arkdata-system-storage-setstorageoptions-i.md) |  |

