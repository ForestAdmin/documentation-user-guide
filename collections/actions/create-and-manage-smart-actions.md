# Using Smart Actions

### What is a Smart Action?

Sooner or later, you will need to perform actions on your data that are **specific to your business**. Moderating comments, generating an invoice, logging into a customer’s account or banning a user are exactly the kind of important tasks to unlock in order to manage your day-to-day operations.

On our Live Demo example, our `companies` collection has many examples of Smart Actions. The simplest one is `Mark as live`.

{% hint style="info" %}
If you're looking for information on native actions (CRUD), check out [this page](./).
{% endhint %}

### Create a Smart Action
Here it depends on your setup: if you are using a self-hosted agent, head on to the [Developer documentation portal](https://docs.forestadmin.com/documentation-portal), navigate to the `Smart Actions` documentation of your agent stack to start plugging them right into your agent.
If you have used instant setup (cloud), you will be able to create new actions right from your Collection settings.

Go to Edit Layout, select the collection where you want to create new actions, then select the `Actions`tab:

![](<../../.gitbook/assets/2023-06-29_14.30.40.png>)

From there you can click on `Create your first action` to get started.
#### Action of type 'Update record'
This action allows you to update the value of selected fields from your records. You just need to select the appropriate fields by clicking on 'Add field', and selecting the right entry from the dropdown menu, then type the desired value on the right

![](<../../.gitbook/assets/2023-06-29_14.44.17.png>)

#### Action of type 'Webhook'
This action allows you to plug in to a workflow automation tool like n8n, make, zapier… and trigger actions on those platforms right from your admin panel. You just need to pick your favorite automation tool, and create a webhook endpoint with your workflow. Then copy the URL to this endpoint in the provided field:

![](<../../.gitbook/assets/2023-06-29_14.49.48.png>)


{% hint style="info" %}
When a webhook action is triggered on a record (or list of records), Forest Admin will send along the ids of those records so that you can use them in your automation process.
{% endhint %}

After saving those actions, you will see a spinner that lets you know the action is being created, and a couple seconds later it is available (you will just need to refresh your browser when prompted).

### Enable/Disable a Smart Action according to the state of a record

Sometimes, your Smart Action only makes sense depending on the state of your records. On our Live Demo, it does not make any sense to enable the `Mark as Live` Smart Action on the `companies` collection if the company is already live, right?

In the collection settings, you can configure the UI options of your Smart Actions.

![](<../../.gitbook/assets/2019-07-01_15.33.57.png>)

![](<../../.gitbook/assets/2019-07-01_15.03.13.png>)

### &#x20;Restrict a Smart Action to specific roles <a href="#restrict-a-smart-action-to-specific-users" id="restrict-a-smart-action-to-specific-users"></a>

When using Forest Admin with several teams and when you have clear roles defined it becomes relevant to restrict a Smart Action only to a specific set of roles. It can be configured in the [Roles tab](../../project-settings/teams-and-users/manage-roles.md#smart-action-permissions) of your project settings.

### Require approval for a Smart Action <a href="#require-approval-for-a-smart-action" id="require-approval-for-a-smart-action"></a>

Critical actions for your business may need approval before being processed.

#### Set up your approval workflow

To add an additional layer of security over a Smart Action, head over to the _Roles_ tab of your [projects settings](../../project-settings/other-project-settings/#how-to-access-project-settings). From there, you'll be able to select Trigger with approval for that Smart Action. Note that this must be set for each role.

#### Review approval requests

Actions requiring approval will be available in the Collaboration menu **(3)** in the “Approvals” section:

* “Requested” for all incoming requests (yours to approve or not)
* “To Review” **(4)** for requests you need to review
* “History” for all past requests.

In “To Review”, you will be able to approve or reject the request **(5)** with an optional message **(6)** for more details.

![](<../../.gitbook/assets/2019-07-01_15.52.53.png>)

![](<../../.gitbook/assets/2019-07-01_16.00.32.png>)

#### Review past approval requests

All past approval requests - made by you or other approvers - in the History tab **(1)**.

![](<../../.gitbook/assets/2019-07-01_15.59.47.png>)

{% hint style="info" %}
You can export your approval requests history from this tab using the top right button **(2)**.
{% endhint %}

You can get more details on a specific action by clicking on it:

![](<../../.gitbook/assets/2019-07-01_16.05.38.png>)

{% hint style="success" %}
Want to go further with Smart Actions? Read the next page to discover how to make your Smart Actions even more powerful with **Forms**!
{% endhint %}
