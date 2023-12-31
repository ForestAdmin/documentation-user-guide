# Customize the Table View

### Show/hide and reorder fields ​​ <a href="#show-hide-fields" id="show-hide-fields"></a>

You can display only specific fields for a collection and in a given order. When the Edit mode is ON, you will see at the very left end of all column headers a small Cog on an orange background **(1)**. If you click on it you will be able to reorder the fields **(2)** and hide/show the desired ones by clicking on the eye icon **(3)**.

![](<../../../.gitbook/assets/2019-06-28_15.26.04.png>)

### Change the number of records per page&#x20;

By default, 15 records are displayed per page. However, you are free to change this number if needed.

{% hint style="warning" %}
The number of records per page affects the **loading time** of your data, so we recommend not having too many results on a single page. Choose your configuration wisely!
{% endhint %}

To do so, you must use the _Edit Layout_ mode, which is accessible through a button at the upper left side of the Forest Admin interface, then adjust your number of records per page at the bottom right.

![](<../../../.gitbook/assets/2019-06-28_15.56.27.png>)

### Change a collection's _reference field_

Your collections are intertwined. When a collection is linked to another by a `belongsto` relationship, we show its most representative value: we call this its **reference field**.&#x20;

By default it's the `id`, but you may want to change it to something more explicit. This can be done from the linked [collection's General settings](../../../collections/manage-your-collection-settings.md#general-tab), but you use the quick access from the Table View:

![Accessing "Address" collection's reference field setting](<../../../.gitbook/assets/2020-02-20_15.10.20.png>)

### Set a Smart View as your default view

You may have created [Smart View](../create-and-manage-smart-views.md#what-is-a-smart-view) to replace the default Table View of a specific collection. \
\
That Smart View is **not applied by default**. Learn how you can [set it as the default view](../create-and-manage-smart-views.md#applying-a-smart-view).
