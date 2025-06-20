---
description: Adding Forest Admin to Okta from a manually configued app
---

# Manual SCIM integration with Okta

{% hint style="info" %}
You must be on a [Forest Admin Enterprise plan](https://www.forestadmin.com/pricing) to have access to this feature.
{% endhint %}

## Supported features

- Provisioning users from Okta to Forest Admin
- Updating user role, permission level, and tags from Okta to Forest Admin: Enabling SCIM will disable user editing from Forest Admin.
- Deleting user in Forest Admin when user is removed from Forest Admin app in Okta.
- Groups are used to assign users to team.

## Adding the Forest Admin app

Go to the Applications tab, then click "Browse App Catalog":

<figure><img src="../../.gitbook/assets/image (466).png" alt=""><figcaption></figcaption></figure>

​​​Select "SCIMForest 2.0 Test App (Header Auth)"

<figure><img src="../../.gitbook/assets/image (463).png" alt=""><figcaption></figcaption></figure>

Give your application a name. Keep in mind this app will be linked to one Forest Admin project. You may want to configure multiple apps if you want to activate SCIM provisioning on several projects.

## Authenticating Okta in Forest Admin

Go to your Forest Admin project settings and enable the User provisioning feature: this will automatically generate a **token** that you will need to paste into your Okta app:​

<figure><img src="../../.gitbook/assets/image (450).png" alt=""><figcaption></figcaption></figure>

Paste your token - prefixed by "Bearer" in the API Token field in the Integration tab:​​​​

{% hint style="danger" %}
If your token is "abc" then write "Bearer abc" in the API Token field
{% endhint %}

<figure><img src="../../.gitbook/assets/image (499).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (487).png" alt=""><figcaption></figcaption></figure>

## Configuring the app

You may then proceed to configure your app:

{% hint style="warning" %}
The "Sync Password" field should be kept disabled, as we don't support it.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (500).png" alt=""><figcaption></figcaption></figure>

## Adding Forest Admin custom parameters

- permissionLevel (string): should match any of “Admin”, “Developer”, “Editor”, or “User”.
- teams (`string`): comma separated list of names exactly matching a team name in the project. ex: `"Operators,Support"`. This should either be filled in via a custom mapping rule or ignored if you are using Groups.
- role (`string`): should match exactly an existing role in the project.
- tags (optional `string`): key/value pairs, separated with a semicolon. ex: `"regions:France,Italie;job:developer"`

Go to Profile Editor and add attributes:

<figure><img src="../../.gitbook/assets/image (536).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The "External namespace" field should be filled with `urn:ietf:params:scim:schemas:extension:forest:2.0:User`
{% endhint %}

## Managing mapping rules

Create mapping rules to automatically provide values to mandatory parameters `role` and `permissionLevel`, and optionally `tags`. If you don’t create mapping rules, you will have to provide these values manually for each user provisioned.

{% hint style="warning" %}
Beware of selecting the right mapping direction: Okta to Forest Admin
{% endhint %}

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

## Adding custom user attributes

You may want to add custom user attributes to base your mapping rules on. To do so, go in the global user profile in Directory > profile editor.

<figure><img src="../../.gitbook/assets/image (571).png" alt=""><figcaption></figcaption></figure>

## Managing teams with SCIM groups

Groups allow you to create mapping rules between Okta groups and Forest Admin teams.

First, go to the Directory tab and on the Groups section, ensure that you defined a group for each Forest Admin team.

<figure><img src="../../.gitbook/assets/image (584).png" alt=""><figcaption></figcaption></figure>

Then go to the Forest Admin App in Okta and click on the "Push groups" tab.

<figure><img src="../../.gitbook/assets/image (596).png" alt=""><figcaption></figcaption></figure>

Click on "Refresh App Groups" then "Push Groups" and select "Find groups by name". Type in the name of any group you want to link with a Forest Admin team.

![](<../../.gitbook/assets/image (582).png>)
![](<../../.gitbook/assets/image (583).png>)

You can then map the Okta group with an existing Forest Admin team or create a new team with the same name.

{% hint style="warning" %}
Warning: when you link a group from Okta to a Forest Admin team, the Forest Admin team will be renamed to match the group name, unless you disable this option (see below).
{% endhint %}

<figure><img src="../../.gitbook/assets/image (589).png" alt=""><figcaption></figcaption></figure>

To prevent Okta from renaming your Forest Admin teams, you can disable groups renaming in the app settings.

![](<../../.gitbook/assets/image (594).png>)
![](<../../.gitbook/assets/image (586).png>)
