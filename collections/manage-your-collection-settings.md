# Manage your collection settings

Here we'll cover your options to tailor your collections to your needs.

### Access your collection settings

You can access the settings of your collections by activating the layout editor **(1)**, and clicking on the cog icon next to your collection’s names **(2)**.

![](<../.gitbook/assets/Capture d’écran 2022-01-27 à 09.50.56.png>)

![](<../.gitbook/assets/Capture d’écran 2022-01-27 à 09.51.41.png>)

### General tab

![](<../.gitbook/assets/Capture d’écran 2022-01-27 à 10.00.03.png>)

As you can see above, `PatientStatus` isn't editable **(1)**, since it's the name of a table in your database. In Forest Admin, a table shows up on the left side bar as a _collection_.

If you wish to change that name, you may use the **Display name** field. Here we've named our collection Patient **(2)**. Note that the plural form of the display name you specified is automatically managed, however you can control it by using **(3)**.

The **Icon** field allows you to change the icon next to your collection name.

The **Reference field** field enables you to specify how links to a record of that collection should be displayed. For instance in our Live demo, the _Customers_ collection has its reference field set to _fullname_, so that it appears as such in other collections:

![](<../.gitbook/assets/Capture d’écran 2019-07-01 à 10.03.14.png>)

{% hint style="info" %}
If no _reference field_ is given, `id` is used to display the link
{% endhint %}

Finally, the **Sorting field** and **Order** fields allow you to manage how you want your collection's data to display at page load. In the image above, we've set them to `updated at` and `descending` respectively, so that going to the Addresses table view will show your data ordered from most recently _updated_ backward.&#x20;

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



