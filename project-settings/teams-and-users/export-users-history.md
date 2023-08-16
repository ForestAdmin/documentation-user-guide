# Export users history

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Users' history will allow you to go back and check any changes made on your users inside of your project. The changes we currently track are:&#x20;

* Permission level
* Role
* Teams
* Tags

Each entry will display the new value for the affected fields listed above. (e.g: adding a new team to a user will log the **complete list of teams** after the action has been saved in our servers).\
\
As a way to display accurate information, the role and teams contained in each entry will be displayed with the name it had at the date of the change, we also include in the CSV export changes made on Roles and Teams such as creation, update (**name only**) and suppression.\
\
In a similar way, we track the moment a user joins or leaves your project.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Example export from users history</p></figcaption></figure>

Columns define in order:&#x20;

* The **timestamp** at which the action happened
* The **initiator**, this can be the email of an admin in your project, `Forest Admin` (only used to create an initial state right before we started tracking changes: 2023-08-10) and lastly `Identity Provider` which can be setup through [SCIM](../other-project-settings/security-tab/#user-provisioning-scim).
* The **action**; `add`, `update` or `remove` a resource
* The affected **resource**; `role`, `team` and `user-project` which represents the user in the context of your project.
* The **identifier** for the affected resource, it is either the name or the email in case of a user.
* The **new value** is a JSON object that contains the affected fields for each entry.
