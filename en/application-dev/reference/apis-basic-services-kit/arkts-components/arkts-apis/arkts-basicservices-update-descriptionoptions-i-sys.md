# DescriptionOptions (System API)

Defines the description options, which specifies the format and language of the description file. The object contains the **format** and **language** fields. **format** indicates the description file format, which can be **STANDARD** or **SIMPLIFIED**. **language** indicates the language code, which can be **zh-cn**.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## format

```TypeScript
format: DescriptionFormat
```

Format of the description file. The value **STANDARD** is applicable to the scenario where complete description is required; **SIMPLIFIED** is applicable to the scenario where only simplified description is required.

**Type:** [DescriptionFormat](arkts-basicservices-update-descriptionformat-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## language

```TypeScript
language: string
```

Language of the description file. The value is a string of 2 to 10 characters, for example, **zh-cn** (Chinese), **en-us** (English), and **ja-jp** (Japanese). Valid characters include letters (case sensitive) and hyphens (-). Lowercase letters are recommended. An exception is thrown if the value is out of range or contains invalid characters.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
