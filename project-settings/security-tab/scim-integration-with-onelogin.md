---
description: Adding Forest Admin to OneLogin
---

# SCIM integration with OneLogin

{% hint style="info" %}
You must be on a [Forest Admin Pro plan](https://www.forestadmin.com/pricing) to have access to this feature.
{% endhint %}

## Supported features

- Provisioning users from OneLogin to Forest Admin
- Updating user role, permission level, and tags from OneLogin to Forest Admin: Enabling SCIM will disable user editing from Forest Admin.
- Deleting user in Forest Admin when user is removed from Forest Admin app in OneLogin.&#x20;
- SCIM Groups are used to assign users to team.

## Adding the Forest Admin app

Go to the Application tab and click "Add App"

<figure><img src="../../.gitbook/assets/image (456).png" alt=""><figcaption></figcaption></figure>

In the search bar, look for SCIM and select "SCIM Provisioner with SAML (SCIM v2 Core)"

<figure><img src="../../.gitbook/assets/image (478).png" alt=""><figcaption></figcaption></figure>

## Authenticating OneLogin in Forest Admin

Name your app, then go to your Forest Admin project settings and enable the User provisioning feature: this will automatically generate a **token** that you will need to paste into your OneLogin app:

<figure><img src="../../.gitbook/assets/image (449).png" alt=""><figcaption></figcaption></figure>

Add the following baseUrl and paste your token generated on Forest Admin:

- SCIM Base URL: `https://api.forestadmin.com/scim`

<figure><img src="../../.gitbook/assets/image (511).png" alt=""><figcaption></figcaption></figure>

## Configuring the app

SCIM JSON Template: add the following:

```json
{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User",
    "urn:ietf:params:scim:schemas:extension:forest:2.0:User"
  ],
  "userName": "{$user.email}",
  "name": {
    "givenName": "{$user.firstname}",
    "familyName": "{$user.lastname}"
  },
  "emails": [
    {
      "value": "{$user.email}",
      "primary": true,
      "type": "work"
    }
  ],
  "urn:ietf:params:scim:schemas:extension:forest:2.0:User": {
    "permissionLevel": "{$parameters.permission_level}",
    "role": "{$parameters.role}",
    "tags": "{$parameters.tags}",
    "teams": "{$parameters.teams}"
  }
}
```

## Adding Forest Admin custom parameters

- permissionLevel (`string`): should match exactly an existing permissionLevel in Forest Admin.
- teams (`string`): comma separated list of names exactly matching a team name in the project. ex: `"Operator,Admin"`. This can be either filled in via a custom mapping rule or or ignored if you are using Groups.
- role (`string`): should match exactly an existing role in the project.
- tags (optional `string`): key/value pairs, separated with a semicolon. ex: `"regions:France,Italie;job:developer"`

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

## Managing mapping rules

Create mapping rules to automatically provide values to mandatory parameters `role`, and `permissionLevel`, and optionally `tags`. If you don’t create mapping rules, you will have to provide these values manually for each user provisioned.

<figure><img src="../../.gitbook/assets/image (548).png" alt=""><figcaption></figcaption></figure>

## Adding custom user attributes

You may want to add custom user attributes to base your mapping rules on. To do so, go in the "Custom User Fields" section of the Users tab.

![](<../../.gitbook/assets/image (579).png>)

## Managing teams with SCIM groups

Groups allow you to create mapping rules between oneLogin roles and Forest Admin teams.

First, go to the Provisioning tab and on the Entitlement section, click on "Refresh" to fetch teams in OneLogin.

<figure><img src="../../.gitbook/assets/image (490).png" alt=""><figcaption></figcaption></figure>

You can then create a rule for each role you want to map with an existing Forest Admin team.

<figure><img src="../../.gitbook/assets/image (518).png" alt=""><figcaption></figcaption></figure>

When a role is added a removed from a user, it will be automatically added or removed to the corresponding Forest Admin team.
