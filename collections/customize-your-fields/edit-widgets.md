# Edit widgets

This page walks you through all available _edit_ widgets settings.

{% hint style="info" %}
For an introduction on what widgets are and a comprehensive list of what widgets you'll be able to choose from, check out the previous page: [Customize your fields](https://docs.forestadmin.com/developer-guide/reference-guide/fields/customize-your-fields)
{% endhint %}

## Text input

Content inputting in its most basic form, the _Text input_ is quite what you will find in most online forms.\
For more advanced or specialized content types, see the other widgets.

## Textarea

Much like the _Text input_, the _Textarea_ widget is more appropriate when inputting longer portions of text.\
To input formatted content, check out the _Rich text editor_ below.

## Rich text editor

This widget is what you need when handling formatted text. You will be able to decorate your text in **bold**, _italic_ and much more.

![](<../../.gitbook/assets/image (421).png>)

## Price editor

This widget is perfect for editing prices, thanks to a real-time preview of what the formatted number will look like:

![](<../../.gitbook/assets/image (626).png>)

To set up your widget:

* Choose a currency symbol between **euros** (EUR), **dollars** (USD) and **pounds** (GBP)
* Choose a base: **Cents** if your values are stored in cents, **Unit** otherwise

![](<../../.gitbook/assets/image (89).png>)

{% hint style="info" %}
The **number formatting** is based on your browser's locale, unless you have a specific [locale](../../project-settings/other-project-settings/general-tab.md#locale) set in your Project settings.
{% endhint %}

## Dropdown

The dropdown is a very powerful and customizable widget. As you would expect, the result will be a dropdown which allows you to choose between several values.

However, you can customize it in the following ways:

### Static

Use _Static_ content type if you want to manually enter your content.

![](<../../.gitbook/assets/image (321).png>)

Your values should be added **manually** - as a comma-separated list -, **unless** you enabled the _Alter values_ option (available in [display settings](./#display-settings)) or if your field is an enum, in which cases you will be able to simply enable/disable values to add them :

!["Alter values" option (display settings)](<../../.gitbook/assets/image (86).png>)

![If "Alter values" enabled or field is an enum](<../../.gitbook/assets/image (542).png>)

### Dynamic

Use this option if you want your content to depend dynamically on your data:

_Simple mode_

![](<../../.gitbook/assets/image (514).png>)

In _Simple mode_, just select which collection you wish to select values from for your dropdown. You can optionally add a filter.

_Dynamic mode_

In Dynamic mode, values will be fetched from your own API endpoint. Here's an example:

{% tabs %}
{% tab title="SQL" %}
![](<../../.gitbook/assets/Screenshot 2019-04-09 at 11.48.31.png>)

{% code title="app.js" %}
```javascript
'use strict';
var express = require('express');
var app = express();
var fs = require('fs');

// ...

// You MUST require these files before the default routes.
fs.readdirSync('./decorators/routes').forEach((file) => {
  if (file[0] !== '.') {
    app.use('/forest', require(`./decorators/routes/${file}`));
  }
});

fs.readdirSync('./routes').forEach((file) => {
  if (file[0] !== '.') {
    app.use('/forest', require('./routes/' + file));
  }
});

app.use(require('forest-express-sequelize').init({
  modelsDir: __dirname + '/models',
  envSecret: process.env.FOREST_ENV_SECRET,
  authSecret: process.env.FOREST_AUTH_SECRET,
  sequelize: require('./models').sequelize
}));

module.exports = app;
```
{% endcode %}

{% code title="decorators/routes/orders.js" %}
```javascript
// Configure the dropdown in dynamic mode using this path: /forest/orders/shippingStatusOptions
const express = require('express');
const router = express.Router();
const Liana = require('forest-express-sequelize');

// This is a simple case but you can retrieve your data from an external API or using your own logic
const data = [
  'Being processed',
  'Ready for shipping',
  'In transit',
  'Shipped',
  'Failed',
];

router.get('/orders/shippingStatusOptions', Liana.ensureAuthenticated, (req, res) => {
  res.send({ data });
});

module.exports = router;
```
{% endcode %}

![The five status are displayed in the drop-down menu.](<../../.gitbook/assets/Screenshot 2019-04-09 at 12.42.21.png>)

{% hint style="info" %}
You can add more logic by retrieving the record id or the record type using `request.context.record.id, request.context.record.type`
{% endhint %}

In the example below, the dropdown will only suggest status according to the current status of the order.

{% code title="decorators/routes/orders.js" %}
```javascript
const express = require('express');
const router = express.Router();
const Liana = require('forest-express-sequelize');
const models = require('../../models');

const STATUS_OPTION_DEFAULT = 'Being processed';
const STATUS_TRANSITIONS = {
  'Being processed': ['Ready for shipping'],
  'Ready for shipping': ['In transit'],
  'In transit': ['Shipped', 'Failed'],
};

router.get('/orders/shippingStatusOptions', Liana.ensureAuthenticated, async (req, res) => {
  const { context } = req.query;
  const recordId = context && context.record && context.record.id;
  let data = [STATUS_OPTION_DEFAULT];

  if (recordId) {
    const order = await models.orders.findById(recordId);
    const currentShippingStatus = order.shippingStatus;
    if (STATUS_TRANSITIONS[currentShippingStatus]) {
      data = STATUS_TRANSITIONS[currentShippingStatus];
    }
  }
  res.send({ data });
});

module.exports = router;
```
{% endcode %}

![Only specific status are displayed based on the previous status of the record.](<../../.gitbook/assets/Screenshot 2019-04-09 at 12.44.02.png>)
{% endtab %}

{% tab title="Mongodb" %}
![](<../../.gitbook/assets/Screenshot 2019-04-09 at 11.48.31.png>)

{% code title="app.js" %}
```javascript
'use strict';
var express = require('express');
var app = express();
var fs = require('fs');

// ...

// You MUST require these files before the default routes.
fs.readdirSync('./decorators/routes').forEach((file) => {
  if (file[0] !== '.') {
    app.use('/forest', require(`./decorators/routes/${file}`));
  }
});

fs.readdirSync('./routes').forEach((file) => {
  if (file[0] !== '.') {
    app.use('/forest', require('./routes/' + file));
  }
});

app.use(require('forest-express-mongoose').init({
  modelsDir: __dirname + '/models',
  envSecret: process.env.FOREST_ENV_SECRET,
  authSecret: process.env.FOREST_AUTH_SECRET,
  mongoose: require('mongoose')
}));

module.exports = app;
```
{% endcode %}

{% code title="decorators/routes/orders.js" %}
```javascript
// Configure the dropdown in dynamic mode using this path: /forest/orders/shippingStatusOptions

const express = require('express');
const router = express.Router();
const Liana = require('forest-express-mongoose');

// This is a simple case but you can retrieve your data from an external API or using your own logic
const data = [
  'Being processed',
  'Ready for shipping',
  'In transit',
  'Shipped',
  'Failed',
];

router.get('/orders/shippingStatusOptions', Liana.ensureAuthenticated, (req, res) => {
  res.send({ data });
});

module.exports = router;
```
{% endcode %}

![The five status are displayed in the drop-down menu.](<../../.gitbook/assets/Screenshot 2019-04-09 at 12.42.21.png>)

{% hint style="info" %}
You can add more logic by retrieving the record id or the record type using `request.context.record.id, request.context.record.type`
{% endhint %}

In the example below, the dropdown will only suggest status according to the current status of the order.

{% code title="decorators/routes/orders.js" %}
```javascript
const express = require('express');
const router = express.Router();
const Liana = require('forest-express-mongoose');
const Order = require('../../models/orders');

const STATUS_OPTION_DEFAULT = 'Being processed';
const STATUS_TRANSITIONS = {
  'Being processed': ['Ready for shipping'],
  'Ready for shipping': ['In transit'],
  'In transit': ['Shipped', 'Failed'],
};

router.get('/orders/shippingStatusOptions', Liana.ensureAuthenticated, async (req, res) => {
  const { context } = req.query;
  const recordId = context && context.record && context.record.id;
  let data = [STATUS_OPTION_DEFAULT];

  if (recordId) {
    const order = await Order.findById(recordId);
    const currentShippingStatus = order.shippingStatus;
    if (STATUS_TRANSITIONS[currentShippingStatus]) {
      data = STATUS_TRANSITIONS[currentShippingStatus];
    }
  }
  res.send({ data });
});

module.exports = router;
```
{% endcode %}

![Only specific status are displayed based on the previous status of the record.](<../../.gitbook/assets/Screenshot 2019-04-09 at 12.44.02.png>)
{% endtab %}
{% endtabs %}

### Relationship

If your field refers to another collection, the dropdown option will automatically populate the data of that collection.\
\
In this example, an **order** `belongs to` a **product**. In **order**'s field settings, you'll find:

![](<../../.gitbook/assets/image (32).png>)

While creating a new order, all products are available in the dropdown:

![](<../../.gitbook/assets/image (577).png>)

You can also **add one or more filters** to display only a dataset of the associated collection.

![](<../../.gitbook/assets/image (385).png>)

In this case, only Star Wars products will be available in the dropdown:

![](<../../.gitbook/assets/image (19).png>)

### Enable search

Say you have a _long list_ of options to choose from. A dropdown becomes a bit _cumbersome_: this is why we've added this option.

![](<../../.gitbook/assets/image (255).png>)

When enabled, the widget becomes an auto-complete input dropdown.

![](<../../.gitbook/assets/image (629).png>)

## Radio button

The radio button widget works the same way as the [dropdown](edit-widgets.md#dropdown) widget: depending on your field type and whether you used the Alter values option (available in [display settings)](./#display-settings), you will have to manually enter your values or simply toggle them.

![Manually entering values](<../../.gitbook/assets/image (325).png>)

!["Alter values" option (display settings)](<../../.gitbook/assets/2020-12-01_15.15.45.png>)

While editing, the widget will look like this:

![](<../../.gitbook/assets/image (267).png>)

## Checkboxes

The checkboxes widget works the same way as the [dropdown](edit-widgets.md#dropdown) widget: depending on your field type and whether you used the Alter values option (available in [display settings)](./#display-settings), you will have to manually enter your values or simply toggle them.

![Manually entering values](<../../.gitbook/assets/image (315).png>)

!["Alter values" option (display settings)](<../../.gitbook/assets/2020-12-01_15.17.17.png>)

While editing, your widget will look like this:

![](<../../.gitbook/assets/image (399).png>)

## File picker

Use this widget to upload files (images, pdf,..). This can be done by clicking on the grey rectangle or drag & drop'ing your file in the grey rectangle.

![](<../../.gitbook/assets/image (361).png>)

### Settings

In your field's settings, you may set the following:

![](<../../.gitbook/assets/image (63).png>)

* _Specific file extensions:_ restrict which file types your users may upload
* _Maximum file size_: set a maximum weight for your files
* _Prefix_: indicate a path to preview your saved files when editing. More on this option [here](display-widgets.md#prefix).

### Edit tools

The File picker widget looks like this:

![](<../../.gitbook/assets/image (353).png>)

When uploading a single image, it allows you to perform 2 basic operations before _using this file_:

* Rotate
* Crop (adjust your image's borders until it fit a desired area)

### Upload multiple files at once

For fields accepting multiple files, a new setting is available: setting a maximum number of files.

![](<../../.gitbook/assets/image (84).png>)

When uploading multiple files at once, your widget will look like this. Note that uploading multiple files at once will prevent you from using the _rotate_ and _crop_ features.

![](<../../.gitbook/assets/image (262).png>)

In the above picture, the _Use these files_ button will become available after removing the first file by clicking the red cross icon.

### Large files upload

If you need to upload large files, you may need to add some code to allow it. Check out [this paragraph](https://docs.forestadmin.com/woodshop/how-tos/import-data-from-a-csv-file#uploading-large-files).

### Date picker

Use this widget if your content is a date.

![To validate these date and time, click outside of the widget](<../../.gitbook/assets/image (580).png>)

{% hint style="info" %}
Depending on your field type, this might be a _Dateonly picker_ widget.
{% endhint %}

### Color picker

Use this widget if your content is a color.

![](<../../.gitbook/assets/image (257).png>)

### JSON editor

Use this widget to handle JSON content.

![](<../../.gitbook/assets/image (368).png>)

## Address

This widget allows you to benefit from [Mapbox](https://www.mapbox.com/)'s address autocompletion.

<figure><img src="../../.gitbook/assets/image (340).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
The full address will be put in a single field (in our above example: _description_)
{% endhint %}

## User dropdown

This widget allows you to input the email address of a user of the current project.\
You may search for a user using their firstname, lastname or email address.

{% hint style="info" %}
The user can then be efficiently displayed using the [User](https://docs.forestadmin.com/user-guide/collections/customize-your-fields/display-widgets#user) _display_ widget.\
\
Both widgets work together to make **record assignment** easily achievable.
{% endhint %}
