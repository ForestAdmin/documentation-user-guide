---
description: Google SSO for Forest Admin
---

# Google SSO

{% hint style="info" %}
You must have one project in your organization with the plan [Forest Admin Pro plan](https://www.forestadmin.com/pricing/) to access this feature.
{% endhint %}

## Requirements


To configure Google SAML SSO, you must:

- Be in Admin mode in Google
- Have admin permission level in Forest Admin

## Configuration
1. Log in to your Google account and navigate to the Admin console.
2. In the Google Admin console, go to Menu: **Apps -> Web and mobile apps**.
3. Click **Add App -> Add custom SAML app** and follow the wizard.
4. In the **Service Provider Details** window, enter:
- ACS URL: Assertion Consumer Service URL is responsible for receiving the SAML response (It should be https://api.forestadmin.com/api/saml/callback).
- Entity ID: This is a globally unique name that Forest Admin gives you.
- Start URL: (Optional) This is used to set the RelayState parameter in a SAML Request, which can be a URL to redirect to after authentication (you can find more info on [IDP-initiated login here](../organization-settings.md#idp-initiated-login)).

{% hint style="info" %}
You can find the [Google documentation on custom SAML application here](https://support.google.com/a/answer/6087519?hl=en).
{% endhint %}


### Troubleshooting

Check the steps below this if you encounter an issue::

* Double check all information (endpoints, certificate expiration dates, etc..)
* Make sure the `Name ID` (the primary email) configured on your Identity Provider is the **email address used on Forest Admin accounts too**
