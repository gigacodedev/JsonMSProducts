Microsoft has made their product and service plan SKU IDs available [in their MS Learn docs](https://learn.microsoft.com/en-us/entra/identity/users/licensing-service-plan-reference):
> When managing licenses in the Azure portal or the Microsoft 365 admin center, you see product names that look something like Office 365 E3. When you use PowerShell v1.0 cmdlets, the same product is identified using a specific but less friendly name: ENTERPRISEPACK. When using PowerShell v2.0 cmdlets or Microsoft Graph, the same product is identified using a GUID value: 6fd2c87f-b296-42f0-b197-1e91e994b900.

While this is helpful, it would be even more useful in JSON. So I wrote a quick script that takes the CSV on that webpage and converts it to JSON, then consolidates each associated service plan into its relevant SKUs in the following schema:
- GUID: GUID used by the skuId property of the subscribedSku Microsoft Graph API
- Product_Display_Name: Used in management portals
- String_ID: Used by PowerShell v1.0 cmdlets when performing operations on licenses or by the skuPartNumber property of the subscribedSku Microsoft Graph API
- Service Plans: List of service plans in the product that correspond to the String ID and GUID
  - Service Plan ID: Service Plan GUID
  - Service Plan Name: Service Plan String ID
  - Service Plans Included Friendly Name: Used in management portals
 
Microsoft will periodically update their products table, and I'll try to keep this repo up to date. Feel free to create a PR if anything needs an update!
