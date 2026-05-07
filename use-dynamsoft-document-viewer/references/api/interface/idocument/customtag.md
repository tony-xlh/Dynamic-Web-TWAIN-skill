---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface CustomTag
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface CustomTag
breadcrumbText: Interface CustomTag
description: Dynamsoft Document Viewer Documentation API Reference Interface CustomTag Page
permalink: /api/interface/idocument/customtag.html
---

# CustomTag

## Syntax

```typescript
interface CustomTag {
    id?: number;
    content?: string;
    contentIsBase64?: boolean;
}
```

## Attributes

### id

The id of the custom tag.

### content

The content of the tag. 

### contentIsBase64

Whether the content is encoded by Base64. 

## Remark

The content of the tags can be plain text or a base64-encoded string. If it’s encoded, it’ll be decoded when generating the TIFF file.

## Related

- [`SaveTiffSettings`]({{ site.api }}interface/idocument/savetiffsettings.html)