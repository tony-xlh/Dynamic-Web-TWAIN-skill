---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer API Reference - Interface ConfigResult
keywords: Documentation, Dynamsoft Document Viewer, API Reference, Interface ConfigResult
breadcrumbText: Interface ConfigResult
description: Dynamsoft Document Viewer Documentation API Reference Interface ConfigResult Page
permalink: /api/interface/configresult.html
---

# ConfigResult

## Syntax

```typescript
interface ConfigResult {
    licenseInfo: any;
    deviceUuid?: string;
}
```

## Attributes

### licenseInfo

The license info of the configured license string.

### deviceUuid

The UUID of the client device. Please refer to [Client UUID](https://www.dynamsoft.com/license-server/docs/about/terms.html#client-uuid)

## Related

- [`init()`]({{ site.api }}namespace/ddv_core.html#init)
