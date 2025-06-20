---
description: Okta SSO for Forest Admin
---

# Okta SSO

{% hint style="info" %}
You must have one project in your organization with the plan [Forest Admin Enterprise plan](https://www.forestadmin.com/pricing) to access this feature.
{% endhint %}

## Configuration

1. In your Okta admin dashboard, click **Create a new app integration**
2. Select **SAML 2.0** and follow the wizard.
3. Navigate to the Okta application you just created. Click on the **Sign On** tab, **Metadata details** section, and copy the `Metadata URL` head to Forest Admin, select **XML file upload or XML file endpoint** and paste the `Metadata URL` to the Metadata XML endpoint.
4. You can perform some tests before enabling it for your whole company..

| Setting                        | Description                                                                                                                           | Value                                                                                   |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| ACS URL\*                      | Assertion Consumer Service URL is responsible for receiving the SAML response. Check _Use this for Recipient URL and Destination URL_ | `https://api.forestadmin.com/api/saml/callback`                                         |
| Audience URI (EntityID)        | A globally unique name                                                                                                                | `forestadmin-OrganizationName`                                                          |
| Name ID format                 | Should be **email address used on Forest Admin accounts**                                                                             | Select **EmailAddress**                                                                 |
| Application username           |                                                                                                                                       | Select **Email** or let **None**                                                        |
| Update application username on |                                                                                                                                       | Select **Create and update**                                                            |
| (Optional) Default RelayState  | Only useful for [IDP-initiated login](../organization-settings.md#idp-initiated-login)                                                | `{"organizationName": "<OrganizationName>", "destinationUrl": "organization.projects"}` |

### Troubleshooting

Check the steps below this if you encounter an issue:

- Double check all information (endpoints, certificate expiration dates, etc..)
- Make sure the `Name ID format` configured on your Identity Provider is the **email address used on Forest Admin accounts too**
