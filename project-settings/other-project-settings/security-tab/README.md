# Security tab

{% hint style="info" %}
You must be on a [Forest Admin Pro plan](https://www.forestadmin.com/pricing/) to have access to this tab
{% endhint %}

Here, we explore essential features like IP whitelisting, auto logout, two-factor authentication (2FA), and user provisioning via SCIM. All to boost your project's security and manage user permissions effectively.

Your Security tab unlocks 3 features:

## **IP whitelisting**

Control which IP addresses you wish to allow access to.

![](<../../../.gitbook/assets/image (609).png>)

## **Auto logout**

Force logout after x minutes of inactivity.

![](<../../../.gitbook/assets/image (274).png>)

Options are 1 min, 2 min, 3 min, 10 min, 30 min, 1h (default), 2h, 3h, 4h, 5h, 10h, and 24h.

## **Two-factor authentication (2FA)**

Enforce 2FA in specific environments.

![](<../../../.gitbook/assets/image (184).png>)

Two-factor authentication (2FA) is a security feature available to everyone. However, requiring that a user has set up 2FA before they can access an environment is what this tab allows you to achieve.

{% hint style="warning" %}
As shown in the screenshot above, if some of your users log in using a third party, ensure 2FA is required on that third party if you want to reach the same level of security.
{% endhint %}

## User provisioning (SCIM)

User provisioning via SCIM is a way to manage your users through your Identity Provider.

Setting this up means you can add any user to a Forest Admin project directly from your Identity Provider, with the correct permission level role and tags.

We have implemented this feature to work with **OneLogin** and **Okta**, but other Identity Providers may be added manually.

{% hint style="warning" %}
Certain Identity Providers may require endpoints that we don't support yet. Should this be the case, please let us know and we could consider adding them.
{% endhint %}

### [Adding Forest Admin to OneLogin](scim-integration-with-onelogin.md)

### [Adding Forest Admin to Okta](scim-integration-with-okta.md)

[Adding Forest Admin to Okta (manually configured app)](manual-scim-integration-with-okta.md)
