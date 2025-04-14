---
description: AWS IAM Identity Center SSO for Forest Admin
---

# AWS IAM Identity Center SSO

{% hint style="info" %}
You must have one project in your organization with the plan [Forest Admin Pro plan](https://www.forestadmin.com/pricing) to access this feature.
{% endhint %}

## Configuration

Forest Admin is compatible with AWS's SAML 2.0 application. To enable SSO from your AWS IAM Identity Center, please follow the detailed step by step [guide](https://docs.aws.amazon.com/singlesignon/latest/userguide/set-up-single-sign-on-access-to-applications.html) `Set up your own SAML 2.0 application`

| Setting                                      | Description                                                                            | Value                                                                                   |
| -------------------------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Application ACS URL\*                      | Assertion Consumer Service URL is responsible for receiving the SAML response. Check _Use this for Recipient URL and Destination URL_ | `https://api.forestadmin.com/api/saml/callback`                                         |
| Application SAML audience                       | This is a globally unique name that Forest Admin gives you (`Unique User ID`).         | `forestadmin-OrganizationName`                                                          |
| (Optional) Relay State                       | Only useful for [IDP-initiated login](../organization-settings.md#idp-initiated-login) | `{"organizationName": "<OrganizationName>", "destinationUrl": "organization.projects"}` |

### Troubleshooting

Check the steps below this if you encounter an issue:

- Double check all information (endpoints, certificate expiration dates, etc..)
- Make sure the `nameID` configured on your Identity Provider is the **email address used on Forest Admin accounts**
