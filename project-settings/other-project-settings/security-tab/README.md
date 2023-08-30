# Security tab

{% hint style="info" %}
You must be on a [Forest Admin Pro plan](https://www.forestadmin.com/pricing) to have access to this tab.
{% endhint %}

Here, we explore essential features like IP whitelisting, auto logout, two-factor authentication (2FA), and user provisioning via SCIM. All to boost your project's security and manage user permissions effectively.

Your Security tab can give you access to various features:

## **IP whitelisting**

Control which IP addresses can access to your admin panel.

![](<../../../.gitbook/assets/image (609).png>)

## **Auto logout**

Force your users session logout after a few minutes of inactivity.

![](<../../../.gitbook/assets/image (274).png>)

Options are 1 min, 2 min, 3 min, 10 min, 30 min, 1h (default), 2h, 3h, 4h, 5h, 10h, and 24h.

## **Two-factor authentication (2FA)**

Enforce a second authentication factor while login to specific environments.

![](<../../../.gitbook/assets/image (184).png>)

Two-factor authentication (2FA) is a security feature available to everyone. However, requiring that a user has set up 2FA before they can access an environment is what this tab allows you to achieve.

{% hint style="warning" %}
As shown in the screenshot above, if some of your users log in using a third party, ensure 2FA is required on that third party if you want to reach the same level of security.
{% endhint %}

## User provisioning (SCIM)

User provisioning via SCIM is a way to manage your users at scale through your Identity Provider.

Setting this up means you can add any user to a Forest Admin project directly from your Identity Provider, with the correct permission level, role and tags.

This feature is compatible with **OneLogin** and **Okta**, but other Identity Providers may be added manually.

Pick and follow the integration guide that fits your needs:

- [Integration with OneLogin](scim-integration-with-onelogin.md)
- [Integration with Okta (app)](scim-integration-with-okta.md)
- [Integration with Okta (manually)](manual-scim-integration-with-okta.md)

{% hint style="warning" %}
Some Identity Providers may require endpoints that are not supported yet. Should this be the case, please [let us know](https://community.forestadmin.com) and we could consider adding them.
{% endhint %}
