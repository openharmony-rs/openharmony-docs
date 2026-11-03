# UTransPosition

## Overview

Position structure for utrans_transIncremental() incrementaltransliteration. This structure defines two substrings of the textbeing transliterated. The first region, [contextStart,contextLimit), defines what characters the transliterator will readas context. The second region, [start, limit), defines whatcharacters will actually be transliterated. The second regionshould be a subset of the first.<p>After a transliteration operation, some of the indices in thisstructure will be modified. See the field descriptions fordetails.<p>contextStart <= start <= limit <= contextLimit<p>Note: All index values in this structure must be at code pointboundaries. That is, none of them may occur between two code unitsof a surrogate pair. If any index does split a surrogate pair,results are unspecified.

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t contextStart | Beginning index, inclusive, of the context to be considered for a transliteration operation. The transliterator will ignore anything before this index. INPUT/OUTPUT parameter: This parameter is updated by a transliteration operation to reflect the maximum amount of antecontext needed by a transliterator. |
| int32_t contextLimit | Ending index, exclusive, of the context to be considered for a transliteration operation. The transliterator will ignore anything at or after this index. INPUT/OUTPUT parameter: This parameter is updated to reflect changes in the length of the text, but points to the same logical position in the text. |
| int32_t start | Beginning index, inclusive, of the text to be transliterated. INPUT/OUTPUT parameter: This parameter is advanced past characters that have already been transliterated by a transliteration operation. |
| int32_t limit | Ending index, exclusive, of the text to be transliterated. INPUT/OUTPUT parameter: This parameter is updated to reflect changes in the length of the text, but points to the same logical position in the text. |


