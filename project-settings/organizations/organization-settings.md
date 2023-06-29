# Organization settings

Your Organization settings are accessible from the top-right dropdown:

![](<../../.gitbook/assets/Capture d’écran 2021-10-13 à 11.11.27.png>)

### Overview tab

The overview tab gathers the basic settings of your Organization: here you'll be able to edit

* its name
* its logo

or delete it **permanently**.

![](<../../.gitbook/assets/image (92).png>)

### Owners tab

In this tab you can manage your Organization Owners. Owners are simply users who **have access to the Organization settings**.

![](<../../.gitbook/assets/image (117).png>)

{% hint style="warning" %}
A user must belong to at least 1 project of the Organization to be invited as an Owner and will be **automatically added as Admin** on all projects of the Organization
{% endhint %}

### Security tab

{% hint style="info" %}
The Security tab is only available for the **Plus plan** or above
{% endhint %}

This tab gathers all security options of your Organization. For now you can only configure Single Sign-On (SSO).

#### Configuring SSO

To start configuring SSO for your Organization, click on "Configure Single Sign-On":

![](<../../.gitbook/assets/Capture d’écran 2021-10-13 à 11.42.24.png>)

You'll first need to **declare Forest Admin in your Identity Provider** using the information in the grey panel:

![](<../../.gitbook/assets/image (620).png>)

{% hint style="warning" %}
Forest Admin supports SAML v2 (not v1)
{% endhint %}

Then choose how you want to communicate information from your Identity Provider (IP):

#### method 1: XML file upload or XML file endpoint

Either upload a file containing the authentication information (you'll be able to generate this file in your Identify Provider) or input the endpoint at which such a file is available (some IPs provide this).

![](<../../.gitbook/assets/image (59).png>)

#### method 2: Manual input

You may also enter your authentication information manually. You'll need to provide:

* a login endpoint
* a logout endpoint
* one certificate

![](<../../.gitbook/assets/image (595).png>)

Click on Test configuration to try to authenticate. If it works, you're all set but you will still need to enable that new SSO authentication method:

![](<../../.gitbook/assets/image (289).png>)

{% hint style="danger" %}
After enabling SSO, all users will be required to [log in](./#how-to-log-in-using-single-sign-on-sso) again.
{% endhint %}

#### IDP-initiated login

Once you have enabled SSO, you have the option to enable IDP-initiated login: this will allow your users to be automatically logged in when they come to Forest Admin from your identity provider dashboard.

![](<../../.gitbook/assets/image (318).png>)

To set it up properly, you will need to set a default **Relay state** on your identity provider following this format:

```javascript
{"organizationName": "<organization_name>", "destinationUrl": "organization.projects"}
```

For instance, on Okta:

![](<../../.gitbook/assets/image (227).png>)

On OneLogin:

![](<../../.gitbook/assets/image (610).png>)

#### Troubleshooting

Follow the below verifications:

* Double check all information (endpoints, certificate expiration dates, etc..)
* Make sure the `nameID` configured on your Identity Provider is the email address used on Forest Admin accounts
* Make sure you selected SAML v2 on your Identity Provider
