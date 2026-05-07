---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface ToolbarConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface ToolbarConfig
breadcrumbText: Interface ToolbarConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface ToolbarConfig Page
permalink: /api/interface/annotationinterface/toolbarconfig.html
---

# ToolbarConfig

## Syntax

```typescript
interface ToolbarConfig {
    enabled?: boolean;
    id?: string; 
    className?: string; // the className of CSS
    style?: CssStyleDeclaration; // the style of the toolbar
    paletteButton?: AnnotationToolbarButton;
    deleteButton?: AnnotationToolbarButton;
    copyButton?: AnnotationToolbarButton;
    highlightButton?: AnnotationToolbarButton;
    underlineButton?: AnnotationToolbarButton;
    strikeoutButton?: AnnotationToolbarButton;
    redactionApplyButton?: AnnotationToolbarButton;
}
```

## Attributes

### enabled

Whether or not the toolbar is enabled.

Default value: `true`

### id

The id of Dom Element. If it is not specified, a random string will be generated.

### className

The className of CSS.

### style

The style which will cover CSS.

### paletteButton

The configuration of palette button in the toolbar. Please refer to [`AnnotationToolbarButton`]({{ site.api }}interface/annotationinterface/annotationtoolbarbutton.html).

### deleteButton

The configuration of delete button in the toolbar. Please refer to [`AnnotationToolbarButton`]({{ site.api }}interface/annotationinterface/annotationtoolbarbutton.html).

### copyButton

The configuration of copy button in the toolbar. Please refer to [`AnnotationToolbarButton`]({{ site.api }}interface/annotationinterface/annotationtoolbarbutton.html).

### highlightButton

The configuration of highlight button in the toolbar. Please refer to [`AnnotationToolbarButton`]({{ site.api }}interface/annotationinterface/annotationtoolbarbutton.html).

### underlineButton

The configuration of underline button in the toolbar. Please refer to [`AnnotationToolbarButton`]({{ site.api }}interface/annotationinterface/annotationtoolbarbutton.html).

### strikeoutButton

The configuration of strikeout button in the toolbar. Please refer to [`AnnotationToolbarButton`]({{ site.api }}interface/annotationinterface/annotationtoolbarbutton.html).

### redactionApplyButton

The configuration of redaction application button in the toolbar. Please refer to [`AnnotationToolbarButton`](/api/interface/annotationinterface/annotationtoolbarbutton.md).

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)