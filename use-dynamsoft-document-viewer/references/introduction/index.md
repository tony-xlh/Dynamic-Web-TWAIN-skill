---
layout: default-layout
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
title: JavaScript PDF Viewer SDK | Dynamsoft Document Viewer
keywords: Documentation, Dynamsoft Document Viewer, Introduction
breadcrumbText: Introduction
description: Powerful JavaScript PDF viewer & document viewer SDK. Integrate seamless document viewing into your web apps with Dynamsoft Document Viewer.
---

# Introduction to Dynamsoft Document Viewer

Dynamsoft Document Viewer is a browser-based JavaScript SDK designed for viewing and editing images and PDFs. It provides a wide range of functionalities, including PDF annotation, page manipulation, image quality enhancement, and document saving. To see it in action, please visit this [online demo](https://demo.dynamsoft.com/document-viewer/).

## Security

Dynamsoft Document Viewer does not rely on any external third-party JavaScript library. All processing, such as rendering and editing, is securely performed within the browser. This architecture eliminates the need for a server-side backend, ensuring security compliance and scalability.

The SDK's [redaction](/features/datamanagement/annotmanagement.md#redaction) feature goes beyond visual masking - it permanently removes the underlying data from the document. This ensures that sensitive information (PII, classified text, financial data) cannot be recovered or leaked, making it ideal for industries with strict compliance requirements like legal, healthcare, and government.

## Browser and Platform Compatibility

Dynamsoft Document Viewer is designed to work seamlessly across different browsers and platforms. It is compatible with major browsers like Chrome, Firefox, Safari, and Edge, ensuring a consistent user experience. Additionally, it supports various operating systems, including Windows, macOS, Linux, iOS, and Android, allowing users to access documents from any device.

## Supported File Types

Users can open, edit, and save PDFs, as well as images in various formats, such as JPEG, PNG, and TIFF.

## Annotation Types

Dynamsoft Document Viewer supports a variety of annotation types to enhance document interaction and collaboration. Users can add, edit, and delete annotations such as:

- text
- highlight
- underline
- strikeout
- shape
- stamp
- freehand drawing
- redaction

## Data Management Concepts

Dynamsoft Document Viewer organizes data using two main concepts: "document" and "page." A document can contain one or multiple pages, and each page must belong to a single document.

- Page: The smallest unit of data management. Each page has a unique page ID.
- Document: A collection of pages, each with a unique doc ID. Documents collectively make up the entire data set.

Managing data, therefore, involves managing documents and pages.

- [Document Management]({{ site.features }}datamanagement/docmanagement.html)
- [Page Management]({{ site.features }}datamanagement/pagemanagement.html)

If you are using the default UI of DDV, data processing and management are handled internally.

## UI Customization

The SDK offers extensive customization options, enabling developers to tailor the UI to meet specific application needs and branding requirements.

## Designed to Support Diverse Document Workflows

Dynamsoft Document Viewer is built to support a wide range of document-centric workflows with its document viewing, editing, and scanning features. It has four built-in viewer types to suit different use cases:

* **Edit Viewer**: Enables viewing and editing of documents with annotation support.
* **Capture Viewer**: Integrates camera controls for streamlined, continuous capture workflows.
* **Perspective Viewer**: Allows document cropping with perspective transformation.
* **Browse Viewer**: Suitable for previewing multi-page documents or navigating document collections.

