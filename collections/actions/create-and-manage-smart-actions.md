# Using Smart Actions

### What is a Smart Action?

Sooner or later, you will need to perform actions on your data that are **specific to your business**. Moderating comments, generating an invoice, logging into a customer’s account or banning a user are exactly the kind of important tasks to unlock in order to manage your day-to-day operations.

On our Live Demo example, our `companies` collection has many examples of Smart Action. The simplest one is `Mark as live`.

{% hint style="info" %}
If you're looking for information on native actions (CRUD), check out [this page](./).
{% endhint %}

### Enable/Disable a Smart Action according to the state of a record

Sometimes, your Smart Action only makes sense depending on the state of your records. On our Live Demo, it does not make any sense to enable the `Mark as Live` Smart Action on the `companies` collection if the company is already live, right?

In the collection settings, you can configure the UI options of your Smart Actions.

![](<../../.gitbook/assets/Capture d’écran 2019-07-01 à 15.33.57.png>)

![](<../../.gitbook/assets/Capture d’écran 2019-07-01 à 15.03.13.png>)

### &#x20;Restrict a smart action to specific users and roles <a href="#restrict-a-smart-action-to-specific-users" id="restrict-a-smart-action-to-specific-users"></a>

When using Forest Admin with several teams and when you have clear roles defined it becomes relevant to restrict a smart action only to a few collaborators. This option is accessible through the Edit layout mode in the Smart actions’ section of your collection's settings.\
\
[Learn more about roles](https://docs.forestadmin.com/documentation/reference-guide/teams-and-users/manage-roles#roles).

![](<../../.gitbook/assets/assign roles and actions.png>)

### Require approval for a Smart action <a href="#require-approval-for-a-smart-action" id="require-approval-for-a-smart-action"></a>

Critical actions for your business may need approval before being processed.

#### Set up your approval workflow

To add an additional layer of security over a smart action, head over to the _Roles_ tab of your [projects settings](../../project-settings/other-project-settings/#how-to-access-project-settings). From there, you'll be able to select Trigger with approval for that smart action. Note that this must be set for each role.

#### Review approval requests

Actions requiring approval will be available in the Collaboration menu **(3)** in the “Approvals” section:

* “Requested” for all incoming requests (yours to approve or not)
* “To Review” **(4)** for requests you need to review
* “History” for all past requests.

In “To Review”, you will be able to approve or reject the request **(5)** with an optional message **(6)** for more details.

![](<../../.gitbook/assets/Capture d’écran 2019-07-01 à 15.52.53.png>)

![](<../../.gitbook/assets/Capture d’écran 2019-07-01 à 16.00.32.png>)

#### Review past approval requests

All past approval requests - made by you or other approvers - in the History tab **(1)**.

![](<../../.gitbook/assets/Capture d’écran 2019-07-01 à 15.59.47.png>)

{% hint style="info" %}
You can export your approval requests history from this tab using the top right button **(2)**.
{% endhint %}

You can get more details on a specific action by clicking on it:

![](<../../.gitbook/assets/Capture d’écran 2019-07-01 à 16.05.38.png>)

{% hint style="success" %}
Want to go further with Smart Actions? Read the next page to discover how to make your Smart Actions even more powerful with **Forms**!
{% endhint %}
