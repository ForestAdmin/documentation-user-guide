# Manage your collection settings

Here we'll cover your options to tailor your collections to your needs.

### Access your collection settings

You can access the settings of your collections by activating the layout editor **(1)**, and clicking on the cog icon next to your collection’s names **(2)**.

![](<../.gitbook/assets/2022-01-27_09.50.56.png>)

![](<../.gitbook/assets/2022-01-27_09.51.41.png>)

### General tab

![](<../.gitbook/assets/2022-01-27_10.00.03.png>)

As you can see above, the name `PatientStatus` isn't editable **(1)**, since it's the technical name of the collection introspected by Forest Admin.

If you wish to change that name, you may use the **Display name** field. Here we've named our collection Patient **(2)**. Note that the plural form of the display name you specified is automatically managed, however you can control it by configuring it manually **(3)**.

The **Icon** field allows you to change the icon next to your collection name.

The **Reference field** field enables you to specify how links to a record of that collection should be displayed. For instance in our Live demo, the _Customers_ collection has its reference field set to _fullname_, so that it appears as such any time a reference to a record of this collection is displayed:

![](<../.gitbook/assets/2019-07-01_10.03.14.png>)

{% hint style="info" %}
If no _reference field_ is given, `id` is used to display the reference link.
{% endhint %}

Finally, the **Sorting field** and **Order** fields allow you to manage how you want your collection's data to display at page load. In the image above, we've set them to `updated at` and `descending` respectively, so that going to the Addresses Table View will show your data ordered from most recently _updated_ backward.&#x20;

{% hint style="success" %}
As you can see, the column header shows a **down arrow** which notifies you it is sorted.
{% endhint %}

#### Collection permissions

Collection permissions are managed within [Roles](../project-settings/teams-and-users/manage-roles.md), expect the following UI-related option:

| Permission                              | Meaning                                                                                                                                                                                                  |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Access to records through segments only | (default: `unchecked`) If `checked`, only segments will be accessible. Not the collection itself. If you click on the collection in the side bar, you will be redirected to the first available segment. |

### Other tabs

_Fields_ settings are covered in the [Fields](customize-your-fields/) section.

_Segments_ settings are covered in the [Segments](segments.md) section.

_Smart Actions_ settings are covered in the[ Actions](actions/create-and-manage-smart-actions.md) section.

Smart Views settings are covered in the [Views](../getting-started/master-your-ui/create-and-manage-smart-views.md) section.
