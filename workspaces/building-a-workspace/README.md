# Building a workspace

Before you can use a workspace, you'll have to build it. To do so, switch to edit mode using the top-right "Edit layout" button.

## Managing components of your workspace

### Adding a component

Components are the bricks of your workspace. To add a component, simply **drag & drop** it from the right-side component menu.

### Renaming a component

Naming your component can help you keep your workspace easy to understand and maintain. Components are given a default name upon creation, but this can be changed from the top-left of the settings panel of your component.

![](<../../.gitbook/assets/image (360).png>)

### Deleting a component

To delete a component, click on the ellipsis icon at the top-right of the settings panel of your component. In the dropdown, select "Delete component".

![](<../../.gitbook/assets/image (358).png>)

{% hint style="warning" %}
Deleting a component may impact other components. If this is the case, you'll be warned before proceeding.
{% endhint %}

## Understanding how components work

### The Text Component

Write anything you wish to display, then customize how it's displayed using the style options.

### The Action Component

The **Action** component can be used to trigger `global,` `single`, and `bulk` Smart Actions as well as CRUD operations.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2022-10-05 at 16.56.40.png" alt=""><figcaption></figcaption></figure>

If you've selected an action that requires selected record(s) to apply to, then you'll need to specify a source component:

Here we have linked the `action2` component so that when you select a record from the`collection1` component, you'll be able to trigger the _Edit a company_ action in 1 click.&#x20;

### The Field Component

The **Field** component lets you read data of a record that you selected in a "source" component.&#x20;

{% hint style="info" %}
**Source** components are components that let you select a record: Collection, Search, Dropdown components can be source components.
{% endhint %}

If you have a Collection component in your workspace, make sure its "On row click" option is set to "Select a record": this will allow you to select a record in your table, which in turn feeds the **Field** component.&#x20;

![](<../../.gitbook/assets/image (109).png>)

In the Field component, select `collection1` as the source and choose which field value you wish to display: here we chose `name`.

![](<../../.gitbook/assets/image (64).png>)

You may have a more complex use case, where you'd want to display a property further away. To achieve this, you'll have to click the _Toggle to input code_ button:

![](<../../.gitbook/assets/2022-10-07_12.18.06 (1).png>)

For instance, if your collection is `Company` and it is linked to a `Country` collection, you may want to display `{{country.name}}` or even `{{country.headquarter.address}}`.

#### Widgets & labels

Note that you may also choose which [widget](../../collections/customize-your-fields/#list-of-display-widgets) to use to display your field.

{% hint style="info" %}
The **(Inherited)** widget will use the same widget used in your Collection settings for this field.
{% endhint %}

Lastly you may also choose whether to display the label and customize it.

### The Search component&#x20;

Use the Search component to quickly select a record within a given Collection:

![](<../../.gitbook/assets/image (81).png>)

With the above settings, you'll be searching within **all fields** of your `Company` records and displaying the [reference field](../../collections/manage-your-collection-settings.md#general-tab).

The Search component can then be used in other components like Field ("on record from"), Text, (templating), Collection (templating in filter), Chart (templating in filter), etc.

### The Dropdown component&#x20;

The Dropdown is a great UI classic. Here's how you can set it up:

Choose a mode between "Static", "Dynamic > Simple" and "Dynamic > Smart"

#### Static

In _Static_ mode, you hard-code values. You may re-order them using the handles.

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
_Enable search_ adds a search to your dropdown, making is easier to find values when there are many.
{% endhint %}

#### Dynamic > Simple

In _Simple_ mode, you choose a collection, a field and optionally a filter: this defines the values that will appear in the dropdown.

![](<../../.gitbook/assets/image (113).png>)

#### Dynamic > Smart

_Smart_ mode lets you fetch values from an external endpoint.

![](<../../.gitbook/assets/image (91).png>)

As explained in the tooltip, the expected response format is:

```
{
    "data": [
        "foo",
        "bar"
    ]
}
```

## Making your components interact

Some of your components display data. You may want this data to influence other components. If you've read the [field component](./#the-field-component) section above, you've seen a simple way to make that happen. But there is another way: using **templating**.\
\
**Templating** is pseudo-code that will fetch the piece of data you want from a component. \
To start using it, simply type `{{` in a text input:

![](<../../.gitbook/assets/image (344).png>)

This opens an autocomplete dropdown which helps you use the correct syntax.

Here are some examples:

<table><thead><tr><th width="340.66545807311365">Templating syntaxe</th><th>Result</th></tr></thead><tbody><tr><td><code>{{collection1.selectedRow.email}}</code></td><td>Displays the column "email" of the select row of collection1</td></tr><tr><td><code>{{currentUser.fullName}}</code></td><td>Displays the current user's fullname</td></tr><tr><td><code>{{currentUser.email}}</code></td><td>Displays the current user's email</td></tr><tr><td><code>{{currentUser.team}}</code></td><td>Displays the current user's team</td></tr><tr><td><code>{{currentUser.tags.some-tag}}</code></td><td>Displays the current user's value of the tag "some-tag"</td></tr></tbody></table>

{% hint style="success" %}
If you rename your components, the syntax adjusts automatically in all components using templating.
{% endhint %}

#### Adding related data

Templating may also be used **in filters** of the Collection component. In practice, this allows you to recreate a related data collection.

![Creating a related data](<../../.gitbook/assets/image (370).png>)

In the example above, we've set up collection1 (`Customer`) and collection2 (`Order`) so that when you click on a **Customer**, it shows **their Orders only** in collection2.

#### Filtering charts

Templating is also useful within the **Chart** component: you may use other components' data to filter on your chart(s).

{% hint style="warning" %}
This feature is only available from version 9.0.0 for Express/Sequelize and Express/Mongoose and version 1.4.0 for agent-nodejs.\
\
If you're seeing this tooltip, you must upgrade first to benefit from the feature\
![](<../../.gitbook/assets/image (460).png>)
{% endhint %}

For instance, if you want to display the number of fast boats belonging to a user, you may use a Collection component in combination with a "Single Value" chart with a filter set up as below:

![](<../../.gitbook/assets/image (476).png>)

Templating also works within **Query** mode, i.e within your SQL queries, like so:

![](<../../.gitbook/assets/image (451).png>)

**Bonus**: it's also possible to use templating in the Timeframe property of Time-based charts. This means that you could for instance create a **Dropdown** component with values _Day_, _Week_, _Month_ and _Year_ and using that dropdown would automatically refresh the chart based on the selected timeframe!&#x20;

This is how you would set it up:

![](<../../.gitbook/assets/image (439).png>)



## Managing visibility of your components

Every component has a `Visible` option - at the bottom of its settings panel - which allows you to control when it is displayed:

<figure><img src="../../.gitbook/assets/image (465).png" alt=""><figcaption></figcaption></figure>

The default choice is **Always**, but there are 2 other options that we'll explain shortly:

* Only when a component is visible
* Only when dynamic variables are defined / Only when source record is selected

### Only when a component is visible

This lets you basically select another component and make your component visible when that other component is.&#x20;

A pretty basic example of this is if you want to show dividers only if the component they are splitting the view for is visible.

Similarly, you can make a Section component hidden unless a component inside of it is displayed.

### Only when dynamic variables are defined / Only when source record is selected

As covered in the [Making your components interact](./#making-your-components-interact) section above, components can be set up to depend on information from another component, using **templating**. This visibility option makes it so that the component is visible only if information from the other component it depends on is available.&#x20;

Here's an example:

![](<../../.gitbook/assets/image (504).png>)

:point\_up: This is a Collection component (`collection2`) that is filtered on another Collection component (`collection1`). See how the filter contains _dynamic variables_ (a.k.a templating)? Well, choosing the "Only when dynamic variables are defined" option means `collection2` will appear only if a record of `collection1` is selected.

{% hint style="info" %}
With the **Always** option, filters containing templating are ignored if undefined.\
\
In practice, this means that in the above screenshot, if Visible was set on Always, `collection2` would ignore its filters unless a record from `collection1` is selected.
{% endhint %}
