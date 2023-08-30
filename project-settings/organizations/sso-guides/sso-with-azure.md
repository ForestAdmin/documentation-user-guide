---
description: Azure Active Directory SSO for Forest Admin
---

# Azure Active Directory SSO

{% hint style="info" %}
You must have one project in your organization with the plan [Forest Admin Pro plan](https://www.forestadmin.com/pricing) to access this feature.
{% endhint %}

## Configuration

1. In the Azure Active Directory admin center, add a new Enterprise application. Forest Admin is not listed in the Azure AD Gallery, so you must select **Create your own application**.
2. Select **Integrate any other application you don’t find in the gallery (Non-gallery)** and follow the wizard.
3. Fill in all required parameters as shown in the table bellow.
4. Navigate to **SAML Signing Certificate** section, and copy the `App Federation Metadata Url` head to Forest Admin, select **XML file upload or XML file endpoint** and paste the `App Federation Metadata Url` to the Metadata XML endpoint.
5. You can perform some tests before enabling it for your whole company..

| Setting                                      | Description                                                                            | Value                                                                                   |
| -------------------------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Reply URL (Assertion Consumer Service URL)\* | Assertion Consumer Service URL is responsible for receiving the SAML response          | `https://api.forestadmin.com/api/saml/callback`                                         |
| Sign on URL\*                                | Sign on URL                                                                            | `https://api.forestadmin.com/api/saml/callback`                                         |
| Identifier (Entity ID)                       | This is a globally unique name that Forest Admin gives you (`Unique User ID`).         | `forestadmin-OrganizationName`                                                          |
| (Optional) Logout URL                        | Redirected to this location after logout                                               | `https://app.forestadmin.com/login`                                                     |
| (Optional) Relay State                       | Only useful for [IDP-initiated login](../organization-settings.md#idp-initiated-login) | `{"organizationName": "<OrganizationName>", "destinationUrl": "organization.projects"}` |

### Troubleshooting

Check the steps below this if you encounter an issue:

- Double check all information (endpoints, certificate expiration dates, etc..)
- Make sure the `nameID` configured on your Identity Provider is the **email address used on Forest Admin accounts**
