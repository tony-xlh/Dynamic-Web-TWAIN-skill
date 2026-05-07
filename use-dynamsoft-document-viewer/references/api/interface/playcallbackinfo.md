---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface PlayCallbackInfo
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface PlayCallbackInfo
breadcrumbText: Interface PlayCallbackInfo
description: Dynamsoft Document Viewer Documentation API Reference Interface PlayCallbackInfo Page
permalink: /api/interface/playcallbackinfo.html
---

# PlayCallbackInfo

## Syntax

```typescript
interface PlayCallbackInfo {
    deviceId: string;
    width: number;
    height: number; 
}
```

## Attributes

### deviceId

The ID of the currently used camera.

### width

The width (in pixels) of the video input.

### height

The height (in pixels) of the video input.

## Related

- [`selectCamera()`]({{ site.api }}class/captureviewer.html#selectcamera)