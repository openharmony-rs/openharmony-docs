# UParseError

## Overview

A UParseError struct is used to returned detailed information aboutparsing errors. It is used by ICU parsing engines that parse longrules, patterns, or programs, where the text being parsed is longenough that more information than a UErrorCode is needed tolocalize the error.<p>The line, offset, and context fields are optional; parsingengines may choose not to use to use them.<p>The preContext and postContext strings include some part of thecontext surrounding the error. If the source text is "let for=7"and "for" is the error (e.g., because it is a reserved word), thensome examples of what a parser might produce are the following:<pre>preContext postContext"" "" The parser does not support context"let " "=7" Pre- and post-context only"let " "for=7" Pre- and post-context and error text"" "for" Error text only</pre><p>Examples of engines which use UParseError (or may use it in thefuture) are Transliterator, RuleBasedBreakIterator, andRegexPattern.

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t line | The line on which the error occurred. If the parser uses this field, it sets it to the line number of the source text line on which the error appears, which will be a value >= 1. If the parse does not support line numbers, the value will be <= 0. |
| int32_t offset | The character offset to the error. If the line field is >= 1, then this is the offset from the start of the line. Otherwise, this is the offset from the start of the text. If the parser does not support this field, it will have a value < 0. |
| UChar preContext[U_PARSE_CONTEXT_LEN] | Textual context before the error. Null-terminated. The empty string if not supported by parser. |
| UChar postContext[U_PARSE_CONTEXT_LEN] | The error itself and/or textual context after the error. Null-terminated. The empty string if not supported by parser. |


