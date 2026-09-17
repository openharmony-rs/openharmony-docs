# FormInfoFilter

The optional options used as filters to ask getFormsInfo to return formInfos from only forms that match the options.

@typedef FormInfoFilter

**Since:** 9

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## bundleName

```TypeScript
bundleName?: string
```

optional bundleName that used to ask getFormsInfo to return form infos with the same bundleName.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## supportedDimensions

```TypeScript
supportedDimensions?: Array<number>
```

optional supportedDimensions that used to ask getFormsInfo to return form infos with the same supportedDimensions. The minimum length is 1, refer to [FormDimension](arkts-form-forminfo-formdimension-e.md).

**Type:** Array&lt;number&gt;

**Since:** 12

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## supportedShapes

```TypeScript
supportedShapes?: Array<number>
```

optional supportedShapes that used to ask getFormsInfo to return form infos with the same supportedShapes. The minimum length is 1, Refer to [FormShape](arkts-form-forminfo-formshape-e.md).

**Type:** Array&lt;number&gt;

**Since:** 12

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.
