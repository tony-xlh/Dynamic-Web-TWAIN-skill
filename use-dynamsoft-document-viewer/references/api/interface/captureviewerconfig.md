---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CaptureViewerConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CaptureViewerConfig
breadcrumbText: Interface CaptureViewerConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface CaptureViewerConfig Page
permalink: /api/interface/captureviewerconfig.html
---

# CaptureViewerConfig

## Syntax

```typescript
interface CaptureViewerConfig {
    canvasStyle?: CanvasStyle;
    quadSelectionStyle?: QuadSelectionStyle;
    enableTorch?: boolean; 
    enableAutoCapture?: boolean;
    enableAutoDetect?: boolean;
    acceptedPolygonConfidence?: number;
    autoCaptureDelay?: number;
    maxFrameNumber?: number;
}
```

## Attributes

### canvasStyle

The style of canvas of the viewer. Please refer to [`CanvasStyle`]({{ site.api }}interface/styleinterface/canvasstyle.html).

### quadSelectionStyle

The style of rectangular selection. Please refer to [`QuadSelectionStyle`]({{ site.api }}interface/styleinterface/quadselectionstyle.html).

### enableTorch

Specify whether to turn on the flashlight.

Default value: `false`

### enableAutoCapture

Specify whether to enable automatic capture.

Default value: `false`

### enableAutoDetect

Specify whether to enable automatic border detection in video stream.

Default value: `false`

### acceptedPolygonConfidence

Specify the threshold confidence level when detecting boundaries. The value range is [0,100].

Default value: 80

### autoCaptureDelay

Specify the delay for auto capture. The unit is millisecond.

Default value: 1000

### maxFrameNumber

Specify the maximum number of frames detected per second.

Default value: 10

## Related

- [`CaptureViewerConstructorOptions`]({{ site.api }}interface/captureviewerconstructoroptions.html)
