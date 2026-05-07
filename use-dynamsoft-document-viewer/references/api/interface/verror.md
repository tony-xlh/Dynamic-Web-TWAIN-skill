---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface VError
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface VError
breadcrumbText: Interface VError
description: Dynamsoft Document Viewer Documentation API Reference Interface VError Page
permalink: /api/interface/verror.html
---

# VError

## Syntax

```typescript
interface VError {
    code: number;
    message: string;
    details?: string[];
}
```

## Attributes

### code

The error code. Please refer to [Error List]({{ site.api }}errorlist.html) for the whole error codes DDV has.

### message

The error message.

### details

The detailed error info.

## Related

- [`DDVError`]({{ site.api }}interface/ddverror.html)