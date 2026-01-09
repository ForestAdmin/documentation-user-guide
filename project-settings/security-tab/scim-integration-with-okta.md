---
description: Adding Forest Admin to Okta from the preconfigured app (recommended)
---

# SCIM integration with Okta

## Supported features

* Provisioning users from Okta to Forest Admin
* Updating user role, permission level, and tags from Okta to Forest Admin: Enabling SCIM will disable user editing from Forest Admin.
* Deleting user in Forest Admin when user is removed from Forest Admin app in Okta.
* SCIM Groups are used to assign users to teams.

Note:

* userName is following an email format and is readonly after creation
* firstName and lastName are also readonly after creation

## Requirements

In order to enable Okta SCIM to manage your Forest Admin users you must:

* Have a [Forest Admin Enterprise plan](https://www.forestadmin.com/pricing)
* Be administrator of your Forest Admin project

## Adding the Forest Admin app

Go to the Applications tab, then click "Browse App Catalog":

<figure><img src="../../.gitbook/assets/image (466).png" alt=""><figcaption></figcaption></figure>

Select "Forest Admin"

<figure><img src="../../.gitbook/assets/image (452).png" alt=""><figcaption></figcaption></figure>

Give your application a label. Keep in mind this app will be linked to a single Forest Admin project. You may want to configure multiple apps if you want to activate SCIM provisioning on several projects.

<figure><img src="../../.gitbook/assets/image (489).png" alt=""><figcaption></figcaption></figure>

## Authenticating Okta in Forest Admin

Go to your Forest Admin project settings and enable the User provisioning feature: this will automatically generate a **token** that you will need to paste into your Okta app:​

<figure><img src="../../.gitbook/assets/image (510).png" alt=""><figcaption></figcaption></figure>

Paste your token in the API Token field in the Integration tab:​​​​

<figure><img src="../../.gitbook/assets/image (447).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (496).png" alt=""><figcaption></figcaption></figure>

## Configuring the app

You may then proceed to configure your app:

<figure><img src="../../.gitbook/assets/image (481).png" alt=""><figcaption></figcaption></figure>

## Managing mapping rules

Create mapping rules to automatically provide values to mandatory parameters `teams`, `role`, and `permissionLevel`, and optionally `tags`. If you don’t create mapping rules, you will have to provide these values manually for each user provisioned.

* permissionLevel (string): should match any of `admin`, `developer`, `editor`, or `user`.
* teams (`string`): comma separated list of names exactly matching a team name in the project. ex: `"Operators,Support"`. This should either be filled in via a custom mapping rule or ignored if you are using Groups.
* role (`string`): should match exactly an existing role in the project.
* tags (optional `string`): key/value pairs, separated with a semicolon. ex: `"regions:France,Italie;job:developer"`

{% hint style="warning" %}
Beware of selecting the right mapping direction: Okta to Forest Admin
{% endhint %}

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Adding custom user attributes

You may want to add custom user attributes to base your mapping rules on. To do so, go in the global user profile in Directory > profile editor.

<figure><img src="../../.gitbook/assets/image (509).png" alt=""><figcaption></figcaption></figure>

## Managing teams with SCIM groups

Groups allow you to create mapping rules between Okta groups and Forest Admin teams.

First, go to the Directory tab and on the Groups section, ensure that you defined a group in Okta for each team in Forest Admin. You can also create teams in Forest Admin directly from Okta.

<figure><img src="../../.gitbook/assets/image (584).png" alt=""><figcaption></figcaption></figure>

Then go to the Forest Admin App in Okta and click on the "Push groups" tab.

<figure><img src="../../.gitbook/assets/image (596).png" alt=""><figcaption></figcaption></figure>

Click on "Refresh App Groups" then "Push Groups" and select "Find groups by name". Type in the name of any group you want to link with a Forest Admin team.

![](<../../.gitbook/assets/image (582).png>) ![](<../../.gitbook/assets/image (583) (1).png>)

You can then map the Okta group with an existing Forest Admin team or create a new team with the same name.

{% hint style="warning" %}
Removing a group from Okta created from or linked to a Forest Admin team, the Forest Admin team will be deleted.
{% endhint %}

{% hint style="warning" %}
When you link a group from Okta to a Forest Admin team, the Forest Admin team will be renamed to match the group name, unless you disable this option (see below).
{% endhint %}

<figure><img src="../../.gitbook/assets/image (589).png" alt=""><figcaption></figcaption></figure>

To prevent Okta from renaming your Forest Admin teams, you can disable groups renaming in the app settings.

![](<../../.gitbook/assets/image (4).png>) ![](<../../.gitbook/assets/image (3).png>)

## Troubleshooting

* I cannot create or update a user Please check that
  * the `permissionLevel` of this user is either `admin`, `editor`, `user` or `developer`
  * the `role` of this user matches one role that you have already defined in Forest Admin (example: `Operations`)
* I have made changes in the Okta app that I don't see reflected in Forest Admin
  * Some updates can take some time. You should allow a couple minutes before the synchronization finishes
* My agent keeps restarting
  * Some updates (for instance related to teams) are susceptible to updating your rendering, therefore your agent will have to restart. This is a normal part of Forest Admin behavior.

_If you still cannot enable SCIM, don't hesitate to_ [_ask for help on our Community forum_](https://community.forestadmin.com/)
