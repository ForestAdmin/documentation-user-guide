# Manage roles and permission levels

## Roles <a href="#roles" id="roles"></a>

Roles can be created **(1)** in the _Roles_ tab of your project settings:‌

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MNKoQqHaS-Lnznag76U%2F-MNKqQtM7TOIj45vKjSl%2FCapture%20d%E2%80%99e%CC%81cran%202020-11-29%20a%CC%80%2022.10.51.png?alt=media\&token=49e34003-e934-453d-b7f3-2e88b817afba)

To manage a role's permissions, click on it **(2)**:

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MMaKOqJ\_wpBuC7BX4zs%2F-MMaKw\_feeQ-8YEp13b\_%2Fimage.png?alt=media\&token=b8b16ddd-d961-4062-b2ee-a2b7d7661e31)

{% hint style="warning" %}
If your project was created before February 2021, please visit [this page](https://docs.forestadmin.com/documentation/how-tos/maintain/migrate-to-the-new-role-system) to learn how to enable this feature.
{% endhint %}

The above screenshot shows your role's details page. This is where you'll be managing all permissions which should apply to all the users assigned to this role.‌

Permissions are displayed in 2 sections:‌

* _Smart Action permissions_
* _Collection permissions_

### Smart Action permissions <a href="#smart-action-permissions" id="smart-action-permissions"></a>

This section lets you to easily manage your Smart Action permissioins (for this role **only**). Click _Show more_ **(1)** to display all permissions, or _Edit permissions_ **(2)** to directly edit its Smart Action permissions.‌

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MNL8RDssS14SucKOxhW%2F-MNL8dVEaQPf3Gt2l6Dt%2FCapture%20d%E2%80%99e%CC%81cran%202020-11-29%20a%CC%80%2023.33.19.png?alt=media\&token=a977faf6-54ec-4fc0-9a99-b7422b4a3792)

* Trigger: Allow users assigned to this role to trigger this Smart Action

#### Approval workflow permissions <a href="#approval-workflow-permissions" id="approval-workflow-permissions"></a>

If you are using our approval workflow feature, your approval permissions are also managed within roles.‌

The following options become available if you are on the [Pro](https://www.forestadmin.com/pricing) plan or above:‌

* _Require approval_: Unlike Trigger, the Smart Action will not be executed unless manually approved
* _Approve_: Allow users assigned to this role to [approve a trigger request](../../collections/actions/create-and-manage-smart-actions.md#review-approval-requests)​
* _Self Approve_: Allow users assigned to this role to approve their own trigger request

<figure><img src="../../.gitbook/assets/image (492).png" alt=""><figcaption></figcaption></figure>

#### Conditional permissions <a href="#collection-permissions" id="collection-permissions"></a>

{% hint style="info" %}
In addition to the **Pro** plan, this feature requires a minimum agent version to be installed.
{% endhint %}

Your processes likely depend on your data: for instance, a $1,000 refund is more sensitive than a $10 refund. You probably want to authorize your operators to trigger $10 refunds, but not $1,000 or more. This is now possible within the permissions page:

<figure><img src="../../.gitbook/assets/image (437).png" alt=""><figcaption></figcaption></figure>

To achieve this, go to the permissions edit page and click on the filter icon:

<figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Permission changes may take up to **15** minutes to apply.
{% endhint %}

That's it! Your operators may now refund without approval for an amount up to $1,000, but any refund of a higher amount will require an approval.

{% hint style="info" %}
The same feature is available for **Trigger** and **Approve** permissions: use the corresponding filter icons to input the conditions you want.
{% endhint %}

### Collection permissions <a href="#collection-permissions" id="collection-permissions"></a>

![](<../../.gitbook/assets/image (544).png>)

_Collection permissions_ allow you to enable/disable the following collection-specific permissions:‌

* _Read (list)_: access to the collection's [Table View](../../getting-started/master-your-ui/the-table-view.md) data. Note that the collection must also be [shown in the layout](../../getting-started/master-your-ui/using-the-layout-editor-mode/) to be displayed.
* _Read (details)_: access to the [Details View](../../getting-started/master-your-ui/using-the-layout-editor-mode/customize-the-details-view.md) (and Summary View) data of any record of this collection.
* _Create_: create a record of this collection (N.B: the "Duplicate" action is also managed by this permission)
* _Update_: update a record of this collection
* _Delete_: delete a record of this collection
* _Export_: export the list of records of this collection

### Control environment access per role <a href="#control-environment-access-per-role" id="control-environment-access-per-role"></a>

From a role's details page, you can also:‌

* &#x20;toggle which environments users assigned to this role have access to **(1)**
*   select which environment you wish to view permissions of or edit them **(2)**

    ​

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MNLEdL3DsRwZtcPE3Y8%2F-MNLHgbJt8yyjtjbegaE%2FCapture%20d%E2%80%99e%CC%81cran%202020-11-30%20a%CC%80%2000.13.58.png?alt=media\&token=25e11968-7174-4b9a-90c6-570b8cf37e05)

**Only remote environments** are available here, since development environments have all permissions‌.

### Export role permissions <a href="#export-role-permissions" id="export-role-permissions"></a>

At anytime you may export your user role permissions to a CSV file by clicking on _Export user permissions_ from the _Users_ tab:‌

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MLweVxJZ9hplEwP4DBy%2F-MLweruzQ-hpmhdUOe5e%2FCapture%20d%E2%80%99e%CC%81cran%202020-11-12%20a%CC%80%2014.34.46.png?alt=media\&token=4267a170-093e-45ef-8d91-5ed3ca9460f3)

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MLw\_8zLAMrECE3UR252%2F-MLwdtJp4dUTFe-1CuHN%2FCapture%20d%E2%80%99e%CC%81cran%202020-11-12%20a%CC%80%2014.06.02.png?alt=media\&token=71b59490-63ee-4bb2-8758-099232387859)

It contains User information **(1)**, Smart Action name **(2)** and Collection name **(3).** Granted permissions **(4)** are as follows:‌

* _empty_: the user is not authorized to use that Smart Action as part of that team
* _trigger_: the user can trigger that Smart Action
* If the [approval workflow module](../../collections/actions/create-and-manage-smart-actions.md#require-approval-for-a-smart-action) is enabled:
  * _request_: the user can ask for an approval to trigger that Smart Action
  * _request/approve_: the user can ask for an approval to trigger that Smart Action and can approve requests of this Smart Action except his own
  * _request/approve(self)_: the user can ask for an approval to trigger that Smart Action and can approve requests of this Smart Action including his own

### Copy role permissions across environments

Setting up role permissions can take a lot of time, especially if you need to do it all over again for another environment.

This is why we've implemented the "Copy role permissions across environments" feature. In a few clicks, you can apply the permissions of **all roles** of an environment to another environment.

To use it, go to: Project Settings -> Roles -> Actions.

![](<../../.gitbook/assets/image (617).png>)

{% hint style="info" %}
This feature is only available to the **Admin** permission level.
{% endhint %}

## Permission level <a href="#permission-level" id="permission-level"></a>

The permission level of a user determines what Forest Admin administration permissions he has. You can assign one of the following _permission levels_ per user:‌

| Forest Admin permission level | Manage Data               | Customize admin UI (activate layout editor) | Access project settings (environments only) | Access project settings (environments, teams, user roles) |
| ----------------------------- | ------------------------- | ------------------------------------------- | ------------------------------------------- | --------------------------------------------------------- |
| **Admin**                     |     :heavy\_check\_mark:  |        :heavy\_check\_mark:                 |             :heavy\_check\_mark:            |               :heavy\_check\_mark:                        |
| **Developer**                 |     :heavy\_check\_mark:  |        :heavy\_check\_mark:                 |             :heavy\_check\_mark:            |                                                           |
| **Editor**                    |     :heavy\_check\_mark:  |        :heavy\_check\_mark:                 |                                             |                                                           |
| **User**                      |     :heavy\_check\_mark:  |                                             |                                             |                                                           |

## Manage a user's role and permission level <a href="#manage-a-users-role-and-permission-level" id="manage-a-users-role-and-permission-level"></a>

You can change a user's role or permission level from their details page:‌

1. Go to the _Users_ tab of your Project settings
2. Click on a user in the list
3. Change the role and/or permission level assigned to that user
4. Don't forget to save

![](https://gblobscdn.gitbook.com/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-MKKUnOvF9h4T2t0c\_vi%2F-MKKxu9dgVLyFlA7VYV3%2FCapture%20d%E2%80%99e%CC%81cran%202020-10-23%20a%CC%80%2016.56.58.png?alt=media\&token=08c9126f-383d-4857-9107-d3df61c6c848)
