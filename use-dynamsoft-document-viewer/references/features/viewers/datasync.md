---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features - Data Synchronisation between Viewers
keywords: Documentation, Dynamsoft Document Viewer, Features, Data Synchronisation between Viewers
breadcrumbText: Data Synchronisation between Viewers
description: Dynamsoft Document Viewer Documentation Features, Data Synchronisation between Viewers
permalink: /features/viewers/datasync.html
---

# Data Synchronisation between Viewers

## How to achieve

If multiple viewers are used at the same time, how to ensure that the data in different viewers is synchronized? 

In this case, you can set the same `groupUid` for each viewer when creating them. 

**Use Case**

After an edit viewer is generated, the subsequently generated perspective viewer wants to achieve data synchronization with the first edit viewer.

```typescript
const editViewer = new Dynamsoft.DDV.EditViewer({
    container: document.getElementById("viewer"),
});

const perspectiveViewer = new Dynamsoft.DDV.PerspectiveViewer({
    container: document.getElementById("viewer"),
    groupUid: editViewer.groupUid, // Set to the same groupUid of the edit viewer
});
```

Thus, the data is synchronized in the viewers which have the same `groupUid`.

## Data to synchronize

Which data will be synchronized in detail?

- Current document: In data-synchronized viewers, the current document is always consistent. That is, when a document is opened or closed in a viewer, the opening and closing document operations of other viewers in the same group are synchronized with this viewer. For example, `editViewer` and `perspectiveViewer` are in the same group:

    ```typescript
    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: document.getElementById("viewer"),
    });

    const perspectiveViewer = new Dynamsoft.DDV.PerspectiveViewer({
        container: document.getElementById("viewer"),
        groupUid: editViewer.groupUid, // Set to the same groupUid of the edit viewer
    });

    // Assume there is a document object firstDoc
    const docUid = firstDoc.uid;
    editViewer.openDocument(docUid);

    perpectiveViewer.currentDocument; // Returns firDoc
    ```

- Current page: When the current page of a viewer changes, the current page of other viewers in the same group will also change synchronously.

    ```typescript
    const editViewer = new Dynamsoft.DDV.EditViewer({
        container: document.getElementById("viewer"),
    });

    const perspectiveViewer = new Dynamsoft.DDV.PerspectiveViewer({
        container: document.getElementById("viewer"),
        groupUid: editViewer.groupUid, // Set to the same groupUid of the edit viewer
    });

    // Assume there is a document object firstDoc
    const docUid = firstDoc.uid;
    editViewer.openDocument(docUid);

    perpectiveViewer.currentDocument; // Returns firDoc

    perspectiveViewer.goToPage(3);

    editViewer.getCurrentPageIndex(); // Returns 3
    ```

{% comment %} - Page data: When data of a page in a viewer is edited or updated, for example, rotated 90 degrees clockwise, the data changes on this page are synchronized with other viewers in the same group. {% endcomment %}
