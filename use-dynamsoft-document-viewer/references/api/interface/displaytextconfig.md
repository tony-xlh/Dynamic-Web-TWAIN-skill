---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface DisplayTextConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface DisplayTextConfig
breadcrumbText: Interface DisplayTextConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface DisplayTextConfig Page
permalink: /api/interface/displaytextconfig.html
---

# DisplayTextConfig

## Syntax

```typescript
interface DisplayTextConfig {
    FitMode_FitWidth?: string;
    FitMode_FitHeight?: string;
    FitMode_FitWindow?: string;
    FitMode_ActualSize?: string;
    DisplayMode_SinglePage?: string;
    DisplayMode_ContinuousPage?: string;
    Crop_CropAll?: string;
    Crop_CropCurrent?: string;
    Crop_CropCancel?: string;
    Crop_CropApply?: string;
    Filter_FilterAll?: string;
    Delete_DeleteCurrent?: string;
    Delete_DeleteAll?: string;
    CameraResolution_720P?: string;
    CameraResolution_1080P?: string;
    CameraResolution_1440P?: string;
    CameraResolution_2160P?: string;
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
    RedactionSet_RedactionMode?: string;
    RedactionSet_RedactionApply?: string;
    RedactionSet_RedactPages?: string;
    RedactPages_Current?: string;
    RedactPages_Specific?: string;
    RedactPages_Ok?: string;
    RedactPages_Cancel?: string;
}
```

## Remark

- Some of built-in elements have default display texts.

    Elements                    | Default Text         
    ----------------------------|----------------------
    FitMode_FitWidth            | "Fit Width"          
    FitMode_FitHeight           | "Fit Height"         
    FitMode_FitWindow           | "Fit Window"         
    FitMode_ActualSize          | "Actual Size"        
    DisplayMode_SinglePage      | "Single Page"            
    DisplayMode_ContinuousPage  | "Enable Scrolling"   
    Crop_CropAll                | "Crop all pages"     
    Crop_CropCurrent            | "Crop current page"  
    Crop_CropCancel             | "Cancel"             
    Crop_CropApply              | "Apply"              
    Filter_FilterAll            | "Apply to all"       
    Delete_DeleteCurrent        | "Delete current"     
    Delete_DeleteAll            | "Delete all"         
    Capture                     | "Capture"  
    CameraResolution_720P       | "720P"
    CameraResolution_1080P      | "1080P"
    CameraResolution_1440P      | "1440P"
    CameraResolution_2160P      | "2160P"
    AnnotationSet               | "Annotation"
    RedactionSet_RedactionMode  | "Mark Areas for Redaction"
	RedactionSet_RedactPages    | "Mark Pages for Redaction"
    RedactionSet_RedactionApply | "Apply Redactions"
	RedactPages_Current         | "Mark current page for redaction"
	RedactPages_Specific        | "Mark specific page range for redaction"
	RedactPages_Ok              | "OK"
	RedactPages_Cancel          | "Cancel"

## Related

- [`getDisplayTextConfig()`]({{ site.api }}namespace/ddv_elements.html#static-getdisplaytextconfig)
- [`setDisplayTextConfig()`]({{ site.api }}namespace/ddv_elements.html#static-setdisplaytextconfig)
