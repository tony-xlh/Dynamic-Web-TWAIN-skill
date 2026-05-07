---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface DDVError
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface DDVError
breadcrumbText: Interface DDVError
description: Dynamsoft Document Viewer Documentation API Reference Interface DDVError Page
permalink: /api/interface/ddverror.html
---

# DDVError

## Syntax

```typescript
interface DDVError {
    message: string;
    cause: VError;
}
```

## Attributes

### message

The error or warning message.

### cause

The specific original cause of the error or warning. Please refer to [`VError`]({{ site.api }}interface/verror.html).

## Related

- [`lastError`]({{ site.api }}namespace/ddv.html#static-lasterror)
- [`clearLastError()`]({{ site.api }}namespace/ddv.html#static-clearlasterror)