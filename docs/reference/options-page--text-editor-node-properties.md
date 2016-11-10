---
title: "Options Page, Text Editor Node Properties"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: na
ms.topic: "article"
helpviewer_keywords: 
  - "Tools Options settings, Text Editor node properties"
  - "automation [Visual Studio], controlling Tools Options"
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 17
ms.author: "kempb"
manager: "ghogen"
translation.priority.ht: 
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
# Options Page, Text Editor Node Properties
This document describes some pages (or properties collections) that are associated with the **Text Editor** category, `DTE.Properties("TextEditor", <Property Page>)`, of the **Options** dialog box. The title of each subsection is the call that is used to access the `Properties` collection, and the table in each subsection lists the properties in the collection.  
  
 The Visual Basic macros in [Controlling Options Settings](../Topic/Controlling%20Options%20Settings.md) demonstrate how to display current options and their values for each page of the **Options** dialog box.  
  
## General  
 `DTE.Properties("TextEditor", "General")`  
  
|Property Item Name|Value|Description|  
|------------------------|-----------|-----------------|  
|GoToAnchorAfterEscape|Get/Set (Boolean)|If `True`, pressing escape while there is a selection causes the insertion point to move to where the action that created the selection was initiated. `False` moves the insertion point to the other end of the selection.|  
|DragNDropTextEditing|Get/Set (Boolean)|Determines whether you can drag a selected region of text from one location to another in the document for copy or cut/paste operations.|  
|HorizontalScrollBar|Get/Set (Boolean)|Determines whether there is a horizontal scrollbar on editor windows.|  
|VerticalScrollBar|Get/Set (Boolean)|Determines whether there is a vertical scroll bar on editor windows.|  
|SelectionMargin|Get/Set (Boolean)|Determines whether there is space at the left of the text pane for special selection operations, drawing breakpoint icons, and so forth.|  
|MarginIndicatorBar|Get/Set (Boolean)|Determines whether there is a vertical line dividing the left margin of the text pane from the main body of the text pane.|  
|UndoCaretActions|Get/Set (Boolean)|If `True`. undo operations include insertion point motion, selection commands, and so forth, in addition to editing actions that modify the buffer.|  
|AutoDelimiterHighlighting|Get/Set (Boolean)|Determines whether typing a closing delimiter causes the editor to highlight the opening delimiter. The editor always bolds the open delimiter regardless of the value of this property.|  
|EditorEmulation|Get/Set (Enum)||  
|DetectUTF8WithoutSignature|Get/Set (Boolean)|Detects whether a file uses UTF-8 encoding when it does not have an encoding signature.|  
|TrackChanges|Get/Set (Boolean)||  
  
## Plain Text  
 `DTE.Properties("TextEditor", "PlainText")`  
  
 The `PlainText` editor options affect the editor settings when text files are edited. Each programming language and [!INCLUDE[vsprvs](../codequality/includes/vsprvs_md.md)] package has its own specific **Text Editor** settings. For example, to view or change the [!INCLUDE[csprcs](../datatools/includes/csprcs_md.md)] editor settings, use `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`. For the **SQL Script** editor settings, use `DTE.Properties("TextEditor", "SQL ")`.  
  
|Property Item Name|Value|Description|  
|------------------------|-----------|-----------------|  
|AutoListMembers|Get/Set (Boolean)|Determines whether an available list of members automatically appears when a user types a period following a variable reference.|  
|AutoListParams|Get/Set (Boolean)|Determines whether a description of an argument list automatically displays when the users types a "(" following a function name.|  
|HideAdvancedMembers|Get/Set (Boolean)|Determines whether statement completion lists all members or only the commonly used ones.|  
|VirtualSpace|Get/Set (Boolean)|Determines whether white space characters are displayed as graphics. Setting this to `true` causes the `WordWrap` property item (in this list) to be set to `false`.|  
|WordWrap|Get/Set (Boolean)|Determines whether the view wraps long lines at word boundaries. Setting this to `true` causes the `VirtualSpace` property item (in this list) to be set to `false`.|  
|WordWrapGlyphs|Get/Set (Boolean)|Displays a glyph at the end of a line; this indicates that the line wraps to the next line.|  
|EnableLeftClickForURLs|Get/Set (Boolean)|Determines whether the editor underlines URLs and enables a single left-click for jumping to the URL in the system registered Web browser.|  
|IndentStyle|Get/Set (\<xref:EnvDTE.vsIndentStyle>)|Determines the indenting style: Default, Smart, or None.|  
|TabSize|Get/Set (Long)|Represents the number of spaces that equal a tab. Setting an integer outside the range 1 to 60 (inclusive) fails.|  
|InsertTabs|Get/Set (Boolean)|If `True`, TAB characters are used when indenting.|  
|IndentSize|Get/Set (Long)|Represents the number of spaces that equals one indent level. Setting an integer value outside the range 1 to 60 (inclusive) fails.|  
|ShowLineNumbers|Get/Set (Boolean)|Determines whether the view of a core editor document displays line numbers along the left margin.|  
|ShowNavigationBar|Get/Set (Boolean)|Determines whether the drop-down lists and buttons appear at the top of editor windows.|  
|CutCopyBlankLines|Get/Set (Boolean)|Cuts or copies blank lines when they are selected.|  
  
## See Also  
 [Controlling Options Settings](../Topic/Controlling%20Options%20Settings.md)   
 [Determining the Names of Property Items on Options Pages](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Options Page, Environment Node Properties](../reference/options-page--environment-node-properties.md)   
 [Options Page, Fonts and Colors Node Properties](../reference/options-page--fonts-and-colors-node-properties.md)