---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface AnnotationDrawingStyleConfig
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface AnnotationDrawingStyleConfig
breadcrumbText: Interface AnnotationDrawingStyleConfig
description: Dynamsoft Document Viewer Documentation API Reference Interface AnnotationDrawingStyleConfig Page
permalink: /api/interface/styleinterface/annotationdrawingstyleconfig.html
---

# Interface

```typescript
interface AnnotationDrawingStyleConfig {
    rectangle?: RectangleStyle;
    ellipse?: EllipseStyle;
    polygon?: PolygonStyle;
    polyline?: PolylineStyle;
    line?: LineStyle;
    ink?: InkStyle;
    textBox?: TextBoxStyle;
    textTypewriter?: TextTypewriterStyle;
    stamp?: StampStyle;
    highlight?: HighlightStyle;
    underline?: UnderlineStyle;
    strikeout?: StrikeoutStyle;
    redaction?: RedactionStyle;
}
```

## Attributes

### rectangle

The default drawing style of rectangle annotation - see [`RectangleStyle`]({{ site.api }}interface/annotationinterface/rectanglestyle.html) for more details. If not set, this uses the default values of `RectangleStyle`.

### ellipse

The default drawing style of ellipse annotation - see [`EllipseStyle`]({{ site.api }}interface/annotationinterface/ellipsestyle.html) for more details. If not set, this uses the default values of `EllipseStyle`.

### polygon

The default drawing style of the polygon annotation - see [`PolygonStyle`]({{ site.api }}interface/annotationinterface/polygonstyle.html) for more details. If not set, this uses the default values of `PolygonStyle`.

### polyline

The default drawing style of the polyline annotation - see [`PolylineStyle`]({{ site.api }}interface/annotationinterface/polylinestyle.html) for more details. If not set, this uses the default values of `PolylineStyle`.

### line

The default drawing style of the line annotation - see [`LineStyle`]({{ site.api }}interface/annotationinterface/linestyle.html) for more details. If not set, this uses the default values of `LineStyle`.

### textBox

The default drawing style of the textbox annotation - see [`TextBoxStyle`]({{ site.api }}interface/annotationinterface/textboxstyle.html) for more details. If not set, this uses the default values of `TextBoxStyle`.

### textTypewriter

The default drawing style of the text typewriter annotation - see [`TextTypewriterStyle`]({{ site.api }}interface/annotationinterface/texttypewriterstyle.html) for more details. If not set, this uses the default values of `TextTypewriterStyle`.

### stamp

The default drawing style of the stamp annotation - see [`StampStyle`]({{ site.api }}interface/annotationinterface/stampstyle.html) for more details. If not set, this uses the default values of `StampStyle`.

### highlight

The default drawing style of the highlight annotation - see [`HighlightStyle`](/api/interface/annotationinterface/highlightstyle.md) for more details. If not set, this uses the default values of `HighlightStyle`.

### underline

The default drawing style of the underline annotation - see [`UnderlineStyle`](/api/interface/annotationinterface/underlinestyle.md) for more details. If not set, this uses the default values of `UnderlineStyle`.

### strikeout

The default drawing style of the strikeout annotation - see [`StrikeoutStyle`](/api/interface/annotationinterface/strikeoutstyle.md) for more details. If not set, this uses the default values of `StrikeoutStyle`.

### redaction

The default drawing style of redaction annotation - see [`RedactionStyle`](/api/interface/annotationinterface/redactionstyle.md) for more details. If not set, this uses the default values of `RedactionStyle`.
