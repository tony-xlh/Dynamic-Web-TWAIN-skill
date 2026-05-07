---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface AnnotationConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface AnnotationConfig
breadcrumbText: Interface AnnotationConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface AnnotationConfig Page
permalink: /api/interface/annotationconfig.html
---

# AnnotationConfig

## Syntax

```typescript
interface AnnotationConfig {
    toolbarConfig?: ToolbarConfig;
    paletteConfig?: PaletteConfig;
    annotationSelectionStyle?: AnnotationSelectionStyle;
    inkCreateDelay?: number; 
    showOnTopWhenSelected?: boolean; 
    enableContinuousDrawing?: boolean;
    defaultStyleConfig?: AnnotationDrawingStyleConfig;
}
```

## Attributes

### toolbarConfig

The configurations of floating toolbar for annotation, please refer to [`ToolbarConfig`]({{ site.api }}interface/annotationinterface/toolbarconfig.html).

### paletteConfig

The configurations of floating palette for annotation, please refer to [`PaletteConfig`]({{ site.api }}interface/annotationinterface/paletteconfig.html).

### annotationSelectionStyle

The style of annotation selection, please refer to [`AnnotationSelectionStyle`]({{ site.api }}interface/styleinterface/annotationselectionstyle.html).

### inkCreateDelay

Specify the ink creation delay. The delay allows users to create the annotation with multiple strokes. Unit is millisecond.

Default value: 1000

[`annotationsAdded`]({{ site.api }}class/annotationmanager.html#annotationsadded) event will be triggered delay.

Only works for the built-in UI.

### showOnTopWhenSelected

Whether to show the annotation(s) on top layer when it is selected. 

Default value: `false`

### enableContinuousDrawing

Whether to continue drawing the annotation. This is invalid for the 'ink' type.

Default value: `false`

### defaultStyleConfig

The initial style configurations for each type of annotation, please refer to [`AnnotationDrawingStyleConfig`](/api/interface/styleinterface/annotationdrawingstyleconfig.md)

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)
