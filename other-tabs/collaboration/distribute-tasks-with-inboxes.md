# Distribute tasks with Inboxes

{% hint style="info" %}
You must [contact a CS]("https://www.forestadmin.com/contact-us?message=Subject: I want to enable the inbox feature") to have access to this feature.
{% endhint %}

The Inbox feature automatically assigns tasks among your team members based, improving the efficiency of your workflows.

## Creating an inbox

Once the feature is enabled for your project, navigate to the Collaboration tab and enable the Edit Layout mode.

In the left menu, find the "Inboxes" section and click "Create Inbox"

An inbox is always based on a segment of a collection. In this example, we will create an inbox based on the `Documents` collection and the `Waiting for Validation` segment, which contains all the documents that have not been verified yet.

You can then select between two dispatch rules:

- "Field based":
  - You can select up to 3 fields.
  - For each field, you can sort ascending or descending.
  - The records will be sorted by the first sorting field, in case of equality, the second sorting field is applied and so on to the third sorting field.
  - For example:
    - You can select the first sorting field to be the create date of the document, sorted descending
    - You can select the second sorting field to be the importance (not sure for this one) of the document, sorted ascending
    - For two `Documents` with the same creation date, the importance will take over for the first that will be assigned
- "Random":
  - The `Documents` will randomly be assigned

## Processing tickets

Once an inbox has been created, access the inbox from the "Collaboration" tab.

### Todo section

The count near the "Todo" section represents the number of records currently in the collection segment selected for the inbox (e.g. `Waiting for Validation`) that have not yet been assigned to an operator.

In the "Todo" section of the inbox, an operator can click on the "Start processing button" to have a task automatically assigned, and being redirected on the record.

The user then does what is necessary to achieve the current workflow, for example trigger a `Validate Document` action. Then the user can click the "Next ticket" button on the top of Forest Admin UI, to be assigned to a new record.

### Doing section

On the "Doing" section, the user can view the tasks that are still in the segment and that are currently assigned to he or she.

### Backlog section

This section is accessible for users with a Editor or Administrator role.

It provides an overview of the current inbox.

You can see all the records in the segment their current task state, and which user is assigned to it.

For the "Doing" tasks, you can see the date when the task was started.

For the "Completed" tasks, you can also see the time it took for the task to get out of the segment. If the records gets out of the segment using an action requiring an approval, it includes the approval time.

### Manual task assignment

Assigning a task to an operator, makes this record be the next one to be assigned for this user, bypassing the sorting rules of the inbox.

It is possible to manually assign a task to a specific user from the [backlog](#backlog-section).

It is also possible to manually assign a task to an operator from the record view, through the native Forest Admin action "Assign to...".

From this action, you can assign a task to users that are not in you current team and also select the inbox. The team should have an inbox based on a segment matching the record state.

## Inbox settings

Inbox settings are accessible from the Edit layout mode.

You can rename and delete inboxes from the settings.

### Organize your inboxes with folders

Inbox folders let you organize the way your inboxes are displayed to your operators.
In the settings, under the "Inbox folder" setting you can add the current inbox in an existing folder, or create a new folder.

### Set a number of maximum concurrent tasks per operators

In the settings you can configure a maximum number of tasks that can be assign at the same time for an operator.

When this number is reached for an operator, when trying clicking on "Next ticket" he or she will be redirected to of the doing tasks.

Tasks manually assigned from the backlog or a record ignore this behavior.

{% hint style="info" %}
This setting is disabled by default
{% endhint %}

### Automatically unassign tasks

You can configure a maximum time before automatically unassigning a task, making the record available for other operators

{% hint style="info" %}
This setting is disabled by default
{% endhint %}
