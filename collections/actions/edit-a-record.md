# Edit a record

Your data is made up of records which contains fields. Each field can be edited - provided the right permission is set. Here we'll learn how to edit a field.

{% hint style="info" %}
You can set an entire **collection** as _Read only_ in its [General settings](../manage-your-collection-settings.md#general-tab).\
You can set a specific **field** as _Read only_ in its [basic settings](../customize-your-fields/#basic-settings).
{% endhint %}

### From the Details view

To edit a record from the Details view, simply click on the Edit button at the top right.

![](<../../.gitbook/assets/Capture d’écran 2020-01-16 à 23.54.47.png>)

You'll enter an Edit mode where you can change values of editable fields. Don't forget to **Save**!

![](<../../.gitbook/assets/Capture d’écran 2020-01-17 à 00.05.03.png>)

{% hint style="info" %}
A field can be disabled in Edit mode for several reasons:\
• if it's set as [read only](../customize-your-fields/#basic-settings) \
• if it's a [Smart field](broken-reference) with no `set` method
{% endhint %}

### From the Summary view

You can edit from your Summary view just as easily:

![](<../../.gitbook/assets/image (588).png>)

### From the Table view

To edit from the table view ("_inline editing_"), **right-click** on the field you wish to edit:

![](<../../.gitbook/assets/Capture d’écran 2020-02-20 à 11.55.14.png>)

The edit input will look like this:

![](<../../.gitbook/assets/Capture d’écran 2020-02-20 à 11.59.04.png>)

Once you've edited the field:

* Click on _Save_ or press **Enter** to save
* Click on _Discard_ or press **Escape** to cancel any changes and exit the inline edit

:warning:If the field is **read-only**, _Edit_ will appear disabled in the right-click menu:

![](<../../.gitbook/assets/Capture d’écran 2020-02-20 à 14.33.02.png>)

{% hint style="warning" %}
**Belongsto** fields' [reference field](../manage-your-collection-settings.md#general-tab) - which appear in blue and are a link to another record - can neither be edited nor copied. However you can still copy their value "**manually**".
{% endhint %}

### Ajusting the way you edit your data

The above forms can be customized [using the Layout Editor](../../getting-started/master-your-ui/using-the-layout-editor-mode/customize-your-creation-and-edition-forms.md).

Moreover, each field uses a default [edit widget](../customize-your-fields/edit-widgets.md) which can also be changed to better fit your edition need.
