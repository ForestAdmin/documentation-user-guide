# Segments

### What is a segment? <a href="#what-is-a-segment" id="what-is-a-segment"></a>

A Segment is a subset of a collection gathering filtered records.

Segments are designed for those who want to _systematically_ visualize data according to specific sets of filters. It allows you to save your filters configuration so you don’t have to compute the same actions every day (e.g. signup this week, pending transactions).

Forest Admin provides a straightforward UI to configure the segments you want step-by-step. The only information Forest Admin needs to create a segment within a collection is a name and some filters.

### Create simple Segments

To create a new segment, activate the Layout Editor mode **(1)** on the top right part of your screen and click on the cog just next to the collection you want to edit **(2)** and select the _Segments_ tab **(3).**&#x20;

![](<../.gitbook/assets/Capture d’écran 2019-07-01 à 16.59.51.png>)

At this point there are 2 possibilities:

If you have never created any segment for this collection, click the "Create your first segment" **(4)**.

Otherwise, click the "+ New segment" link **(5)**.

![](<../.gitbook/assets/Capture d’écran 2019-07-01 à 17.02.33.png>)

To create your segment, give it a name **(6)** and add 1 or more filter(s) **(7)**. \
You can also adjust your **sorting** **field** and **order** [like you would for a collection](manage-your-collection-settings.md#general-tab).

### Create SQL Query Segments

Forest Admin gives you a second option to create segment: SQL queries.&#x20;

{% hint style="warning" %}
**Query** **mode** is only available for databases which support SQL.\
\
For **security** reasons, only `SELECT` queries are allowed.
{% endhint %}

SQL queries allow you to create advanced filters and connect your data through a few lines of code if you know how SQL queries work.

Simply switch to **Query** mode **(1)**, type in your SQL query **(2)** and save.

![](<../.gitbook/assets/Capture d’écran 2019-07-01 à 17.19.49.png>)

{% code title="QUERY" %}
```sql
SELECT t.id FROM transactions t
JOIN companies beneficiary ON t.beneficiary_company_id = beneficiary.id
JOIN companies emitter ON t.emitter_company_id = emitter.id
WHERE beneficiary.headquarter ILIKE '%United States%' AND emitter.headquarter ILIKE '%United States%'
```
{% endcode %}

{% hint style="warning" %}
The returned column **must** be `id` .&#x20;
{% endhint %}

In the above example, we display the transactions whose beneficiaries and emitters are in the United States.

{% hint style="info" %}
If you want to make a SQL segment based on several databases, you can use the [dblink function](https://www.postgresql.org/docs/10/contrib-dblink-function.html) for postgreSQL.
{% endhint %}

### Organize your workflows through with the layout editor ​

Usually, you want the organization of your segments to match the sequencing of your business workflows. To do so, you can **reorder** your segments using the Layout Editor mode just [like you would for collections](../getting-started/master-your-ui/using-the-layout-editor-mode/#reorder-collections-and-fields).

![](<../.gitbook/assets/Capture d’écran 2019-07-01 à 17.30.22.png>)

{% hint style="warning" %}
By default, newly created segments are **disabled**.
{% endhint %}
