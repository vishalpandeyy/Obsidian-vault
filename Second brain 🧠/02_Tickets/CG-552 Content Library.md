---
ticket: 
tags:
  - jira
  - bug
status: in-progress
TODO:
  - Assess Video Editing in uploadcare
  -  Assess Click's Image Manager
---

TODO:
- assess video editing 
- assess current [[Image manager]]


# 🎫 <Research uploadcare.com>

## Summary
The request is to run a POC with **uploadcare.com** and evaluate the integration.

The Content Library will be a replacement of the Image Manager for managing content, files, templates, assets and integrate it in Marketing Automation and Click CRM.

The Content Lib will be used by the latest email, form, landing pages editors and it should use the existing customer storage account.

## Hypothesis

## Fix Ideas

## Result

## Links
- PR: 
- Jira: 


## Requirements Analysis

## **Core File Management Features**

**Upload & Storage Requirements:**

- Multi-source uploads (local, URLs, cloud storage)
    
- Drag-and-drop functionality
    
- Folder/subfolder organization
    
- File versioning and metadata management
    
- Storage quotas and limits (1GB for MA, 10GB for enterprise)
    

**Image Processing Requirements:**

- On-the-fly image editing (resize, crop, optimize)
    
- Format conversion capabilities
    
- Preview functionality
    
- Integration with email/landing page editors
    

**Search & Organization Requirements:**

- Multiple view types (list/tile)
    
- Advanced filtering and sorting
    
- Wildcard search capabilities
    
- Tagging and metadata support
    
- Folder management with alphabetization
    

## POC Implementation Tasks

## **Phase 1: Core Integration**

- **Task 1.1**: Implement Uploadcare widget with editing capabilities12
    
- **Task 1.2**: Set up Azure Blob Storage backend integration12
    
- **Task 1.3**: Configure automatic file transfer from Uploadcare to Azure12
    
- **Task 1.4**: Implement basic folder structure in Azure Blob Storage12
    

## **Phase 2: File Browser Integration**

- **Task 2.1**: Integrate File Browser (filebrowser.org) for navigation
    
- **Task 2.2**: Implement custom actions for Uploadcare integration
    
- **Task 2.3**: Configure Azure Blob Storage as File Browser backend
    
- **Task 2.4**: Add file selection handling and preview capabilities
    

## **Phase 3: Advanced Features**

- **Task 3.1**: Implement Uploadcare Proxy for on-the-fly editing
    
- **Task 3.2**: Add metadata management and tagging system
    
- **Task 3.3**: Develop search functionality with wildcard support
    
- **Task 3.4**: Create quota management and storage monitoring
    

## **Phase 4: Editor Integration**

- **Task 4.1**: Integrate with email designer for seamless image insertions
    
- **Task 4.2**: Implement drag-and-drop support from file browser
    
- **Task 4.3**: Add bulk operations and batch processing
    
- **Task 4.4**: Create responsive design for various screen sizes2
    

## Key Concerns & Limitations

## **Technical Challenges**

- **File Browser Limitations**: No native Uploadcare integration requires custom logic3
    
- **Public URL Requirements**: Azure Blob files must be publicly accessible or use signed URLs for Uploadcare Proxy3
    
- **Complex Workflow**: Three-step process (upload → browse → edit on insertion) adds complexity3
    

## **Scalability Concerns**

- **Storage Management**: Implementing per-customer quotas across multiple storage backends
    
- **Performance**: Large file collections may impact File Browser performance
    
- **CDN Integration**: Balancing between Azure Blob and Uploadcare CDN delivery
    

## **User Experience Challenges**

- **Learning Curve**: Users need to understand the upload-browse-edit workflow3
    
- **Editor Switching**: Seamless transitions between different editing contexts
    
- **Metadata Consistency**: Ensuring tags and metadata sync across systems
    

## Recommended Integration Approach

Based on the POC analysis3, the recommended architecture is:

|Step|Tool/Component|Editing Supported|Notes|
|---|---|---|---|
|Upload|Uploadcare Widget|✅ (native)|Editing at upload, store in Azure Blob|
|Browse/Select|File Browser|❌|Folder navigation, selection only|
|Edit on Insert|Uploadcare Proxy/CDN|✅ (on-the-fly)|Editing via Proxy URL before template insertion|