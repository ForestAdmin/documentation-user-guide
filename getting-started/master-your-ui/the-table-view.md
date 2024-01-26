---
description: >-
  The Table View is the gateway to your data. It shows records as rows and
  their fields as columns.
---

# The Table View

## Search

To search in Forest, use the search bar at the top of the page **(1)**:

![](../../.gitbook/assets/2022-01-26_17.35.18.png)

Your search terms are highlighted within the matching results **(2)**.

{% hint style="warning" %}
Only regular fields are searched on. All _reference fields_ of `belongsTo` records are ignored, unless you are using an **extended search**.
{% endhint %}

### Extended search

Lets search for "Lowe":

![](../../.gitbook/assets/2020-01-17_16.27.33.png)

We get no result!&#x20;

![](../../.gitbook/assets/2020-01-17_16.28.26.png)

The **extended search** lets you search also within _reference fields_ of `belongsTo` records.

![](<../../.gitbook/assets/image (331).png>)

{% hint style="info" %}
_Extended search_ is **not the default** search because it is **slower**.
{% endhint %}

### Advanced syntax for search

{% hint style="info" %}
_Advanced syntax for search_ is only supported on nodejs agents `@forestadmin/agent` starting from version 1.37.
{% endhint %}

Search supports advanced syntax to help you find exactly what you are looking for:

- `-term` will search for records that do not contain `term` ;
- `property:term` will search for records that contain `term` in the `property` field ;
- `relation.childProperty:term` will search for records that contain `term` in the `childProperty` field of the `relation` relation ;
- `term1 OR term2` will search for records that contain `term1` or `term2` ;
- `term1 AND term2` will search for records that contain `term1` and `term2` (equivalent to `term1 term2`);
- `term1 AND (term2 OR term3)` will search for records that contain `term1` and either `term2` or `term3`.
- `property:NULL` will explicitly search for records that contain the technical value `NULL` in the `property` field ;
- `"multiple quoted words"` will search for records that contain the phrase `multiple quoted words` without splitting it into multiple terms ;

All elements of the advanced syntax can be combined, for instance `property:term OR -term2 OR relation.childProperty:term3`.

### Search on text fields

Searching on text fields is done differently, depending on the different operators supported by your database. We select the right operator in this order of priority:

1. `Contains (case insensitive)`
2. `Contains (case sensitive)`
3. `Equal`

It means that, in a database that supports the first operator, searching the term `Term` will return all records containing the text `term` even if the case does not match. For instance:

- `TERM` will match
- `abcTERMdef` will also match

#### Searching on numbers

Number fields support the following additional syntax:

- `>42` will search for records that contain a number greater than `42` ;
- `>=42` will search for records that contain a number greater than or equal to `42` ;
- `<42` will search for records that contain a number lower than `42` ;
- `<=42` will search for records that contain a number lower than or equal to `42`.

This syntax can be used in combination with property names, for instance `property:>42` will search for records that contain a number greater than `42` in the `property` field.

#### Searching on dates

Date fields support the following additional syntax:

- `2020` will search for records that contain a date in the year `2020` ;
- `2020-01` will search for records that contain a date in `January 2020` ;
- `2020-01-01` will search for records that contain a date on `January 1st 2020` ;

Operators `>`, `>=`, `<`, `<=` can be used in combination with dates, for instance

- `property:>2020-01-01` will search for records that contain a date after `January 1st 2020` in the `property` field ;
- `property:<=2020` will search for records that contain a date in `2020` or before in the `property` field.

Dates will be considered expressed in the timezone configured in Forest Admin.

#### Searching on booleans

Boolean values support the following additional syntax:

- `true` or `1` will search for records that contain `true` ;
- `false` or `0` will search for records that contain `false` ;

True and false values are case insensitive, meaning that `True` and `False` will also work for instance.

## Filters

Searching is just one way to be faster at finding the desired data. Forest Admin also allows you to use filters to sort your data.

### Sort your data

By clicking on a column’s header **(1)**, you will sort the data by descending then ascending order, depending on the type of data in this field. An arrow **(2)** will appear in the header, showing you that this column is sorted.

![](../../.gitbook/assets/2019-06-28_16.06.09.png)

### Add one or several filters

![](../../.gitbook/assets/2019-08-12_18.16.32.png)

You can filter your list of records by clicking at the very end of the search bar on ‘Filter’ **(1)**. Or you can also click on the filter icon in column headers as a shortcut to pre-fill the property you wish to filter on **(2)**.&#x20;

If you notice there is no filter **(3)**: either you have [disabled filtering on this field](../../collections/customize-your-fields/#basic-settings), or it is a Smart Field that does not support filters.

Once opened, the filter management dropdown will look like this:

![](<../../.gitbook/assets/image (388).png>)

{% hint style="info" %}
The list of filtering options available depends on the nature of the selected field.
{% endhint %}

To change the logic between conditions, simply click to toggle between AND and OR.

![](../../.gitbook/assets/2019-08-12_18.32.27.png)

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

The Table View does not only display your data. It also allows you to interact with it:

{% hint style="info" %}
Forest Admin provides basic CRUD actions out of the box. Check out how you can [duplicate and delete from the Table View](../../collections/actions/#native-actions), but also [create](../../collections/actions/create-a-record.md) and [update](../../collections/actions/edit-a-record.md) from dedicated views.
{% endhint %}

#### Select all records vs Select current page only

On all Table Views, you'll notice a down caret (▾) next to the top-left header checkbox. Clicking on it lets you choose between selecting all records of the collection or selection only records from the current page:

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

Very large collections can’t be displayed on a single page. Where this is the case, you will be able to check the number of records in the collection at the bottom right side of the Table View **(1)**. At the bottom in the middle, you will be able to browse through the different pages of the collection **(2)**.

![](../../.gitbook/assets/2019-06-28_15.53.01.png)
