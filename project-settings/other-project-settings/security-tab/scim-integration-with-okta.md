---
description: Adding Forest Admin to Okta from the preconfigured app (recommended)
---

# SCIM integration with Okta

{% hint style="info" %}
You must be on a [Forest Admin Pro plan](https://www.forestadmin.com/pricing/) to have access to this feature
{% endhint %}

## Supported features

* Provisioning users from Okta to Forest Admin
* Updating user role, permission level, teams, and tags from Okta to Forest Admin: Enabling SCIM will disable user editing from Forest Admin.
* Deleting user in Forest Admin when user is removed from Forest Admin app in Okta.&#x20;
* Groups can be used to assign users to team, do not use the "teams" parameter is you want to use groups to handle teams.

## Adding the Forest Admin app

Go to the Applications tab, then click "Browse App Catalog":

<figure><img src="../../../.gitbook/assets/image (466).png" alt=""><figcaption></figcaption></figure>

Select "Forest Admin"

<figure><img src="../../../.gitbook/assets/image (452).png" alt=""><figcaption></figcaption></figure>

Give your application a label. Keep in mind this app will be linked to one Forest Admin project. You may want to configure multiple apps if you want to activate SCIM provisioning on several projects.

<figure><img src="../../../.gitbook/assets/image (489).png" alt=""><figcaption></figcaption></figure>

## Authenticating Okta in Forest Admin

Go to your Forest Admin project settings and enable the User provisioning feature: this will automatically generate a **token** that you will need to paste into your Okta app:​

<figure><img src="../../../.gitbook/assets/image (510).png" alt=""><figcaption></figcaption></figure>

Paste your token in the API Token field in the Integration tab:​​​​

<figure><img src="../../../.gitbook/assets/image (447).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (496).png" alt=""><figcaption></figcaption></figure>

## Configuring the app

You may then proceed to configure your app:

<figure><img src="../../../.gitbook/assets/image (481).png" alt=""><figcaption></figcaption></figure>

## Managing mapping rules

Create mapping rules to automatically provide values to mandatory parameters `teams`, `role`, and `permissionLevel`, and optionally `tags`. If you don’t create mapping rules, you will have to provide these values manually for each user provisioned.

* permissionLevel (string): should match any of “Admin”, “Developer”, “Editor”, or “User”.
* role (`string`): should match exactly an existing role in the project.
* teams (optional `string`): team names, separated with a coma. ex: `"team1,team2,someOtherTeam"`. If this parameter is not present, you have to use groups to handle teams.
* tags (optional `string`): key/value pairs, separated with a semicolon. ex: `"regions:France,Italie;job:developer"`

{% hint style="warning" %}
Beware of selecting the right mapping direction: Okta to ForestAdmin
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (443).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
For _teams_, the function `Arrays.toCsvString(user.<your_custom_parameter>)` allows to conversion of a multivalue field to a string with a comma separator.
{% endhint %}

## Adding custom user attributes

You may want to add custom user attributes to base your mapping rules on. To do so, go in the global user profile in Directory > profile editor.

<figure><img src="../../../.gitbook/assets/image (509).png" alt=""><figcaption></figcaption></figure>

## Managing teams with SCIM groups

You can use SCIM groups to manage teams in Forest Admin. Groups allow you to create mapping rules between Okta groups and Forest Admin teams.

First, go to the Directory tab and on the Groups section, ensure that you defined a group for each ForestAdmin team.

<figure><img src="../../../.gitbook/assets/image (584).png" alt=""><figcaption></figcaption></figure>

Then go to the ForestAdmin App in Okta and click on the "Push groups" tab.

<figure><img src="../../../.gitbook/assets/image (596).png" alt=""><figcaption></figcaption></figure>

Click on "Push Groups" and select "Find groups by name". Type in the name of any group you want to link with a ForestAdmin team.

![](<../../../.gitbook/assets/image (582).png>)![](<../../../.gitbook/assets/image (583).png>)

Okta will then check if a ForestAdmin team exists with the same name, or suggest you to select an existing team to link with the group.

{% hint style="warning" %}
Warning: when you link a group from Okta to a ForestAdmin team, the ForestAdmin team will be renamed to match the group name, unless you disable this option (see below).
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (589).png" alt=""><figcaption></figcaption></figure>

To prevent Okta from renaming your ForestAdmin teams, you can disable groups renaming in the app settings.

![](<../../../.gitbook/assets/image (594).png>)![](<../../../.gitbook/assets/image (586).png>)
