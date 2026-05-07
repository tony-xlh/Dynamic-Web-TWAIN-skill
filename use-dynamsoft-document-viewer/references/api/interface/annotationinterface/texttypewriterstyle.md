---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface TextTypewriterStyle
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface TextTypewriterStyle
breadcrumbText: Interface TextTypewriterStyle
description: Dynamsoft Document Viewer Documentation API Reference Interface TextTypewriterStyle Page
permalink: /api/interface/annotationinterface/texttypewriterstyle.html
---

# TextTypewriterStyle

## Syntax

```typescript
interface TextTypewriterStyle {
    opacity?: number;
    textContent?: TextContent;
}
```

## Attributes

### opacity

The opacity of the whole annotation. The value range is [0,1], value which is greater than 1 will default to 1.

Default value: 1

### textContent

The text content of the text typewriter annotation. The content in the interface TextContent cannot be an empty string. Please refer to [`TextContent`]({{ site.api }}interface/annotationinterface/textcontent.html).

## Related

- [`EditViewerConstructorOptions`]({{ site.api }}interface/editviewerconstructoroptions.html)
