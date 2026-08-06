# PrinterRange

定义打印范围的接口。

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-print-interface PrinterRange--><!--Device-print-interface PrinterRange-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## endPage

```TypeScript
endPage?: int
```

表示结束页。默认值为待打印文件的最大页数。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterRange-endPage?: int--><!--Device-PrinterRange-endPage?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pages

```TypeScript
pages?: Array<int>
```

表示待打印的页面范围的集合。默认值为空。

**类型：** Array&lt;int&gt;

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterRange-pages?: Array<int>--><!--Device-PrinterRange-pages?: Array<int>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## startPage

```TypeScript
startPage?: int
```

表示起始页。默认值为1。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterRange-startPage?: int--><!--Device-PrinterRange-startPage?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

