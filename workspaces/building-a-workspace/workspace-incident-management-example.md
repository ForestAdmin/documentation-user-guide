# Workspace Incident Management example

In this guide, we will walk you through the creation of a [Workspace for the Incident Management use case](https://app.forestadmin.com/demo-incident-management/Production/Customer%20service/workspaces/9ebfdb30-c636-11ec-94ce-79b648012fd9). The use case is here applied to a ride sharing app, but can be relevant to many other applications!

The goal of this Workspace is to allow support representatives to quickly visualise the latest incidents reported by users, analyse the issue and resolve or escalate them.



![](<../../.gitbook/assets/Screen Recording 2022-07-28 at 18.35.50.gif>)



## Create your Workspace

The first step is to create your first option. In your Forest Admin project, preferably in your staging environment, click on the 🧩 logo and then "Create your first Workspace"

That's it, you've created your first Workspace! You are now in the Workspace drag-and-drop editor.

You can rename it by clicking the 🖊 icon next to "My Workspace".&#x20;

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 15.55.50.png>)



## Add text to guide your users

To make your Workspace clear and guide your users, you can add Text components. Drag and drop the "Text" component from the right bar to the place you want in your Workspace:

![](<../../.gitbook/assets/image (369).png>)

Let's add the title of the workspace for instance. You can choose the color, formatting, size of the text and the text component.

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 15.58.37.png>)

Make your Workspace more personal leveraging the Templating feature, which allows to add dynamic data into a text component. Just start typing `{{` and you'll see available fields to use. In our case, as we're just starting to build our Workspace, the only data available will be the one from the user interacting with the Workspace.

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 16.00.42.png>)

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 16.01.18.png>)



## Add a chart component

One big advantage of Workspaces is that you can mix various components in a single interface. In our case, we want to give support representatives visibility on the types of issues to review. To do so, drag and drop the [Chart ](https://docs.forestadmin.com/user-guide/dashboards/charts/create-a-chart)component from the side bar:

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 16.03.22.png>)

Then, give your chart a name, decide on the chart type. Here we're going with "Distribution" as we want to display the mix of issues.

Choose the collection for which you want to display data, in our case "Issue", and select "Count" for the view.

![](<../../.gitbook/assets/image (371).png>)

Done, you now have a graph. By the way, you can also leverage the Text component to guide your users into how to use your Workspace!

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 18.30.12.png>)

## Add a collection to allow users to manipulate data

Next, let's jump to the heart of our Workspace, the [Collection ](../../collections/manage-your-collection-settings.md)components that will allow users to see the pending incidents, and to review and solve them.

To add a collection to your workspace, select the Collection component from the sidebar:

![](<../../.gitbook/assets/Screenshot 2022-07-11 at 16.23.17.png>)

Place it in your Workspace and resize it as you wish. In the sidebar, select which collection you want to display, in our case "Issue", as well as which [segment](../../collections/segments.md). For this Workspace, we want have a segment of all issues with the "To Review" status

As we'll see later, we are creating a dynamic Workspace, which reacts to which record you select in your collection. So setup the behaviour "Select a record" when users click on a collection's row! Add a text component describing the collection to guide your users, and you're all done.

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 16.23.49.png>)

## Use Field components Templating and Links to make your Workspace actionable

This is how Workspace's magic takes place: make it a dynamic interface for your workflow! We'll create a dedicated section in the Workspace using the Vertical Divider and Text components

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 16.29.15.png>)

Note that we're also using the Templating feature here to dynamically display the category of the issue we're reviewing.

### Dynamically link to relevant information

Use the Link component to allow users to access all the details of a selected issue if necessary.

After you added the Link component to your dashboard, select "Redirect to record" as the URL type, and the correct Source, in our case the select Issue. The link will be dynamically updated according to the selecting record.

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 16.32.18.png>)

### Visualize records' data with the Field component

With the Field component, you can make it easier for your users to check the values of different fields from your collections' records with the Field component.&#x20;

To add a Field component to your Workspace, drag and drop it from the "Data" section in the sidebar.

![](<../../.gitbook/assets/Screenshot 2022-06-23 at 16.01.52.png>)

Now, configure your Field component. In this Workspace, we want to show the details of a selected incident. So select your "Issues" collection as the Field's "source", then the information you want to show as "Field".&#x20;

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 18.27.33.png>)

You can customise the size of the widgets and additional parameters, then click "Save" and you're good to go. Repeat those steps for as many different information types you want to display in your workspace.

![](<../../.gitbook/assets/Screenshot 2022-07-28 at 18.28.38.png>)

And that's it! Now when a support representative will click on a row in the "Issues" collection, they will see the issue's details displayed in the Workspace, and will be able to quickly resolve the issue.
