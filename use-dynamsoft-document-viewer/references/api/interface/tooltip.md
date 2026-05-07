---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface Tooltip
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface Tooltip
breadcrumbText: Interface Tooltip
description: Dynamsoft Document Viewer Documentation API Reference Interface Tooltip Page
permalink: /api/interface/tooltip.html
---

# Tooltip

## Syntax

```typescript
interface Tooltip {
    CameraResolution?: string;
    Capture?: string;
    Flashlight?: string;
    CameraConvert?: string;
    AutoDetect?: string;
    AutoCapture?: string;
    Rotate?: string;
    RotateLeft?: string;
    RotateRight?: string;
    Load?: string;
    Download?: string;
    Delete?: string;
    DeleteCurrent?: string;
    DeleteAll?: string;
    Zoom?: string;
    ZoomIn?: string;
    ZoomOut?: string;
    ZoomByPercentage?: string;
    Crop?: string;
    CropAll?: string;
    CropCurrent?: string;
    CropMode?: string;
    PerspectiveAll?: string;
    FullQuad?: string;
    Undo?: string;
    Redo?: string;
    Restore?: string;
    Pan?: string;
    Filter?: string;
    Print?: string;
    ThumbnailSwitch?: string;
    DisplayMode?: string;
    ContinuousPage?: string;
    MultiPage?: string;
    SinglePage?: string;
    FitMode?: string;
    FitWidth?: string;
    FitHeight?: string;
    FitWindow?: string;
    ActualSize?: string;
    Back?: string;
    Close?: string;
    Done?: string;
    FirstPage?: string;
    LastPage?: string;
    NextPage?: string;
    PrevPage?: string;
    ImagePreview?: string;
    AnnotationSet?: string;
    EllipseAnnotation?: string;
    InkAnnotation?: string;
    LineAnnotation?: string;
    PolygonAnnotation?: string;
    PolylineAnnotation?: string;
    RectAnnotation?: string;
    StampIconAnnotation?: string;
    StampImageAnnotation?: string;
    TextBoxAnnotation?: string;
    TextTypewriterAnnotation?: string;
    SelectAnnotation?: string;
    EraseAnnotation?: string;
    HighlightAnnotation?: string;
    UnderlineAnnotation?: string;
    StrikeoutAnnotation?: string;
    BringForward?: string;
    BringToFront?: string;
    SendBackward?: string;
    SendToBack?: string;
    TextSearchPanelSwitch?: string;
    TextSelectionMode?: string;
    RedactPages?: string;
    RedactionApply?: string;
    RedactionMode?: string;
    RedactionSet?: string;
}
```

## Remark 

- The default tooltip is empty.

## Related

- [`getTooltip()`]({{ site.api }}namespace/ddv_elements.html#static-gettooltip)
- [`setTooltip()`]({{ site.api }}namespace/ddv_elements.html#static-settooltip)