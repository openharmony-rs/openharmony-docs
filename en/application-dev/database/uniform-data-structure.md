# Uniform Data Structs (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @junathuawei1; @zph000-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->


## When to Use

Uniform data structs are provided to define data of common [uniform data types](../reference/apis-arkdata/js-apis-data-uniformTypeDescriptor.md#uniformdatatype). For example, the data struct for the system-defined home screen icon (the uniform data type is **openharmony.app-item**) is provided to help you easily define the data.

Applications can directly use the uniform data structs in certain scenarios. For example, in the drag-and-drop operation across applications, you can write the data (encapsulated in a uniform struct) to be dragged to [DragEvent](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#dragevent7). The target application (application requesting the data) reads the data from **DragEvent** and parses the data in the uniform data struct. Using uniform data structs for data interaction between applications effectively reduces the development workload in your application experience.

## Uniform Data Structs

The following table lists the uniform data structs provided by the UDMF.

| Data Struct                                                                                               |       Data Type       | Description  |
|-----------------------------------------------------------------------------------------------------| :-------------------: |------|
| [PlainText](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#plaintext)                  |      'general.plain-text'        | Plain text. |
| [Hyperlink](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#hyperlink)                  |       'general.hyperlink'       | Hyperlink. |
| [HTML](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#html)                            |         'general.html'          | Rich text. |
| [OpenHarmonyAppItem](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#openharmonyappitem) | 'openharmony.app-item'    | Icon.  |
| [ContentForm](../reference/apis-arkdata/js-apis-data-uniformDataStruct.md#contentform14)            | 'general.content-form'    | Content widget.|

## How to Develop

The following describes how to use the uniform data structs to define a hyperlink and a plaint text.

The data provider can call **addRecord()** provided by the UDMF to add data records and call **getRecords()** to obtain all data records in the current data object.

1. Import the required modules.

    <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/UniformDataStructure/entry/src/main/ets/pages/UdmfInterface.ets) -->

    ``` TypeScript
    // 1. Import the unifiedDataChannel and uniformTypeDescriptor modules.
    import { uniformDataStruct, uniformTypeDescriptor, unifiedDataChannel } from '@kit.ArkData';
    import hilog from '@ohos.hilog';
    ```

2. Create a data record for a hyperlink.

3. Create a data record and add it to the unified data object.

4. Create a unified data object instance.

5. Add a data record for the **plainText**.

6. Add and obtain all data records in the current UnifiedData object.

7. Traverse each record, determine the data type, and convert the data type into a child class object to obtain the original data record.

    <!-- @[unified_data_structure](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/Udmf/UniformDataStructure/entry/src/main/ets/pages/UdmfInterface.ets) -->

    ``` TypeScript
    // 2. Create a data record for a hyperlink.
    let hyperlinkDetails: Record<string, string> = {
      'attr1': 'value1',
      'attr2': 'value2'
    }
    let hyperlink: uniformDataStruct.Hyperlink = {
      uniformDataType: 'general.hyperlink',
      url: 'www.XXX.com',
      description: 'This is the description of this hyperlink',
      details: hyperlinkDetails
    }

    // Modify the description of hyperlink.
    hyperlink.description = '...';

    // Access the object property.
    hilog.info(0xFF00, '[Sample_Udmf]', `hyperlink.url = ${hyperlink.url}`);

    // 3. Create a data record for a plain text and add it to the UnifiedData instance created.
    let plainTextDetails: Record<string, string> = {
      'attr1': 'value1',
      'attr2': 'value2'
    }
    let plainText: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is plainText textContent example',
      abstract: 'this is abstract',
      details: plainTextDetails
    }
    // 4. Create a UnifiedData instance.
    let unifiedData = new unifiedDataChannel.UnifiedData();
    let hyperlinkRecord =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.HYPERLINK, hyperlink);
    let plainTextRecord =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);

    // 5. Add a plainText data record.
    unifiedData.addRecord(hyperlinkRecord);
    unifiedData.addRecord(plainTextRecord);

    // 6. Obtain all data records in this UnifiedData instance.
    let records = unifiedData.getRecords();

    // 7. Traverse all records, determine the data type of the record, and convert the record into a child class object to obtain the original data record.
    for (let i = 0; i < records.length; i++) {
      let unifiedDataRecord = records[i] as unifiedDataChannel.UnifiedRecord;
      let record = unifiedDataRecord.getValue() as object;
      if (record != undefined) {
        // Obtain the type of each data record.
        let type: string = record['uniformDataType'];
        switch (type) {
          case uniformTypeDescriptor.UniformDataType.HYPERLINK:
            Object.keys(record).forEach(key => {
              hilog.info(0xFF00, '[Sample_Udmf]', `show records: ${key} + , value: ${record[key]}`);
            });
            break;
          case uniformTypeDescriptor.UniformDataType.PLAIN_TEXT:
            Object.keys(record).forEach(key => {
              hilog.info(0xFF00, '[Sample_Udmf]', `show records: ${key} + , value: ${record[key]}`);
            });
            break;
          default:
            break;
        }
      }
    }
    ```
