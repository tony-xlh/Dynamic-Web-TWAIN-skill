---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface DocumentDetectConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface DocumentDetectConfig
breadcrumbText: Interface DocumentDetectConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface DocumentDetectConfig Page
permalink: /api/interface/documentdetectconfig.html
---

# DocumentDetectConfig

## Syntax

```typescript
interface DocumentDetectConfig {
    acceptedPolygonConfidence?: number; 
    enableAutoCapture?: boolean; 
    autoCaptureDelay: number;  
}
```

## Attributes

### acceptedPolygonConfidence

The accepted confidence. Value range: [0, 100] in percentage.

The higher the setting, the more accurate the automatic boundaries detection.

The default value is the vaule which is set by [`CaptureViewerConfig`-`acceptedPolygonConfidence`]({{ site.api }}interface/captureviewerconfig.html#acceptedpolygonconfidence).

### enableAutoCapture

Wheter to enable auto capture. The default value is the vaule which is set by [`CaptureViewerConfig`-`enableAutoCapture`]({{ site.api }}interface/captureviewerconfig.html#enableautocapture).

### autoCaptureDelay

The delay for auto capture. The unit is millisecond. The default value is the vaule which is set by [`CaptureViewerConfig`-`autoCaptureDelay`]({{ site.api }}interface/captureviewerconfig.html#autocapturedelay).
