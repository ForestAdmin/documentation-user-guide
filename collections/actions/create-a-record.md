# Create a record

To create a new record, click the **Add** button from the Table view.

![](<../../.gitbook/assets/Capture d’écran 2020-01-17 à 00.18.43.png>)

{% hint style="warning" %}
There's no **Add** button? Record creation might be [disabled](../manage-your-collection-settings.md#collection-permissions).
{% endhint %}

Once on the creation form, fill out all required fields as per your database's constraints:

![](<../../.gitbook/assets/Capture d’écran 2020-01-17 à 12.56.51.png>)

{% hint style="info" %}
This form can be customized. Check out [this section](../../getting-started/master-your-ui/using-the-layout-editor-mode/customize-your-creation-and-edition-forms.md#customizing-a-creation-form) to do so.
{% endhint %}

When creating a record, you can also link an _existing_ `belongsTo` records **(1)** or create a _new_ one **(2)**.

You can also add existing **(4)** or new **(5)** `hasMany` records from its _Related data_ collections **(3)**:

![](<../../.gitbook/assets/Capture d’écran 2020-01-17 à 16.03.06.png>)

{% hint style="info" %}
If the `orders` field of collection _Customers_ is **read-only**, you won't be able to add any order.
{% endhint %}

{% hint style="warning" %}
Disabling **record creation** for collection Orders will remove "Create new order" **(5)** in this creation form. However you'll still be able to "Add existing order" **(4)**.
{% endhint %}
