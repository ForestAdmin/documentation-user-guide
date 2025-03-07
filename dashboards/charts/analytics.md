# Display record-specific charts in Analytics

### Creating a Chart on a specific record <a href="#creating-a-chart-on-a-specific-record" id="creating-a-chart-on-a-specific-record"></a>

Forest Admin’s dashboard is handy when it comes to monitoring the overall KPIs. But you may find the analytics module useful for a more in-depth examination of a specific company, user or any other items.

![](<../../.gitbook/assets/image (381).png>)

{% hint style="info" %}
“Analytics per record” are only supported in the API and Query modes.
{% endhint %}

* For Query charts, in agent v1, use the character `?` to inject the current record the user is currently seeing to your query. Meanwhile in agent v2, you must use `{{recordId}}`.
* For API charts, the parameter `record_id` is automatically passed in the HTTP body to access the record the user is currently seeing.

{% hint style="success" %}
A chart added on a record with such parameters will work for **all records**.
{% endhint %}

{% hint style="info" %}
To enable this feature in agent v2, your developers have to add a connection name into the datasources on which you want to execute live queries chart.

After that, you must select on which one you want to run the query.
{% endhint %}

{% hint style="warning" %}
For **security** reasons, only `SELECT` queries are allowed.
{% endhint %}

#### An example  <a href="#analytics-per-account" id="analytics-per-account"></a>

In the following example, we compute the number of transactions per month for the company “Deliveroo”. The `companies.id` is an integer here, so there’s no need to quote it.

```sql
SELECT DATE_TRUNC('month', transactions.created_at) AS key, SUM(transactions.amount) / 100 AS value
FROM companies
JOIN transactions ON companies.id = transactions.beneficiary_company_id
WHERE companies.id = ?
GROUP BY key;
```

![](<../../.gitbook/assets/2019-07-02_14.30.07.png>)
