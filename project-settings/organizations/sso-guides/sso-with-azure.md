---
description: Azure Active Directory SSO for Forest Admin
---

# Azure Active Directory SSO

{% hint style="info" %}
You must have one project in your organization with the plan [Forest Admin Pro plan](https://www.forestadmin.com/pricing/) to have access to this feature.
{% endhint %}

## Requirements

To configure Azure Active Directory SAML SSO, you must:

- Have admin permission level in Forest Admin

## Configuration
1. In the Azure Active Directory admin center, add a new Enterprise application. Retool is not listed in the Azure AD Gallery, so you must select Create your own application.
2. Select SAML 2.0 and follow the wizard.
3. Fill in all required parameters as shown in the tab bellow. Leave Relay state and Logout URL blank.
4. Navigate to **SAML Signing Certificate** section. And copy the `App Federation Metadata Url` head to Forest Admin, select **XML file upload or XML file endpoint** and paste the `App Federation Metadata Url` to the Metadata XML endpoint.
5. Perform some tests and enables it for your whole company.


| Setting | Description | Value |
| --- | --- | --- |
| Reply URL (Assertion Consumer Service URL)* | Assertion Consumer Service URL is responsible for receiving the SAML response | `https://api.forestadmin.com/api/saml/callback` |
| Sign on URL* | Sign on URL | `https://api.forestadmin.com/api/saml/callback` |
| Single Logout URL | Redirected to this location after logout | `https://app.forestadmin.com/login` |
| Audience (EntityID) | Should be **email address used on Forest Admin accounts** | `forestadmin-OrganizationName` |

### Troubleshooting

Follow the below verifications:

* Double check all information (endpoints, certificate expiration dates, etc..)
* Make sure the `nameID` configured on your Identity Provider is the **email address used on Forest Admin accounts**