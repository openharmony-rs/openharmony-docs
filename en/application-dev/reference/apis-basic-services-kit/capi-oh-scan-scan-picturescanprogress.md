# Scan_PictureScanProgress
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

## Overview

Defines the progress of scanning a picture by the scanner.

**Since**: 12

**Related module**: [OH_Scan](capi-oh-scan.md)

**Header file**: [ohscan.h](capi-ohscan-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t progress | Progress of scanning a picture, ranging from 0 to 100.|
| int32_t fd | Scanner file handle.|
| bool isFinal | Whether the picture is the last one to be scanned.|
