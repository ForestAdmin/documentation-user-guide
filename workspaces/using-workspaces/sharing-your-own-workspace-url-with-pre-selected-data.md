# Sharing your own Workspace URL with pre-selected data

Imagine you're in the middle of a task on Workspaces, you have filtered a collection and picked the desired records, selecting the most interesting tab for this case, etc.

The only thing is that you have to leave, and let one of your coworkers do the rest.&#x20;

You can simply copy the URL of the Workspace you're currently working on, and send it to your colleague. He or she will be able to pick-up your work exactly from where you left it off.&#x20;

Check the example below.

{% embed url="https://www.loom.com/share/b72dad909a5041ec8e749cd458053cbc" %}

## How to build the URL myself?

Forest Admin now incorporates the context of workspace components directly into the URL. This feature allows you to construct a URL that reflects a highly specific state of a workspace, thus enabling you to guide users to a detailed workspace scenario.

This enhancement proves especially beneficial when redirecting users from external tools to Forest Admin. With this capability, users can arrive at a workspace that is already pre-populated with the appropriate context, including selected records, filters, and more, thereby creating a streamlined and intuitive user experience.

### **URL Construction**

The query parameters of the URL are constructed this way: `<componentName>.<attribute>=<value>`

For instance, here's how you can encode a URL:

```jsx
encodeURI('<https://app.forestadmin.com/Library/Development/Operations/workspaces/615546e6-e0ea-4c8e-98fa-a4e0bc9dc8d1?component1.selectedRecords=[1,2]&component1.search="search something">')
```

This will result in the following encoded URL:

```jsx
<https://app.forestadmin.com/Library/Development/Operations/workspaces/615546e6-e0ea-4c8e-98fa-a4e0bc9dc8d1?component1.selectedRecords=%5B1,2%5D&component1.search=%22search%20something%22>'
```

### **Component Parameters**

Each component type can have specific parameters:

* **Toggle**:
  * **`isToggled`**: This is a boolean and should only be set when it's different than the default.
* **Search**:
  * **`selectedRecords`**: This is an array that contains the selected record ID (string). Note that only one record should be in the array for the search.
* **Dropdown**:
  * **`selectedValue`**: This is a string that represents the selected value.
* **Tabs**:
  * **`tabIndex`**: This is a number that represents the index of the selected tab.
* **Collection**:
  * **`selectedRecords`**: This is an array that contains the selected record IDs (strings).
  * **`areAllRecordsSelected`**: This is a boolean indicating whether all records are selected. If this option is set to **`true`**, **`selectedRecords`** should not be set. This option is set with "Select all records".
  * **`excludedRecords`**: This is an array that contains the IDs of unselected records (strings). This should be set if at least one record is unselected with "Select all record".
  * **`currentPage`**: This is a number representing the current page (if it's greater than 1).
  * **`search`**: This is a string that contains the search value.
  * **`isSearchExtended`**: This is a boolean that represents if the search has been extended.
  * **`segmentId`**: This is a string that represents the selected segment ID. This is only required if the selected segment is different than the one configured by default.
  * **`filter`**: This is a JSON object with the following structure:

```json
{
  "type": "and" / "or",
  "conditions": [
    {
      "operator": "is",
      "value": "valueOfCondition",
      "fieldName": "fieldName"
    }
  ]
}
```

By effectively utilizing these query options, you can customize workspaces to suit your specific needs in Forest Admin, and share it even though it is not done yet.
