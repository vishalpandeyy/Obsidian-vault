  

## **POC Analysis: Uploadcare + File Browser UI for Azure Blob Images in Email Designer**

  

### **Assumptions**

- **Image assets are stored in Azure Blob Storage.**

- **Uploadcare is used for image editing only at two points:**

  - While uploading new images (via the Uploadcare widget).

  - When inserting images into the email designer (user clicks a button, opens a file browser, selects an image, and can edit it on the fly before insertion).

- **No need to edit images directly from the file uploader after upload.**

- **The file browser should allow folder navigation, browsing, and selection of images/files (not photo-centric).**

  

---

  

### **Architecture & Workflow**

  

#### **1. Uploading Images**

- **User uploads new images via the Uploadcare widget.**

  - Uploadcare widget provides image editing features (crop, rotate, effects) at upload time.

  - After editing, the image is stored directly in Azure Blob Storage (if you configure Uploadcare to use Azure as storage, or you sync uploads there).

  

#### **2. Browsing & Selecting Images for Email Designer**

- **User clicks an "Insert Image" button in the email designer.**

- **A file browser UI opens, showing images/folders from Azure Blob Storage.**

  - File Browser (filebrowser.org) is used for folder navigation and selection.

  - User browses and selects the desired image.

  

#### **3. Editing Images on the Fly**

- **Upon selection, the file browser passes the Azure Blob image URL to Uploadcare via its [Proxy feature](https://uploadcare.com/docs/delivery/proxy/).**

  - This generates a special Uploadcare CDN URL for the selected image.

- **User is presented with an Uploadcare-powered editor (or a UI that builds transformation URLs) to apply edits (crop, resize, effects) on the fly.**

  - The edited image is delivered via Uploadcare’s CDN with transformations applied.

  - The final URL is inserted into the email designer template.

  

---

  

### **Is File Browser (filebrowser.org) a Good Fit?**

  

#### **Strengths**

- **Modern, folder-based UI:** File Browser provides a familiar file/folder navigation and selection experience, supporting Azure Blob Storage as a backend.

- **Multi-file and multi-type support:** Not limited to images; can manage any file type.

- **Extensible:** Can be customized to add actions (e.g., "Edit with Uploadcare" button on image selection).

- **Self-hosted and open source:** Offers flexibility and control.

  

#### **Limitations**

- **No native Uploadcare integration:** You must add custom logic to pass the selected image’s Azure Blob URL to Uploadcare’s Proxy endpoint for editing.

- **No built-in editing:** All editing must be handled by Uploadcare’s Proxy/CDN and your integration.

- **Requires public or signed URLs:** For Uploadcare Proxy to access images, Azure Blob files must be publicly accessible or have signed URLs.

  

---

  

### **Recommended Integration Flow**

  

1. **Upload (with editing):**

   - Use Uploadcare widget for uploading new images, with editing features enabled at upload time.

   - Store images in Azure Blob Storage.

  

2. **Browse and select:**

   - Use File Browser UI to navigate Azure Blob folders and select images.

  

3. **Edit on insertion:**

   - On selection, generate an Uploadcare Proxy CDN URL for the image.

   - Present Uploadcare’s editing UI or a custom UI for applying transformations.

   - Use the final CDN URL in the email designer.

  

---

  

### **Summary Table**

  

| Step                | Tool/Component       | Editing Supported | Notes                                                |

|---------------------|---------------------|-------------------|------------------------------------------------------|

| Upload              | Uploadcare Widget    | Yes (native)      | Editing at upload; store in Azure Blob               |

| Browse/Select       | File Browser         | No                | Folder navigation, selection only                    |

| Edit on Insert      | Uploadcare Proxy/CDN | Yes (on-the-fly)  | Editing via Proxy URL before inserting into template  |

  

---

  

### **Conclusion**

  

- **File Browser** is a strong fit for the asset browsing and selection layer, provided you add a custom integration to pass selected image URLs to Uploadcare’s Proxy for editing.

- **Uploadcare** provides robust editing at upload and at insertion via its Proxy, meeting your requirements for on-the-fly image editing.

- **This architecture is scalable, flexible, and leverages best-in-class open-source and SaaS tools.**  

- **Custom integration work is required** to bridge File Browser and Uploadcare Proxy, but this is straightforward and does not require modifying either core product.

  

---

  

**In summary:**  

Your refined workflow is well-supported by using File Browser for navigation/selection and Uploadcare for editing, with minimal custom glue code to connect the two at the point of image insertion into the email designer.