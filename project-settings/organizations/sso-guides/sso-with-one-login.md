---
description: OneLogin SSO for Forest Admin
---

# OneLogin SSO

{% hint style="info" %}
You must have one project in your organization with the plan [Forest Admin Pro plan](https://www.forestadmin.com/pricing/) to access this feature.
{% endhint %}

## Configuration
1. In your OneLogin admin dashboard, click **Add app**
2. Select **SAML Custom Connector (Advanced)** and follow the wizard.
3. In the **Configuration** section, enter all required parameters as shown in the tab bellow.
4. Navigate to **SSO** section, and copy the `Issuer URL` head to Forest Admin, select **XML file upload or XML file endpoint** and paste the `Issuer URL` to the Metadata XML endpoint.
5. You can perform some tests before enabling it for your whole company..

| Setting | Description | Value |
| --- | --- | --- |
| ACS URL* | Assertion Consumer Service URL is responsible for receiving the SAML response | `https://api.forestadmin.com/api/saml/callback` |
| ACS Consumer) URL Validator* | URL Validator | `^https://(api\|app).development.forestadmin.com/.*$` |
| Logout URL | Redirected to this location after logout | `https://app.forestadmin.com/login` |
| SAML nameID format | Should be the **email address used on Forest Admin accounts** | Select **Email** |
| Audience (EntityID) | A globally unique name | `forestadmin-OrganizationName` |
| (Optional) RelayState | Only useful for [IDP-initiated login](../organization-settings.md#idp-initiated-login) | `{"organizationName": "<OrganizationName>", "destinationUrl": "organization.projects"}`|

### IDP-initiated login
You can find more info on [IDP-initiated login here](../organization-settings.md#idp-initiated-login)

![](<../../../.gitbook/assets/image (610).png>)



### Troubleshooting

Check the steps below this if you encounter an issue::

* Double check all information (endpoints, certificate expiration dates, etc..)
* Make sure the `nameID` configured on your Identity Provider is the **email address used on Forest Admin accounts**
