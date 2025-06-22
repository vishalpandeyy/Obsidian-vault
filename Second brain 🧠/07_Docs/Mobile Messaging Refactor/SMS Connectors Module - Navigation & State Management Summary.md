### **1. Route Structure**

- **Parent Route:**  
    /sms-settings/connector
    
- **Child Routes:**
    
    - /sms-settings/connector/twilio
        
    - /sms-settings/connector/bulk-sms
        
    - /sms-settings/connector/message-media
        
- **Component Hierarchy:**
    
    - SmsConnectorsComponent hosts a <router-outlet> for child connector components.
        
    - Each connector type (Twilio, BulkSMS, MessageMedia) has its own component rendered for its respective route.
        

### **2. Add/Edit Mode Handling**

- **Single Route for Both Modes:**  
    Each connector’s add and edit modes share the same route (e.g., /sms-settings/connector/twilio).
    
- **Mode Determination:**  
    The mode is determined by the presence of a currentConnector object in the shared RxJS store (SmsSettingsStoreService):
    
    - If currentConnector exists, the component is in **edit** mode.
        
    - If not, it is in **add** mode.
        

### **3. Navigation Actions**

- **On Save (Add or Edit):**  
    After creating or updating a connector, navigation returns to the connector list:
    
    `this.router.navigate(['../', SmsSettingsRouting.ConnectorList], {   relativeTo: this.route.parent,   queryParamsHandling: 'preserve', });`
    
- **On Cancel:**  
    Similar navigation logic is used to return to the connector list.
    

### **4. State Persistence Issue [**[https://clickdimensions.atlassian.net/browse/CG-4104](https://clickdimensions.atlassian.net/browse/CG-4104) **]**

- **Problem:**  
    The RxJS store (SmsSettingsStoreService) is in-memory only.  
    **If the user refreshes the page or navigates directly to an edit route, the store is cleared and edit mode cannot be restored.**
    
- **Impact:**  
    This affects all connectors (Twilio, BulkSMS, MessageMedia, etc.), not just Twilio.
    

### **5. Recommendations for Robustness**

- **Use Route Parameters for Edit:**  
    Change edit routes to include a unique connector ID (e.g., /sms-settings/connector/twilio/:connectorId).  
    On navigation, fetch the connector by ID from the backend and set it in the store.
    
- **Alternative:**  
    Persist currentConnector in browser storage (localStorage/sessionStorage), but this is less robust and not recommended for sensitive or frequently changing data.
    

### **6. Summary Table**

|   |   |   |   |   |
|---|---|---|---|---|
|Connector Type|Add/Edit Route|Mode Detection|Refresh Safe?|Recommended Fix|
|Twilio|/sms-settings/connector/twilio|Store state|No|Use /twilio/:connectorId|
|BulkSMS|/sms-settings/connector/bulk-sms|Store state|No|Use /bulk-sms/:connectorId|
|MessageMedia|/sms-settings/connector/message-media|Store state|No|Use /message-media/:connectorId|

## **Conclusion**

- The SMS Connectors module uses a shared route for add/edit, relying on in-memory store state to distinguish modes.
    
- This pattern is fragile on refresh or direct navigation.
    
- **For robust, refresh-safe navigation and deep-linking, use route parameters for edit mode and fetch connector data by ID.**