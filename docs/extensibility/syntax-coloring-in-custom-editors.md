---
title: "Syntax Coloring in Custom Editors"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: na
ms.topic: "article"
helpviewer_keywords: 
  - "editors [Visual Studio SDK], custom - syntax coloring"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
translation.priority.mt: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Syntax Coloring in Custom Editors
Visual Studio Environment SDK editors, including the core editor, use language services to identify specific syntactical items and display them with specified colors for a given document view.  
  
## Colorization Requirements  
 All editors implementing a language service's colorizer must:  
  
1.  Use an object implementing \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> to manage the text to be colorized and an object implementing \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> to provide a document view of the text.  
  
2.  Obtain an interface to a particular language service by querying the VSPackage's service provider using the languages service's identifying GUID.  
  
3.  Call the \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID*> method of the object implementing \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. This method associates the language service with the \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementation that the VSPackage uses to manage the text that is to be colorized.  
  
## Core Editor Usage of a Language Service's Colorizer  
 When a language service with a colorizer is obtained by an instance of the core editor, the parsing and rendering of text by a language service's colorizer occurs automatically without requiring any further intervention on your part.  
  
 The IDE transparently:  
  
-   Calls the colorizer as needed to parse and analyze text as it is added or modified in the implementation of \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Ensures that the display supplied by the document view provided by the \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementation is updated and repainted using the information returned by the colorizer.  
  
## Non-core Editor Usage of a Language Service's Colorizer  
 Non-core editor instances can also use a language service's syntax colorization service, but they must explicitly retrieve and apply the service's colorizer and repaint their document views themselves.  
  
 To do this requires a non-core editor to:  
  
1.  Obtain a language service's colorizer object (which implements `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` and \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Your VSPackage does this by calling the \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer*> method on the language service's interface.  
  
2.  Call the \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine*> method to request that a particular span of text be colorized.  
  
     The \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine*> method returns an array of values, one for each letter in the text span being colorized. It also identifies the text span as a particular type of colorable item, such as a comment, keyword, or data type.  
  
3.  Use the colorization information returned by \<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine*> to repaint and display its text.  
  
> [!NOTE]
>  In addition to using a language service's colorizer, a VSPackage can choose to use the general-purpose Visual Studio Environment SDK text-coloring mechanism. For more information on this mechanism, see [Using Fonts and Colors](../extensibility/using-fonts-and-colors.md).  
  
## See Also  
 [Syntax Coloring in a Legacy Language Service](../extensibility/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementing Syntax Coloring](../extensibility/implementing-syntax-coloring.md)   
 [How to: Use Built-In Colorable Items](../extensibility/how-to--use-built-in-colorable-items.md)   
 [Custom Colorable Items](../extensibility/custom-colorable-items.md)