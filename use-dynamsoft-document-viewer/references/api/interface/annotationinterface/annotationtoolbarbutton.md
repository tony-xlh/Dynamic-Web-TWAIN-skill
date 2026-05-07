---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface AnnotationToolbarButton
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface AnnotationToolbarButton
breadcrumbText: Interface AnnotationToolbarButton
description: Dynamsoft Document Viewer Documentation API Reference Interface AnnotationToolbarButton Page
permalink: /api/interface/annotationinterface/annotationtoolbarbutton.html
---

# AnnotationToolbarButton

## Syntax

```typescript
interface AnnotationToolbarButton {
    id?: string; 
    className?: string; 
    style?: Partial<CSSStyleDeclaration>; 
    tooltip?: string; 
    displayText?: string;
    label?: string; 
}
```

## Attributes

### id

The id of Dom Element. If it is not specified, a random string will be generated.

### className

The className of CSS.

### style

The style which will cover CSS.

### tooltip

The tooltip of the button. 

### displayText

The display text of the button.

### label

The display text of the button. (use display text instead)

## Related

- [`ToolbarConfig`]({{ site.api }}interface/annotationinterface/toolbarconfig.html)