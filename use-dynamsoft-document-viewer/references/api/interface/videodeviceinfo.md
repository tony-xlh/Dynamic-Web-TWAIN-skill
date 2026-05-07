---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface VideoDeviceInfo
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface VideoDeviceInfo
breadcrumbText: Interface VideoDeviceInfo
description: Dynamsoft Document Viewer Documentation API Reference Interface VideoDeviceInfo Page
permalink: /api/interface/videodeviceinfo.html
---

# VideoDeviceInfo

## Syntax

```typescript
interface VideoDeviceInfo {
    deviceId: string; 
    label: string;
}
```

## Attributes

### deviceId

An alphanumeric string that uniquely identifies a camera.

### label

A human-readable string describing the camera.

## Related

- [`getAllCameras()`]({{ site.api }}class/captureviewer.html#getallcameras)
- [`getCurrentCameras()`]({{ site.api }}class/captureviewer.html#getcurrentcamera)
- [`selectCamera()`]({{ site.api }}class/captureviewer.html#selectcamera)