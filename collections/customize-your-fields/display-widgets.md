# Display widgets

This page walks you through all available _display_ widgets settings.

{% hint style="info" %}
For an introduction on what widgets are and a comprehensive list of what widgets you'll be able to choose from, check out the previous page: [Customize your fields](./)​
{% endhint %}

## Text <a href="#text" id="text"></a>

This is the most basic way to display your content (depending on your field type). If you want to take into account text formatting, check out the next section.

## Date <a href="#date" id="date"></a>

In Forest Admin, your ability to manage your data extends to customizing how dates and times are displayed in your interface. This is particularly useful when standard date formats don't fit your needs or you want to provide a more locale-specific representation.

We utilize [Moment.js](https://momentjs.com/), a powerful tool that provides a simple way to format dates and times. You don't need to understand programming or the ins and outs of Moment.js to make use of it. It's as easy as entering a combination of special tokens into the date format field in the Forest Admin UI.

For instance, if you want to display your dates in a full descriptive format like "Wednesday, May 10th 2023, 8:02:17 am", you would enter the format string "dddd, MMMM Do YYYY, h:mm:ss a" directly into the date format field.

With this widget, you can control how your dates will be displayed:

![](<../../.gitbook/assets/image (284).png>)

To customize your date format, use [Moment.js](https://momentjs.com/) syntax:

![](<../../.gitbook/assets/2019-07-01_11.46.22.png>)

Here's what each token represents:

* "M" => Returns "5" - representing the current month
* "Mo" => Returns "5th" - the current month in ordinal form
* "MM" => Returns "05" - the current month with a leading zero
* "MMM" => Returns "May" - the shorthand name of the current month
* "MMMM" => Returns "May" - the full name of the current month
* "Q" => Returns "2" - the current quarter of the year
* "Qo" => Returns "2nd" - the current quarter in ordinal form
* "D" => Returns "10" - the current day of the month
* "Do" => Returns "10th" - the current day in ordinal form
* "DD" => Returns "10" - the current day with a leading zero
* "ddd" => Returns "Wed" - the shorthand name of the current day of the week
* "dddd" => Returns "Wednesday" - the full name of the current day of the week
* "A" => Returns "AM" or "PM" - the current period of the day
* "a" => Returns "am" or "pm" - the current period of the day in lowercase
* "H" => Returns "8" - the current hour in 24-hour format
* "HH" => Returns "08" - the current hour with a leading zero
* "h" => Returns "8" - the current hour in 12-hour format
* "hh" => Returns "08" - the current hour in 12-hour format with a leading zero
* "m" => Returns "2" - the current minute
* "mm" => Returns "02" - the current minute with a leading zero
* "s" => Returns "17" - the current second
* "ss" => Returns "17" - the current second with a leading zero
* "S" => Returns "0" - the first fractional second (if any)
* "Z" => Returns "-05:00" - the offset from UTC
* "ZZ" => Returns "-0500" - the offset from UTC without a colon separator
* "X" => Returns a Unix timestamp (the number of seconds that have elapsed since 01 January, 1970 UTC)

By using these tokens, you can have complete control over how dates and times are presented, making it easier and more intuitive to read and interpret your data in Forest Admin.

Here are five examples of various date and time formatting possibilities in Forest Admin:

1. **"Do MMM, YYYY"**
   * This will return the date in a format like "10th May, 2023". It uses the day of the month in ordinal form, the shorthand name of the month, a comma, and the full year.
2. **"dddd, hA"**
   * This will return something like "Wednesday, 8AM". It's a simple format that includes the full name of the day of the week, followed by the hour in 12-hour format and the period of the day in uppercase.
3. **"YYYY-MM-DD HH:mm"**
   * This format will provide a date and time like "2023-05-10 08:02". It's a standard and commonly used format, especially in data storage and technical applications. It includes the full year, the month and day with leading zeros, and the hour and minute in 24-hour format with leading zeros.
4. **"MMM Do, h:mm a"**
   * This format will return "May 10th, 8:02 am". It uses the shorthand name of the month, the day in ordinal form, and the hour and minute in 12-hour format with the period of the day in lowercase.
5. **"Qo quarter, YYYY"**
   * This will return something like "2nd quarter, 2023". It's an interesting format that shows the current quarter in ordinal form and the full year. This could be useful for financial or business applications where data is often considered on a quarterly basis.

## Price

This widget allows you to display a number as a nicely formatted price:

![](<../../.gitbook/assets/image (102).png>)

* Choose a currency symbol between **euros** (EUR), **dollars** (USD) and **pounds** (GBP)
* Choose a base: **Cents** if your values are stored in cents, **Unit** otherwise

![](<../../.gitbook/assets/image (71).png>)

{% hint style="info" %}
The **number formatting** is based on your browser's locale, unless you have a specific [locale](../../project-settings/other-project-settings/general-tab.md#locale) set in your Project settings.
{% endhint %}

## Percentage

This widget is useful to display a number (ranged between 0 and 1) as a percentage.

Without using the percentage widget:

![](<../../.gitbook/assets/image (636).png>)

Using the percentage widget:

![](<../../.gitbook/assets/image (613).png>)

{% hint style="info" %}
If you manually **search** for a percentage value, you should type the unformatted value, as shown below.
{% endhint %}

![](<../../.gitbook/assets/image (643).png>)

## File viewer

This widget is your go-to widget for viewing files of all types.

![](<../../.gitbook/assets/image (17).png>)

{% hint style="warning" %}
Previews are only available for images and PDFs.
{% endhint %}

### Images

Images can be previewed from all views. Click on them to display the following modal:

![](<../../.gitbook/assets/image (138).png>)

From this modal, you can:

* **Click** to zoom
* **Scroll** to zoom in
* **Drag & drop** your zoomed-in area

{% hint style="info" %}
The _File viewer_ widget will also act as a **carousel** when viewing multiple images or files. In this case, your field must be defined as an array of strings (`type: ['String']`).
{% endhint %}

{% hint style="warning" %}
Your images need to be **public** to be displayed!\
If you must keep them **private**, you should consider using [signed URLs](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-signed-urls.html).
{% endhint %}

### PDFs

From the Table View, clicking on the file icon will open the PDF in a new tab.

![](<../../.gitbook/assets/2019-07-01_12.08.02.png>)

From the summary and Details Views, the PDF can be previewed:

![](<../../.gitbook/assets/image (230).png>)

{% hint style="danger" %}
If your PDF seems to be loading indefinitely, it might be protected (you'll see a `Load denied by X-Frame-Options` error in your console).

This can be solved by adding&#x20;

`X-Frame-Options: ALLOW-FROM https://app.forestadmin.com/`

in your file hosting server (replace `https://app.forestadmin.com` by your custom domain if you have one).
{% endhint %}

### Settings

In this widget's settings, you can manage whether to authorize rotation and zoom features, add a prefix and change the preview size.

![](<../../.gitbook/assets/image (223).png>)

### Prefix

Use this option to specify a URL prefix or path prefix depending on your usage. For instance:

* If you store your files on an external cloud (ie: AWS S3) and in your database as a **filename**, your prefix will be a link like this:

![](<../../.gitbook/assets/2019-04-15_09.24.25.png>)

* If you store your images in **base64**, you could find it convenient to add a `data:image/png;base64` prefix on the go:

![](<../../.gitbook/assets/2019-04-19_11.28.29.png>)

### Preview size

Choosing a preview size will show your image or PDF in the following sizes:

![Small (max-height: 150px)](<../../.gitbook/assets/image (139).png>)

![Medium (max-height: 400px)](<../../.gitbook/assets/image (245).png>)

![Large (max-height: 1000px)](<../../.gitbook/assets/image (256).png>)

{% hint style="info" %}
_Custom_ allows you to specify a precise height and width in pixels.
{% endhint %}

## Link <a href="#link" id="link"></a>

Select this widget if your content is actually URLs.

![](<../../.gitbook/assets/image (232).png>)

{% hint style="info" %}
Links will always **open in a new tab**.
{% endhint %}

Note that if your content is not a valid url, it will still be clickable but simply show a blank page.\
\
You can also choose to display a title instead of the link.&#x20;

![](<../../.gitbook/assets/Screenshot 2020-01-07 at 11.54.05.png>)

## Map <a href="#map" id="map"></a>

Select this widget if you want to visualize a point coordinates on a map.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-L\_II7LUdAOkcJsUNFZy%2F-L\_IJblBj02ohUaAKIYi%2Fimage.png?alt=media\&token=74be70cf-ba69-46e6-b51f-d9adad61278d)

{% hint style="info" %}
Coordinates format must be:\
\- 48.8566, 2.3522 :white\_check\_mark: \
\- 48.8566° N, 2.3522° E :x:&#x20;
{% endhint %}

## JSON

Use this widget to neatly display your JSON.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LR7SWfEwsNtj\_ZiSkSA%2F-L\_II7LUdAOkcJsUNFZy%2F-L\_IJf1dCciE4jukwKma%2Fimage.png?alt=media\&token=70c5565a-e205-44ff-8b60-2bc6f7753c29)

## User

{% hint style="info" %}
Use this _display_ widget with the [User dropdown](https://docs.forestadmin.com/user-guide/collections/customize-your-fields/edit-widgets#user-dropdown) _edit_ widget for optimal results.
{% endhint %}

This widget detects emails of existing Forest Admin users of your project and displays their profile picture:

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

Here are the possible cases:

* **(1)** : the user belongs to the project. The profile picture is composed of his initials.
* **(2)** : the user belongs to the project and has a [gravatar](https://gravatar.com/).&#x20;
* **(3)** : the field is empty. Notice that you may assign it simply by clicking on it.
* **(4)** : the user doesn't belong to this project.&#x20;

Notice that you may assign **multiple users** if your field is an **array** of emails:

<figure><img src="../../.gitbook/assets/image (497).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
At any time, you may display additional information on the user by **hovering** the profile picture.
{% endhint %}
