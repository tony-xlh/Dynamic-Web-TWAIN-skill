---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: Dynamsoft Document Viewer Features
keywords: Documentation, Dynamsoft Document Viewer, Features
breadcrumbText: User Interface
description: Dynamsoft Document Viewer Documentation Features
permalink: /features/index.html
---

# Features

Generally, the key features of DDV are shown as below.

## Data Management

Data management is to manage the data which is imported into DDV. 

How does DDV implement data management? First of all, there are two concepts which need to be introduced, document and page. 

Page can be understood as a page, currently an image, which is the smallest unit of managing data. Each page has a unique pageUid. 

And the pages are placed in the document. Each document also has its unique docUid, one document after another makes up the whole data. 

![Doc&Page](/assets/imgs/doc&page.png)

So manage data is to manage documents and pages.

- [Document management]({{ site.features }}datamanagement/docmanagement.html)
- [Page management]({{ site.features }}datamanagement/pagemanagement.html)

Actually, if you are using the default UI of DDV, the data has been processed and managed internally.

Starting from version 2.0, DDV supports annotation functionalities, which means that annotation data also needs to be managed.

- [Annotation management]({{ site.features }}datamanagement/annotmanagement.html)

## Viewers

Viewers are used to display the data. According to the different uses of viewers, DDV provides five different viewer types, which are implemented through five viewer classes.

- [Edit Viewer]({{ site.features }}viewers/editviewer.html)
- [Capture Viewer]({{ site.features }}viewers/captureviewer.html)
- [Perspective Viewer]({{ site.features }}viewers/perspectiveviewer.html)
- [Browse Viewer]({{ site.features }}viewers/others.html#browse-viewer)
- [Custom Viewer]({{ site.features }}viewers/others.html#custom-viewer)
{% comment %}- [Data synchronisation between viewers]({{ site.features }}viewers/datasync.html){% endcomment %}

## Advanced

- [How to configure image filter]({{ site.features }}advanced/imagefilter.html)
- [How to configure boundaries detection]({{ site.features }}advanced/documentdetect.html)