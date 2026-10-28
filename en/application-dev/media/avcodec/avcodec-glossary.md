# Glossary

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @rchdlee; @mr-chencxy-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=76c7e58f88d458a2eed1c860a204064aa189ef85 translatedAt=2026-10-22T03:56:51.709Z pushedAt=2026-10-22T12:38:49.316Z nl=1 -->

## A

### Advanced Audio Coding (AAC)

A widely used lossy audio compression encoding format. It leverages the characteristics of human hearing to remove inaudible or insensitive sounds, and then applies entropy encoding to reduce the remaining data, making it a perceptual audio encoding format. It is commonly used for audio compression, storage, and transmission in scenarios such as music and calls.

### Advanced Video Coding (AVC/H.264)

A mainstream video compression coding standard (AVC and H.264 are two names for the same standard) that strikes a balance between compression efficiency and implementation complexity. It is one of the most commonly used video encoding formats today.

### Annex B

A byte stream encapsulation format for H.264/AVC and H.265/HEVC bitstreams, which uses start codes (00 00 01 or 00 00 00 01) to delimit individual NALUs. It is the bitstream input format supported by video decoders.

### Asynchronous Mode

A running mechanism of a codec. Input/output buffers are obtained asynchronously through callbacks, and the codec proactively notifies the application when data is ready. It applies to most codec scenarios and is recommended.

## B

### B Frame

A frame type in video encoding that supports bidirectional prediction. It references both preceding and following encoded frames for prediction, which significantly reduces temporal redundancy and improves the compression ratio. However, because it needs to reference subsequent frames, it increases end-to-end latency.

### Bitrate

The data volume of the encoded bitstream per second, in bps. It measures the degree of compression and directly affects image quality and bandwidth/storage usage.

### Bitrate Control Mode

The strategy used by a video encoder to control the output bitrate, determining how to balance bitrate, image quality, and content complexity. Supported control modes include `CBR`, `VBR`, `CQ`, `SQR`, and `CBRHQ`.

### Bitstream

A continuous audio/video data stream formed after encoding and compression. It is the output of the encoder and the input of the decoder, and must be encapsulated before it can become a playable file.

### Buffer Mode

A data path mode of a codec. An application directly reads and writes raw pixel or PCM data through the buffer (AVBuffer) provided by the codec. It is suitable for scenarios that require frame-by-frame processing, such as video editing and raw data saving.

## C

### Capability Query

A mechanism for obtaining the codecs supported by the platform and their specifications (such as software/hardware decoding, resolution range, and bitrate control mode) through the capability query API before creating a codec, so as to select a codec that meets the requirements and configure parameters correctly.

### CBR High Quality (CBRHQ)

An enhanced rate control mode of CBR that provides better image quality while keeping the bitrate constant. It supports only H.265 (HEVC) encoding and automatically falls back to CBR when the platform does not support it.

### Channel Layout

A specification that describes the number, spatial arrangement, and semantic relationships of channels in multichannel audio, such as mono, stereo, 5.1, and 7.1 configurations.

### Codec

A functional unit that implements audio/video encoding or decoding. An application creates an instance by media type or codec name and drives it to compress or restore data.

### Common Encryption (CENC)

A common encryption specification defined by MPEG (ISO/IEC 23001-7) that describes the encryption information of media samples (such as the algorithm, key identifier, and sub-sample division), allowing the same encrypted content to be adapted to different DRM systems.

### Constant Bitrate (CBR)

A rate control mode in which the encoder keeps the output bitrate as constant as possible, producing a stable and predictable bitstream. It is suitable for scenarios that require high bandwidth stability, such as low-latency and real-time interaction.

### Constant Quality (CQ)

A rate control mode that aims to keep the encoding quality constant. It requires configuring a quality parameter and is suitable for scenarios that demand high quality consistency without strictly constraining the bitrate.

### Crop

A rectangular area defined by top, bottom, left, and right coordinates: in a bitstream or decoded output, it is used to define the valid display area and to extract the actual valid picture from an image frame encoded at an aligned size; in pre-encoding processing, it is used to extract a specified region for encoding.

## D

### Decoded Picture Buffer (DPB)

A buffer that stores decoded frames for reference by subsequent frames. The reference frames in the buffer are classified into short-term reference frames and long-term reference frames based on their retention duration, and the buffer is cleared when an I frame is refreshed.

### Decoding Timestamp (DTS)

A timestamp that marks when a frame of data should be decoded. Together with the presentation timestamp (PTS), it controls the decoding and display timing of audio and video.

### Demuxing

The process of separating and extracting stream samples and description information, such as audio, video, and subtitles, from an encapsulated media container file. It is a prerequisite step for playback/decoding.

### Digital Rights Management (DRM)

A technical system for copyright protection, license management, and decryption control of encrypted media content. The decoder processes protected content by binding a decryption session.

### Drop Frame

A process that selectively drops input frames based on the target frame rate to reduce bandwidth consumption and implement adaptive bitrate. It can be performed proactively by pre-encoding processing before encoding, or by intelligent smooth fast decoding before decoding.

## E

### End of Stream (EOS)

A special flag indicating that all bitstream data has been fed in or output. After receiving this flag, the codec no longer accepts new input, but continues to output until the last frame.

## F

### Free Lossless Audio Codec (FLAC)

An open-source lossless audio compression encoding format that reduces file size without losing any audio information. The number of samples per frame varies with the sampling rate.

### Frame Rate

The number of frames displayed or processed per second in a video, measured in fps, which affects picture smoothness and data volume.

## G

### Group of Pictures (GOP)

A group of consecutive, independently decodable pictures in an encoded bitstream, starting from one I frame and ending before the next I frame. It is the basic component of an elementary stream.

## H

### HDR Vivid

A dynamic HDR video standard (brand name "HDR Vivid") released by the Ultra HD Video Industry Alliance (UWA, formerly the China Ultra HD Video Industry Alliance). It optimizes image quality frame by frame based on dynamic metadata, providing a wider luminance and color range. The bitstream must be identified by a dedicated marker.

### High Efficiency Video Coding (HEVC/H.265)

The high-efficiency video coding standard that succeeds H.264 (HEVC and H.265 refer to the same standard). At the same image quality, it achieves a significantly higher compression ratio than H.264 and supports 8-bit/10-bit and richer color metadata.

## I

### I frame

An intra-frame encoded frame that can be decoded independently. It serves as the reference point for random access and seeking in the bitstream, and also as the start and end point of a GOP.

### Instantaneous Decoding Refresh (IDR)

A special type of I frame (also called an instantaneous decoding refresh frame). All subsequent frames no longer reference frames before this IDR frame. When the decoder processes this frame, it clears the reference frame buffer. It is used for random access, error recovery, and restarting decoding of the bitstream.

## L

### Long-Term Reference (LTR)

A reference frame that can reside in the decoded picture buffer for a long time and is updated through marker-based replacement. It is the preferred mechanism for implementing a temporal layered bitstream structure and cross-frame reference.

## M

### Macroblock

The basic encoding processing unit in H.264/AVC, typically a 16×16 pixel block. The size of an encoded frame is aligned in units of macroblocks.

### Motion Vectors (MV)

A vector that describes inter-frame motion information during decoding. It is used for inter-frame prediction and serves as a key basis for frame dropping decisions in intelligent smooth variable-speed decoding.

### Muxing

The process of writing encoded audio, video, subtitle, and other bitstreams together with their descriptive information into a single file in a specific container format. It is the step that produces a playable media file, such as an mp4 file.

## P

### P Frame

A frame type in video encoding that is predicted by referencing only previously encoded frames. Its compression efficiency is higher than that of an I frame but lower than that of a B frame.

### Parameter Set

A set of syntax elements in a bitstream that carries the global information required for decoding, commonly including the Sequence Parameter Set (SPS), Picture Parameter Set (PPS), and Video Parameter Set (VPS).

### Pulse-Code Modulation (PCM)

An uncompressed raw digital audio data format. It is the output of audio decoding and the input of encoding, and serves as the core intermediate data form in the audio processing pipeline.

### Per-frame Parameter Channel

A parameter delivery channel bound to a specific input frame. It delivers parameters for each frame individually (such as requesting an I frame, LTR marking, and ROI), with precise effective timing, avoiding the use of the SetParameter API whose effective timing is uncertain.

### Pixel Format

A format definition that describes how the data of each pixel in an image is arranged (such as NV12, YUVI420, and RGBA), determining how the codec interprets and processes the image memory.

### Picture Order Count (POC)

The sequence number of a picture in the bitstream playback order, used to identify the display order and reference relationship of frames. It is reset to zero after an IDR frame is refreshed.

### Preprocessing

The preprocessing capability that a video encoder performs on input frames before they enter the encoding pipeline. It includes downsampling, cropping, and frame dropping, and is used to adjust the size, region, and frame rate of input frames before encoding.

### Protection System Specific Header (pssh)

DRM system-specific header information carried in a media file. It corresponds to a UUID and is used to identify the DRM system type and deliver its initialization data.

### Presentation Timestamp (PTS)

A timestamp that marks when a frame of data should be presented or displayed, used for audio-video synchronization and display timing control.

## R

### Reference Frame

An encoded frame that is used by other frames for inter prediction during encoding/decoding. Based on how long it stays in the decoded picture buffer, it is classified as a short-term reference frame or a long-term reference frame.

### Region of Interest (ROI)

A video encoding optimization technique that allocates more encoding resources to the specified key rectangular region in the frame, ensuring that the content in this region is clearly presented under limited bandwidth.

### Resolution

The pixel size specification of a video image (for example, 1920×1080), which determines the picture clarity and data volume, and is a core dimension for codec configuration and capability query.

## S

### Sample Rate

The number of times an audio signal is sampled per second, in Hz. It determines the frequency range that the audio can represent and is one of the core parameters of audio codec.

### Secure Video Path

A method of transmitting video data through a hardware-protected path after DRM decryption, preventing keys and plaintext data from being exposed to non-secure environments. Only the `Surface` mode is supported.

### Short-Term Reference (STR)

A reference frame that cannot reside in the decoded picture buffer for a long time. It is updated in a first-in-first-out manner, and its cross-frame reference span is limited.

### Smart Fluency Speed Decoding

A system capability that combines hardware decoding capability with a human-factor perception model. It accurately removes non-key frames with low visual perception weight before decoding, reducing the decoding load during high-speed playback.

### Stable Quality Rate Control (SQR)

A rate control mode that aims to maintain stable image quality. It controls encoding quality through a stable quality rate factor and a maximum bitrate, supports only H.265 (HEVC) encoding, and is suitable for scenarios that require high image quality consistency.

### Stride

The number of bytes actually occupied by each row of an image in memory (including alignment padding). It is usually not less than the number of bytes corresponding to the effective width of the image. It results from hardware memory alignment, and you must use it to copy image data correctly.

### Surface Mode

A data path mode for encoding and decoding, in which the codec directly passes input/output image frames through NativeWindow, achieving zero-copy of data within the system. It is suitable for playback, preview, and interfacing with graphics data sources such as cameras.

### Synchronous Mode

An operating mechanism of a codec. The application proactively requests input/output buffers through the `Query` interface to drive the codec process, without relying on callbacks. It is applicable to scenarios where the timing of data transmission and reception needs to be actively controlled.

## T

### Temporal Scalability

A video encoding technology that can produce temporally layered bitstreams. It uses a multi-layer reference structure to scale the frame rate by dropping frames layer by layer, providing resilience against packet loss in weak network conditions.

### Temporal Group of Pictures (TGOP)

A temporal layered unit subdivided within a GOP, composed of a base layer and one or more subsequent enhancement layers. It is the basic unit for constructing a temporal layered bitstream structure.

### Track

An independent media data stream in a media file (such as an audio track, video track, subtitle track, cover track, or auxiliary track). Each track has a unique identifier and carries one type of media data.

### Transcoding

The process of converting media data from one encoding format to another. After transcoding, the data must be re-muxed and saved.

## V

### Variable Bitrate (VBR)

A rate control mode (also referred to as dynamic bitrate in this document) in which the output bitrate varies dynamically with the complexity of the video/audio content. More complex scenes are allocated a higher bitrate. It is suitable for real-time streaming and offline encoding.

### Variable Refresh Rate (VRR)

A video playback feature that dynamically adjusts the screen refresh rate based on the video content during playback, saving screen display power while ensuring smoothness.

### Video Usability Information (VUI)

A set of auxiliary color and display information carried in an H.264/H.265 bitstream, including the YUV range, color gamut, transfer characteristics, and matrix coefficients, used to correctly restore and display picture colors.

## Y

### YUV

A color space that represents an image using a luminance component Y and chrominance components U/V. It is the raw pixel data format output by video decoding and the basic data form for video codec processing.
