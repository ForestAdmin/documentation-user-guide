---
description: >-
  The Table view is the gateway to your data. It shows records as rows and
  their fields as columns.
---

# The Table view

## Search

To search in Forest, use the search bar at the top of the page **(1)**:

![](<../../.gitbook/assets/2022-01-26_17.35.18.png>)

Your search terms are highlighted within the matching results **(2)**.

{% hint style="warning" %}
Only regular fields are searched on. All _reference fields_ of `belongsTo` records are ignored, unless you are using an **extended search**.
{% endhint %}

### Extended search

Lets search for "Lowe":

![](<../../.gitbook/assets/2020-01-17_16.27.33.png>)

We get no result!&#x20;

![](<../../.gitbook/assets/2020-01-17_16.28.26.png>)

The **extended search** lets you search also within _reference fields_ of `belongsTo` records.

![](<../../.gitbook/assets/image (331).png>)

{% hint style="info" %}
_Extended search_ is **not the default** search because it is **slower**.
{% endhint %}

## Filters

Searching is just one way to be faster at finding the desired data. Forest Admin also allows you to use filters to sort your data.

### Sort your data

By clicking on a column’s header **(1)**, you will sort the data by descending then ascending order, depending on the type of data in this field. An arrow **(2)** will appear in the header, showing you that this column is sorted.

![](<../../.gitbook/assets/2019-06-28_16.06.09.png>)

### Add one or several filters

![](<../../.gitbook/assets/2019-08-12_18.16.32.png>)

You can filter your list of records by clicking at the very end of the search bar on ‘Filter’ **(1)**. Or you can also  click on the filter icon in column headers as a shortcut to pre-fill the property you wish to filter on **(2)**.&#x20;

If you notice there is no filter **(3)**: either you have [disabled filtering on this field](../../collections/customize-your-fields/#basic-settings), or it is a Smart Field that does not support filters.

Once opened, the filter management dropdown will look like this:

![](<../../.gitbook/assets/image (388).png>)

{% hint style="info" %}
The list of filtering options available depends on the nature of the selected field.
{% endhint %}

To change the logic between conditions, simply click to toggle between AND and OR.

![](<../../.gitbook/assets/2019-08-12_18.32.27.png>)

Click **Apply filters** for them to be taken into account.

Once applied, you can save filters as segments (learn more about [segments](../../collections/segments.md#what-is-a-segment)).

{% hint style="warning" %}
**Filtering on related data** is available from version 7.3.0 (4.0.0 for Rails).
{% endhint %}

### Understanding filters

Most filters are quite straight-forward. Some, however, require a little more explanation:

#### Date filters

There are many date filters which should let you filter exactly on the time period of your choice, but it can get a little confusing. We've added a tooltip which tells you what the directly within the dropdown:

![](../../.gitbook/assets/docforest.png)

{% hint style="success" %}
Just **hover** a date filter to see how it would apply right now.
{% endhint %}

#### "is blank" vs "is present" (Mongodb only)

In NoSQL orms, there is a difference between:

{% code title="Sample A" %}
```
{ color: "red", size: "" }
```
{% endcode %}

and

{% code title="Sample B" %}
```
{ color: "red" }
```
{% endcode %}

Now imagine a third sample:

{% code title="Sample C" %}
```
{ color: "blue", size: "M" }
```
{% endcode %}

Then the following filter conditions will yield the following results:

| Condition(s)                      | Result(s) |
| --------------------------------- | --------- |
| size is blank                     | A and B   |
| size is present                   | A and C   |
| size is present and size is blank | A         |

## Select

The Table view does not only display your data. It also allows you to interact with it:

{% hint style="info" %}
Forest Admin provides basic CRUD actions out of the box. Check out how you can [duplicate and delete from the Table view](../../collections/actions/#native-actions), but also [create](../../collections/actions/create-a-record.md) and [update](../../collections/actions/edit-a-record.md) from dedicated views.
{% endhint %}

#### Select all records vs Select current page only

On all table views, you'll notice a down caret (▾) next to the top-left header checkbox. Clicking on it lets you choose between selecting all records of the collection or selection only records from the current page:

![](<../../.gitbook/assets/2020-03-05_17.47.07 copie.png>)

Selecting all records has no consequence, however applying an action to all those records might. That's why we've added a warning when you **select all records (1)**:

![](<../../.gitbook/assets/2020-03-05_17.47.19 copie.png>)

{% hint style="info" %}
Having selected all records, you can deselect records from this page only: moving to any another page will deselect all records.
{% endhint %}

Otherwise, you can **select records from current page only (2)** which will select only visible records:

![](<../../.gitbook/assets/2020-03-05_17.47.40 copie.png>)

## Pagination

Navigating the Forest Admin interface is pretty straightforward, and it won’t come as a surprise that our pagination is equally straightforward.

### Browse several pages

Very large collections can’t be displayed on a single page. Where this is the case, you will be able to check the number of records in the collection at the bottom right side of the Table view **(1)**. At the bottom in the middle, you will be able to browse through the different pages of the collection **(2)**.

![](<../../.gitbook/assets/2019-06-28_15.53.01.png>)
