---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface TextTypewriterAnnotationOptions
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface TextTypewriterAnnotationOptions
breadcrumbText: Interface TextTypewriterAnnotationOptions
description: Dynamsoft Document Viewer Documentation API Reference Interface TextTypewriterAnnotationOptions Page
permalink: /api/interface/annotationinterface/texttypewriterannotationoptions.html
---

# TextTypewriterAnnotationOptions

## Syntax

```typescript
interface TextTypewriterAnnotationOptions {
    x?: number;
    y?: number;
    textContents?: TextContent[];
    opacity?: number; // The value range is [0,1], value which is greater than 1 will default to 1.
    flags?: Flags;
}
```

## Attributes

### x

The x-coordinate of the upper-left corner of the text typewriter annotation to draw.

Default value: 10

### y

The y-coordinate of the upper-left corner of the text typewriter annotation to draw.

Default value: 10

### textContents

The text contents of the text typewriter annotation. The content in the interface TextContent cannot be an empty string. Please refer to [`TextContent`]({{ site.api }}interface/annotationinterface/textcontent.html).

Default value: `[{content: "Insert text here",}]`

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1.

Default value: 1

<!--
### author

The author of annotation.

Default value: `''`

### subject

The subject of annotation.

Default value: `''`  -->

### flags

The flags of annotation.

Please refer to [`Flags`]({{ site.api }}interface/annotationinterface/flags.html).

## Related

- [`TextTypewriter()`]({{ site.api }}class/annotation/texttypewriter.html#texttypewriter)
- [`getOptions()`]({{ site.api }}class/annotation/texttypewriter.html#getoptions) under `TextTypewriter` class
- [`updateOptions()`]({{ site.api }}class/annotation/texttypewriter.html#updateoptions) under `TextTypewriter` class
