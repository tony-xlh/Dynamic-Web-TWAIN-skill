---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface VideoConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface VideoConfig
breadcrumbText: Interface VideoConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface VideoConfig Page
permalink: /api/interface/videoconfig.html
---

# VideoConfig

## Syntax

```typescript
interface videoConfig {
    resolution?: [number, number];
    fill?: boolean; 
}
```

## Attributes

### resolution

The resolution of the camera video input. If the specified resolution is not exactly supported, the closest resolution will be applied.

Default value: `[1280, 720]` which means 720P.

### fill

Specify whether the video stream fills the viewer. 

Default value: `false`

## Related

- [`play()`]({{ site.api }}class/captureviewer.html#play)
