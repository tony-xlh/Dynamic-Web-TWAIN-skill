---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface Flags
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface Flags
breadcrumbText: Interface Flags
description: Dynamsoft Document Viewer Documentation API Reference Interface Flags Page
permalink: /api/interface/annotationinterface/flags.html
---

# Flags

## Syntax

```typescript
interface Flags {
    print?: boolean;
    noMove?: boolean;
    noView?: boolean;
    noResize?: boolean;
    noRotate?: boolean;
    readOnly?: boolean;
}
```

## Attributes

### print

<!--To print the annotation when printing the page, default value: `true`.-->
Indicates whether the annotation is printable. Default value: `true`. Only printable annotations will be included when the page is printed.

### noMove

Prevents users from moving annotations.

Default value: `false`

Note: 

For the following annotations, it is not effective and the default value is `true`.

* [`Highlight`](/api/class/annotation/highlight.md)
* [`Strikeout`](/api/class/annotation/strikeout.md)
* [`Underline`](/api/class/annotation/underline.md)
* [`Redaction`](/api/class/annotation/redaction.md) (text-type)

### noView

Not to display the annotation or allow a user to interact with the annotation.

Default value: `false`

### noResize

Prevents users from resizing annotations.

Default value: `false`.

Note: 

For [`TextTypeWriter`](/api/class/annotation/texttypewriter.md), it is not effective and the default value is `true`.

### noRotate

Prevents users from rotating annotations.

Default value: `false`

Note: 

For the following annotations, it is not effective and the default value is `true`.

* [`TextTypeWriter`](/api/class/annotation/texttypewriter.md)
* [`Polyline`](/api/class/annotation/polyline.md)
* [`Polygon`](/api/class/annotation/polygon.md)
* [`Line`](/api/class/annotation/line.md)
* [`Highlight`](/api/class/annotation/highlight.md)
* [`Strikeout`](/api/class/annotation/strikeout.md)
* [`Underline`](/api/class/annotation/underline.md)
* [`Redaction`](/api/class/annotation/redaction.md)


### readOnly

Not to allow a user to interact with the annotation, default value: `false`.

## Related

- [`RectAnnotationOptions`]({{ site.api }}interface/annotationinterface/rectannotationoptions.html)
- [`EllipseAnnotationOptions`]({{ site.api }}interface/annotationinterface/ellipseannotationoptions.html)
- [`PolygonAnnotationOptions`]({{ site.api }}interface/annotationinterface/polygonannotationoptions.html)
- [`PolylineAnnotationOptions`]({{ site.api }}interface/annotationinterface/polylineannotationoptions.html)
- [`LineAnnotationOptions`]({{ site.api }}interface/annotationinterface/lineannotationoptions.html)
- [`InkAnnotationOptions`]({{ site.api }}interface/annotationinterface/inkannotationoptions.html)
- [`TextBoxAnnotationOptions`]({{ site.api }}interface/annotationinterface/textboxannotationoptions.html)
- [`TextTypewriterAnnotationOptions`]({{ site.api }}interface/annotationinterface/texttypewriterannotationoptions.html)
- [`StampAnnotationOptions`]({{ site.api }}interface/annotationinterface/stampannotationoptions.html)
- [`HighlightAnnotationOptions`](/api/interface/annotationinterface/highlightannotationoptions.md)
- [`UnderlineAnnotationOptions`](/api/interface/annotationinterface/underlineannotationoptions.md)
- [`StrikeoutAnnotationOptions`](/api/interface/annotationinterface/strikeoutannotationoptions.md)
- [`RedactionAnnotationOptions`](/api/interface/annotationinterface/redactionannotationoptions.md)
