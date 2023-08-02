# Customize your fields

Your fields are what contains your data. They belong to a collection, so in order to customize them, go to your _Collection settings_ by enabling the **Layout Editor mode**.

Here's an example of what you'll see in the _Fields_ tab:

![](<../../.gitbook/assets/2020-07-23_10.09.23.png>)

## Basic settings

As you can see below - **(1)**, you can change how your field's name will be displayed to your users.

![](<../../.gitbook/assets/2020-07-23_10.11.26.png>)

You can also add a _description_ **(2)** which will be displayed when you edit your data via this field.

Other options are also available:

* **Read only**: Enable if you don't want anyone to modify the data of this field.
* **Filtering enabled**: Disable if you don't want anyone to use a filter on this field.

## Edit settings

This section is where you will adjust how you edit this field.\
First, select a **widget (1)**.&#x20;

![](<../../.gitbook/assets/2020-07-23_10.21.14.png>)

{% hint style="info" %}
After selecting a widget, its _settings_ panel should open automatically. You can however reopen that panel at any time by clicking on the cog icon **(2)**.
{% endhint %}

### List of edit widgets

An edit widget is an interface tool which will be displayed when you edit your data. Here are a few examples:

![](<../../.gitbook/assets/image (72).png>)

The list of available _edit_ widgets will depend on the type of your field. Here is the complete list:

| Field type                          | Available edit widgets                                                                                                                                                                                |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| String                              | <ul><li>text input (default)</li><li>textarea</li><li>rich text editor</li><li>dropdown </li><li>radio button </li><li>file picker</li><li>color picker</li><li>JSON editor</li><li>address</li></ul> |
| Enum                                | <ul><li>text input (default)</li><li>dropdown</li><li>radio button </li></ul>                                                                                                                         |
| Number                              | <ul><li>number input (default)</li><li>dropdown</li><li>radio button </li></ul>                                                                                                                       |
| Date                                | date picker                                                                                                                                                                                           |
| DateOnly                            | dateonly picker                                                                                                                                                                                       |
| Array (of string, enum, number,...) | <ul><li>text input (default)</li><li>carousel editor</li><li>checkboxes</li></ul>                                                                                                                     |
| JSON                                | JSON editor                                                                                                                                                                                           |
| Point                               | Text input (default)                                                                                                                                                                                  |
| File reference                      | <ul><li>text input</li><li>file picker (default)</li></ul>                                                                                                                                            |
| Reference                           | <ul><li>default</li></ul>                                                                                                                                                                             |

## Display settings

A display widget is an interface tool which will be displayed when you display your data.

Select a _display_ widget **(1)**.&#x20;

![](<../../.gitbook/assets/2020-07-23_10.41.03.png>)

This is how you will **control how your data is displayed** in your views (table view, summary view, related data views, etc).

{% hint style="info" %}
After selecting a widget, its _settings_ panel should open automatically. You can however reopen that panel at any time by clicking on the cog icon **(2)**.
{% endhint %}

### List of display widgets

The list of available _display_ widgets will depend on the type of your field. Here is the complete list:

| Field type                          | Available display widgets                                                                                                                  |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| String                              | <ul><li>text (default)</li><li>badge</li><li>date</li><li>file viewer</li><li>link</li><li>map</li><li>color sample</li><li>JSON</li></ul> |
| Enum                                | <ul><li>text</li><li>badge (default)</li><li>color sample</li><li>link</li></ul>                                                           |
| Number                              | number                                                                                                                                     |
| Date                                | date                                                                                                                                       |
| DateOnly                            | dateonly                                                                                                                                   |
| Array (of string, enum, number,...) | <ul><li>text (default)</li><li>carousel</li></ul>                                                                                          |
| JSON                                | <ul><li>text</li><li>code snippet (default)</li></ul>                                                                                      |
| Point                               | <ul><li>text</li><li>formatted text</li><li>map (default)</li></ul>                                                                        |
| File reference                      | <ul><li>text</li><li>link to file(s) (default)</li><li>file(s) preview</li></ul>                                                           |
| Reference                           | link to record                                                                                                                             |
