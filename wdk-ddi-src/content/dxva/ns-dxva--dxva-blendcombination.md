---
UID: NS.dxva._DXVA_BlendCombination
title: DXVA_BlendCombination
author: windows-driver-content
description: The DXVA_BlendCombination structure is sent by the host decoder to the accelerator to specify how a blended picture is created from a source picture and a graphic image with accompanying alpha-blending information.
old-location: display\dxva_blendcombination.htm
ms.assetid: ae711ec5-841d-49cc-a701-1fb6ecaa9a66
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: dxva.h
req.include-header: Dxva.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXVA_BlendCombination
req.alt-loc: dxva.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: DXVA_BlendCombination, DXVA_BlendCombination, *LPDXVA_BlendCombination
req.iface: 
---

# DXVA_BlendCombination structure



## -description
<p>The DXVA_BlendCombination structure is sent by the host decoder to the accelerator to specify how a blended picture is created from a source picture and a graphic image with accompanying alpha-blending information.</p>


## -syntax

````
typedef struct _DXVA_BlendCombination {
  WORD             wPictureSourceIndex;
  WORD             wBlendedDestinationIndex;
  RECT             PictureSourceRect16thPel;
  RECT             PictureDestinationRect;
  RECT             GraphicSourceRect;
  RECT             GraphicDestinationRect;
  WORD             wBlendDelay;
  BYTE             bBlendOn;
  BYTE             bWholePlaneAlpha;
  DXVA_AYUVsample2 OutsideYUVcolor;
} DXVA_BlendCombination, *LPDXVA_BlendCombination;
````


## -struct-fields
<dl>

### -field <b>wPictureSourceIndex</b>

<dd>
<p>Specifies the uncompressed surface index, as defined by the contents of the DWORD pointed to by the <b>lpInputData</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff550469">DD_BEGINMOCOMPFRAMEDATA</a> in a prior call to <a href="https://msdn.microsoft.com/0038aedc-2e4f-4d89-878f-7f6f751015cc">DdMoCompBeginFrame</a>, of the picture to be combined with the graphic. This value is 0xFFFF if back-end hardware alpha blending is in use (when the <b>bConfigBlendType</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> is 1).</p>
</dd>

### -field <b>wBlendedDestinationIndex</b>

<dd>
<p>Specifies the uncompressed surface index, as defined by the contents of the DWORD pointed to by the <b>lpInputData</b> member of DD_BEGINMOCOMPFRAMEDATA in a prior call to <b>DdMoCompBeginFrame</b>, of the combined picture to be created. This value is 0xFFFF if back-end hardware alpha blending is in use (when the <b>bConfigBlendType</b> member of DXVA_ConfigAlphaCombine is 1). </p>
<p>This value cannot be equal to <b>wPictureSourceIndex</b> unless back-end hardware alpha blending is in use.</p>
</dd>

### -field <b>PictureSourceRect16thPel</b>

<dd>
<p>Specifies the area of the source picture to be combined with the graphic image as a <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> structure. Dimensions are specified in units of one-sixteenth of the distance between sample values of the luminance component. (In other words, the members in the RECT structure are fixed-point representations that have 28 bits before the binary point and 4 bits after the binary point.) This one-sixteenth sample accuracy allows <b>PictureSourceRect16thPel</b> to contain the same accuracy as the <i>frame_centre_horizontal_offset</i> and <i>frame_centre_vertical_offset</i> pan-scan variables in MPEG-2 video.</p>
<p>If the <b>bConfigPictureResizing</b> member of DXVA_ConfigAlphaCombine is zero, all dimensions in <b>PictureSourceRect16thPel</b> must be integer multiples of 16.</p>
</dd>

### -field <b>PictureDestinationRect</b>

<dd>
<p>Specifies the area of the destination picture as a RECT structure. This will contain the area defined for the source picture by <b>PictureSourceRect16thPel</b>.</p>
<p>If the <b>bConfigPictureResizing</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> is zero, the area specified by <b>PictureDestinationRect</b> must have the same width and height as the area specified by <b>PictureSourceRect16thPel</b>. If <b>PictureDestinationRect</b> differs in size from <b>PictureSourceRect16thPel</b>, the resampling method to be applied is not specified, but must have a quality that is at least equivalent to that of bilinear resampling.</p>
</dd>

### -field <b>GraphicSourceRect</b>

<dd>
<p>Specifies the area of the source graphic image as a <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> structure. This area is combined with the part of the source picture specified by <b>PictureSourceRect16thPel</b> to create the alpha-blended picture.</p>
</dd>

### -field <b>GraphicDestinationRect</b>

<dd>
<p>Specifies the area of the destination graphic image as a <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> structure.</p>
<p>If the <b>bConfigGraphicResizing</b> member of DXVA_ConfigAlphaCombine is zero, the destination picture must have the same width and height as the area specified by <b>GraphicSourceRect</b>. If <b>GraphicDestinationRect</b> differs in size from <b>GraphicSourceRect</b>, the resampling method to be applied to the graphic image is not specified. However, the resampling method used should have a quality that is at least equivalent to a bilinear resampling of an AYUV surface that represents the blending information.</p>
</dd>

### -field <b>wBlendDelay</b>

<dd>
<p>Specifies the number of milliseconds of delay prior to the blending combination going into effect. If back-end hardware blending is in use (for example, if the <b>bConfigBlendType</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> is 1), <b>wBlendDelay</b> contains the number of milliseconds of delay prior to the blending combination going into effect. If front-end blending is in use, this member has no meaning and must be zero.</p>
</dd>

### -field <b>bBlendOn</b>

<dd>
<p>Specifies when a blending combination operation starts and stops. If back-end hardware blending is in use, blending is applied from the time specified in a blending combination operation (with <b>bBlendOn</b> equal to 1) until the execution time of a new blending combination (with <b>bBlendOn</b> equal to 1), or until the blending is disabled by a blending combination operation (with <b>bBlendOn</b> equal to zero). If back-end hardware blending is in use and <b>bBlendOn</b> is zero, the only other value in the alpha-blend combination buffer that has meaning is <b>wBlendDelay</b>. If front-end blending is in use, this member has no meaning and must be zero .</p>
</dd>

### -field <b>bWholePlaneAlpha</b>

<dd>
<p>Contains an opacity multiplier for the alpha channel of the graphic image. The value zero indicates that the graphic image is transparent (so that the graphic content has no effect on the resulting blended picture). The value 255 indicates that the graphic image uses its full sample opacity. If <b>bWholePlaneAlpha</b> is not equal to zero, the blend specified is to multiply the opacity of each location in the graphic content by (<b>bWholePlaneAlpha</b>+1)/256. For a zero value of <b>bWholePlaneAlpha</b>, the blend to use is the opacity specified in the graphic image without alteration. This must be equal to 255 if the <b>bConfigWholePlaneAlpha</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> is zero.</p>
</dd>

### -field <b>OutsideYUVcolor</b>

<dd>
<p>Indicates whether areas outside of the <b>PictureDestinationRect</b> use a constant color for blending. If so, this member specifies that color constant. The <b>OutsideYUVcolor</b> member is defined as a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563116">DXVA_AYUVsample2</a> structure. See the <b>Remarks</b> section for more information.</p>
</dd>
</dl>

## -remarks
<p>In the event that the source and destination pictures are not in 4:4:4 format, every second sample of the graphic blending information (for example, the first, third, or fifth) is applied to the subsampled source chrominance information in the vertical or horizontal direction as needed to produce the blended result.</p>

<p>The following sections show the restrictions placed on the <b>left</b>, <b>right</b>, <b>top</b>, and <b>bottom</b> members of the RECT structure.</p>

<p>The following restrictions apply to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> dimensions of <b>PictureSourceRect16thPel</b>:</p>

<p><b>left</b> and <b>top</b> must be greater than or equal to zero.</p>

<p><b>right</b> and <b>bottom</b> must be greater than or equal to <b>left</b> and <b>top</b>, respectively.</p>

<p>If <b>right</b> is equal to <b>left</b> or <b>top</b> is equal to <b>bottom</b>, all the RECT members must have the value zero indicating that the source picture is not used. This case is allowed only if the <b>bConfigOnlyUsePicDestRectArea</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> is zero.</p>

<p><b>right</b> and <b>bottom</b> must not exceed 16 times the allocated width and height, respectively, of the uncompressed source picture surface.</p>

<p>For example, if <b>PictureSourceRect16thPel</b> is used to select an entire MPEG-2 decoded picture, the <b>PictureSourceRect16thPel</b> values can be computed as follows:</p>

<p><b>left</b> = 0</p>

<p><b>top</b> = 0</p>

<p><b>right</b> = 16 X <i>horizontal_size</i></p>

<p><b>bottom</b> = 16 X <i>vertical_size</i></p>

<p>The following restrictions apply to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> dimensions for <b>PictureDestinationRect</b>:</p>

<p><b>left</b> and <b>top</b> must be greater than or equal to zero.</p>

<p><b>right</b> and <b>bottom</b> must be greater than or equal to <b>left</b> and <b>top</b>, respectively.</p>

<p>If <b>right</b> is equal to <b>left</b> or <b>top</b> is equal to <b>bottom</b> (only allowed if the <b>bConfigOnlyUsePicDestRectArea</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> is zero), all of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> members must have the value zero and <b>PictureSourceRect16thPel</b> must also specify all values having the value zero.</p>

<p>If the <b>bConfigBlendType</b> member of DXVA_ConfigAlphaCombine is zero, <b>right</b> and <b>bottom</b> must not exceed the allocated width and height, respectively, of the uncompressed destination picture surface.</p>

<p>If the <b>bConfigBlendType</b> member of DXVA_ConfigAlphaCombine is 1, <b>right</b> and <b>bottom</b> must not exceed the allocated width and height, respectively, of the source graphic surface.</p>

<p>If alpha-blend data loading uses the <b>bConfigDataType</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563129">DXVA_ConfigAlphaLoad</a> with a value of 2, the following restrictions apply to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> dimensions of <b>GraphicSourceRect</b>:</p>

<p><b>top </b>and <b>left </b>must be zero.</p>

<p><b>right</b> must be equal to the End X-coordinate minus the Start X-coordinate of the last preceding DVD SET_DAREA DCCMD, plus 1, to adjust for the differing rectangle interpretations as described in the following note in the RECT Structure Restrictions for <b>GraphicDestinationRect</b> section.</p>

<p><b>bottom</b> must be equal to the End Y-coordinate minus the Start Y-coordinate of the last preceding DVD SET_DAREA DCCMD, plus 1, to adjust for the differing rectangle interpretations.</p>

<p>If alpha-blend data loading does not use the <b>bConfigDataType</b> member of DXVA_ConfigAlphaLoad with a value of 2, the following restrictions apply to the RECT dimensions of <b>GraphicSourceRect</b>:</p>

<p><b>left</b> and <b>top</b> must be greater than or equal to zero.</p>

<p><b>right </b>and <b>bottom</b> must be greater than or equal to <b>left</b> and <b>top</b>, respectively.</p>

<p>If <b>right</b> is equal to <b>left</b> or <b>top</b> is equal to <b>bottom</b>, all the RECT members must have the value zero, indicating no use of the graphic picture. </p>

<p><b>right</b> and <b>bottom</b> must not exceed the allocated width and height, respectively, of the graphic source image. The allocated width and height are defined as 720 and 576 samples, respectively, when the <b>bConfigDataType</b> member of DXVA_ConfigAlphaLoad equals 2.</p>

<p>The following restrictions apply to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> dimensions of <b>GraphicDestinationRect</b>:</p>

<p><b>right</b> and <b>bottom</b> must be greater than or equal to <b>left</b> and <b>top</b>, respectively. If <b>right</b> is equal to <b>left</b> or <b>top</b> is equal to <b>bottom</b>, then all these members of the RECT structure must have the value zero and <b>GraphicSourceRect</b> must also specify that all its members have the value zero.</p>

<p>If the <b>bConfigBlendType</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> equals zero, <b>right</b> and <b>bottom</b> must not exceed the allocated width and height, respectively, of the uncompressed destination picture surface.</p>

<p>If the <b>bConfigBlendType</b> member of DXVA_ConfigAlphaCombine equals 1, <b>right</b> and <b>bottom</b> must not exceed the allocated width and height, respectively, of the source graphic image.</p>

<p>If alpha-blend data loading uses the <b>bConfigDataType</b> member of DXVA_ConfigAlphaCombine with a value of 2 and the <b>bConfigGraphicResizing</b> member of DXVA_ConfigAlphaCombine with a value of zero, the following additional restrictions on <b>GraphicDestinationRect</b> dimensions apply:</p>

<p><b>top</b> must be equal to the Start Y-coordinate of the last preceding DVD SET_DAREA DCCMD.</p>

<p><b>left</b> must be equal to either the Start X-coordinate of the last preceding DVD SET_DAREA DCCMD or to that value minus 8. For more information, see <a href="https://msdn.microsoft.com/df335e5e-4f7c-440a-88ef-00f6e0f916e2">DVD 704-Wide Non-Pan-Scan Example</a> and <a href="https://msdn.microsoft.com/22047c8e-30e3-4204-9f7d-b8b97be668ae">DVD 352-Wide Example</a>.</p>

<p><b>right</b> must be equal to the value of <b>left</b>, plus the End X-coordinate minus the Start X-coordinate of the last preceding DVD SET_DAREA DCCMD, plus 1, to adjust for the differing rectangle interpretations described in the following note.</p>

<p><b>bottom</b> must be equal to the value of <b>top</b> plus the End Y-coordinate minus the Start Y-coordinate of the last preceding DVD SET_DAREA DCCMD, plus 1, to adjust for the differing rectangle interpretations described in the following note.</p>

<p>The values for the <b>OutsideYUVcolor</b> structure are as follows:</p>

<p>The value of <b>OutsideYUVcolor.bSampleAlpha8</b> must be 255 if the areas outside of the <b>PictureDestinationRect</b> are generated as a constant color to use for blending.</p>

<p>All other values for <b>OutsideYUVcolor.bSampleAlpha8</b> are reserved for future use.</p>

<p>The value of <b>OutsideYUVcolor.bSampleAlpha8</b> must be zero if the <b>bConfigStayInPicDestRectArea</b> member of the DXVA_ConfigAlphaCombine structure equals 1.</p>

<p>If <b>OutsideYUVcolor.bSampleAlpha8</b> is zero, the only area of the destination surface that is affected by the blend is the part within the <b>PictureDestinationRect</b>.</p>

<p>If <b>OutsideYUVcolor.bSampleAlpha8</b> is 255, any area of the destination surface that is outside of <b>PictureDestinationRect</b> but within <b>GraphicDestinationRect</b>, is generated by blending the graphic with the color specified in the nonalpha members of <b>OutsideYUVcolor</b>. In this case, the entire allocated area of the destination surface that falls outside of both <b>PictureDestinationRect</b> and <b>GraphicDestinationRect</b> is set to the color specified in the nonalpha members of <b>OutsideYUVcolor</b>. If the <b>bConfigBlendType</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a> structure is 1, the <b>OutsideYUVcolor</b> members are set to indicate blending with black by specifying <b>bSampleAlpha8</b> = 255, <b>bY_Value</b> = 16, and <b>bCbValue</b> = <b>bCrValue</b> = 128.</p>

<p>When the <b>bConfigBlendType</b> member of the DXVA_ConfigAlphaCombine structure is 1  (back-end hardware blend), blending operations may differ somewhat from those described in this reference. Some resizing parameters used to map a video picture from a source picture to a destination picture size may be applied in a modified manner to map the graphic image to its proper location relative to the source picture. However, the blended result will be equivalent to the blended result obtained by the alpha-blend combination commands in this reference.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dxva.h (include Dxva.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563126">DXVA_ConfigAlphaCombine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550469">DD_BEGINMOCOMPFRAMEDATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563116">DXVA_AYUVsample2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/0038aedc-2e4f-4d89-878f-7f6f751015cc">DdMoCompBeginFrame</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXVA_BlendCombination structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>