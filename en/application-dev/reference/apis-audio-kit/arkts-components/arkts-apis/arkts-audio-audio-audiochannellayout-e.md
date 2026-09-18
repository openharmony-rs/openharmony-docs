# AudioChannelLayout

Audio AudioChannel Layout. A 64-bit integer indicates that the appearance and order of the speakers for recording or playback.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_UNKNOWN

```TypeScript
CH_LAYOUT_UNKNOWN = 0x0
```

Unknown Channel Layout.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_MONO

```TypeScript
CH_LAYOUT_MONO = 0x4
```

Channel Layout For Mono, 1 channel in total. Speaker layout: front center(FC).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_STEREO

```TypeScript
CH_LAYOUT_STEREO = 0x3
```

Channel Layout For Stereo, 2 channels in total. Speaker layout: front left(FL), front right(FR).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_STEREO_DOWNMIX

```TypeScript
CH_LAYOUT_STEREO_DOWNMIX = 0x60000000
```

Channel Layout For Stereo-Downmix, 2 channels in total. Speaker layout: Stereo left, stereo right.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_2POINT1

```TypeScript
CH_LAYOUT_2POINT1 = 0xB
```

Channel Layout For 2.1, 3 channels in total. Speaker layout: Stereo plus low-frequency effects(LFE).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_3POINT0

```TypeScript
CH_LAYOUT_3POINT0 = 0x103
```

Channel Layout For 3.0, 3 channels in total. Speaker layout: Stereo plus back center(BC).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_SURROUND

```TypeScript
CH_LAYOUT_SURROUND = 0x7
```

Channel Layout For Surround, 3 channels in total. Speaker layout: Stereo plus FC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_3POINT1

```TypeScript
CH_LAYOUT_3POINT1 = 0xF
```

Channel Layout For 3.1, 4 channels in total. Speaker layout: Surround plus LFE.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_4POINT0

```TypeScript
CH_LAYOUT_4POINT0 = 0x107
```

Channel Layout For 4.0, 4 channels in total. Speaker layout: Surround plus BC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_QUAD

```TypeScript
CH_LAYOUT_QUAD = 0x33
```

Channel Layout For Quad, 4 channels in total. Speaker layout: Stereo plus left and right back speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_QUAD_SIDE

```TypeScript
CH_LAYOUT_QUAD_SIDE = 0x603
```

Channel Layout For Quad-Side, 4 channels in total. Speaker layout: Stereo plus left and right side speakers(SL, SR).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_2POINT0POINT2

```TypeScript
CH_LAYOUT_2POINT0POINT2 = 0x3000000003
```

Channel Layout For 2.0.2, 4 channels in total. Speaker layout: Stereo plus left and right top side speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER1_ACN_N3D

```TypeScript
CH_LAYOUT_AMB_ORDER1_ACN_N3D = 0x100000000001
```

Channel Layout For ORDER1-ACN-N3D First Order Ambisonic(FOA), 4 channels in total. First order, Ambisonic Channel Number(ACN) format, Normalization of three-D(N3D).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER1_ACN_SN3D

```TypeScript
CH_LAYOUT_AMB_ORDER1_ACN_SN3D = 0x100000001001
```

Channel Layout For ORDER1-ACN-SN3D FOA, 4 channels in total. First order, ACN format, Semi-Normalization of three-D(SN3D).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER1_FUMA

```TypeScript
CH_LAYOUT_AMB_ORDER1_FUMA = 0x100000000101
```

Channel Layout For ORDER1-FUMA FOA, 4 channels in total. First order, Furse-Malham(FuMa) format.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_4POINT1

```TypeScript
CH_LAYOUT_4POINT1 = 0x10F
```

Channel Layout For 4.1, 5 channels in total. Speaker layout: 4.0 plus LFE.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_5POINT0

```TypeScript
CH_LAYOUT_5POINT0 = 0x607
```

Channel Layout For 5.0, 5 channels in total. Speaker layout: Surround plus two side speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_5POINT0_BACK

```TypeScript
CH_LAYOUT_5POINT0_BACK = 0x37
```

Channel Layout For 5.0-Back, 5 channels in total. Speaker layout: Surround plus two back speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_2POINT1POINT2

```TypeScript
CH_LAYOUT_2POINT1POINT2 = 0x300000000B
```

Channel Layout For 2.1.2, 5 channels in total. Speaker layout: 2.0.2 plus LFE.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_3POINT0POINT2

```TypeScript
CH_LAYOUT_3POINT0POINT2 = 0x3000000007
```

Channel Layout For 3.0.2, 5 channels in total. Speaker layout: 2.0.2 plus FC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_5POINT1

```TypeScript
CH_LAYOUT_5POINT1 = 0x60F
```

Channel Layout For 5.1, 6 channels in total. Speaker layout: 5.0 plus LFE.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_5POINT1_BACK

```TypeScript
CH_LAYOUT_5POINT1_BACK = 0x3F
```

Channel Layout For 5.1-Back, 6 channels in total. Speaker layout: 5.0-Back plus LFE.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_6POINT0

```TypeScript
CH_LAYOUT_6POINT0 = 0x707
```

Channel Layout For 6.0, 6 channels in total. Speaker layout: 5.0 plus BC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_HEXAGONAL

```TypeScript
CH_LAYOUT_HEXAGONAL = 0x137
```

Channel Layout For Hexagonal, 6 channels in total. Speaker layout: 5.0-Back plus BC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_3POINT1POINT2

```TypeScript
CH_LAYOUT_3POINT1POINT2 = 0x500F
```

Channel Layout For 3.1.2, 6 channels in total. Speaker layout: 3.1 plus two top front speakers(TFL, TFR).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_6POINT0_FRONT

```TypeScript
CH_LAYOUT_6POINT0_FRONT = 0x6C3
```

Channel Layout For 6.0-Front, 6 channels in total. Speaker layout: Quad-Side plus left and right front center speakers(FLC, FRC).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_6POINT1

```TypeScript
CH_LAYOUT_6POINT1 = 0x70F
```

Channel Layout For 6.1, 7 channels in total. Speaker layout: 5.1 plus BC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_6POINT1_BACK

```TypeScript
CH_LAYOUT_6POINT1_BACK = 0x13F
```

Channel Layout For 6.1-Back, 7 channels in total. Speaker layout: 5.1-Back plus BC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_6POINT1_FRONT

```TypeScript
CH_LAYOUT_6POINT1_FRONT = 0x6CB
```

Channel Layout For 6.1-Front, 7 channels in total. Speaker layout: 6.0-Front plus LFE.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT0

```TypeScript
CH_LAYOUT_7POINT0 = 0x637
```

Channel Layout For 7.0, 7 channels in total. Speaker layout: 5.0 plus two back speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT0_FRONT

```TypeScript
CH_LAYOUT_7POINT0_FRONT = 0x6C7
```

Channel Layout For 7.0-Front, 7 channels in total. Speaker layout: 5.0 plus left and right front center speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT1

```TypeScript
CH_LAYOUT_7POINT1 = 0x63F
```

Channel Layout For 7.1, 8 channels in total. Speaker layout: 5.1 plus two back speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_OCTAGONAL

```TypeScript
CH_LAYOUT_OCTAGONAL = 0x737
```

Channel Layout For Octagonal, 8 channels in total. Speaker layout: 5.0 plus BL, BR and BC.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_5POINT1POINT2

```TypeScript
CH_LAYOUT_5POINT1POINT2 = 0x300000060F
```

Channel Layout For 5.1.2, 8 channels in total. Speaker layout: 5.1 plus two top side speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT1_WIDE

```TypeScript
CH_LAYOUT_7POINT1_WIDE = 0x6CF
```

Channel Layout For 7.1-Wide, 8 channels in total. Speaker layout: 5.1 plus left and right front center speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT1_WIDE_BACK

```TypeScript
CH_LAYOUT_7POINT1_WIDE_BACK = 0xFF
```

Channel Layout For 7.1-Wide, 8 channels in total. Speaker layout: 5.1-Back plus left and right front center speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER2_ACN_N3D

```TypeScript
CH_LAYOUT_AMB_ORDER2_ACN_N3D = 0x100000000002
```

Channel Layout For ORDER2-ACN-N3D Higher Order Ambisonics(HOA), 9 channels in total. Second order, ACN format, N3D.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER2_ACN_SN3D

```TypeScript
CH_LAYOUT_AMB_ORDER2_ACN_SN3D = 0x100000001002
```

Channel Layout For ORDER2-ACN-SN3D HOA, 9 channels in total. Second order, ACN format, SN3D.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER2_FUMA

```TypeScript
CH_LAYOUT_AMB_ORDER2_FUMA = 0x100000000102
```

Channel Layout For ORDER2-FUMA HOA, 9 channels in total. Second order, FuMa format.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_5POINT1POINT4

```TypeScript
CH_LAYOUT_5POINT1POINT4 = 0x2D60F
```

Channel Layout For 5.1.4, 10 channels in total. Speaker layout: 5.1 plus four top speakers(TFL, TFR, TBL, TBR).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT1POINT2

```TypeScript
CH_LAYOUT_7POINT1POINT2 = 0x300000063F
```

Channel Layout For 7.1.2, 10 channels in total. Speaker layout: 7.1 plus two top side speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_7POINT1POINT4

```TypeScript
CH_LAYOUT_7POINT1POINT4 = 0x2D63F
```

Channel Layout For 7.1.4, 12 channels in total. Speaker layout: 7.1 plus four top speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_10POINT2

```TypeScript
CH_LAYOUT_10POINT2 = 0x180005737
```

Channel Layout For 10.2, 12 channels in total. Speaker layout: FL, FR, FC, TFL, TFR, BL, BR, BC, SL, SR, wide left(WL), and wide right(WR).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_9POINT1POINT4

```TypeScript
CH_LAYOUT_9POINT1POINT4 = 0x18002D63F
```

Channel Layout For 9.1.4, 14 channels in total. Speaker layout: 7.1.4 plus two wide speakers(WL, WR).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_9POINT1POINT6

```TypeScript
CH_LAYOUT_9POINT1POINT6 = 0x318002D63F
```

Channel Layout For 9.1.6, 16 channels in total. Speaker layout: 9.1.4 plus two top side speakers.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_HEXADECAGONAL

```TypeScript
CH_LAYOUT_HEXADECAGONAL = 0x18003F737
```

Channel Layout For Hexadecagonal, 16 channels in total. Speaker layout: Octagonal plus two wide speakers, six top speakers(TFL, TFR, TFC, TBL, TBR, TBC).

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER3_ACN_N3D

```TypeScript
CH_LAYOUT_AMB_ORDER3_ACN_N3D = 0x100000000003
```

Channel Layout For ORDER3-ACN-N3D HOA, 16 channels in total. Third order, ACN format, N3D.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER3_ACN_SN3D

```TypeScript
CH_LAYOUT_AMB_ORDER3_ACN_SN3D = 0x100000001003
```

Channel Layout For ORDER3-ACN-SN3D HOA, 16 channels in total. Third order, ACN format, N3D.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core

## CH_LAYOUT_AMB_ORDER3_FUMA

```TypeScript
CH_LAYOUT_AMB_ORDER3_FUMA = 0x100000000103
```

Channel Layout For ORDER3-FUMA HOA, 16 channels in total. Third order, FuMa format.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Core
