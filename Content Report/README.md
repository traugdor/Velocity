# Site Navigations

This was created on Cascade Server v7.10

This Content Report format was created for use on [Henderson State University website] [hsu] for the express purpose of displaying all content that was created or modified within the last specified number of days.

## Basic Setup

### Installing the components

Copy `format.vm` into your site in Cascade Server.

### Other setup

#### Additional Components

 - Create an index block named `Content Report`
 - Create a metadata set named `Content Report`
 - A template file containing nothing but `<system-region name=“DEFAULT” />`

This index block should have the following options set

 - Index type: `Folder Index`
 - Depth of Index: `10`
 - Max Rendered Assets: `0`
 - Indexed Asset Types: `Pages; Files`
 - Rendering Behavior: `Render normally, starting at the endexed folder`
 - Page XML: `Render page XML inline only for the current page`
 - Block XML: disabled, leave as is
 - Indexed Asset Content: `Regular Content; System Metadata; User Metadata`
 - Other Indexed Info: `Append Calling Page Data`
 - Sort Method: `Alphabetical`
 - Sort Order: `Ascending`

The Metadata set should have the following options set
 - All metadata fields set to hidden
 - A dynamic metadata field created as so
  * Type of field: `Text`
  * Field is required: `Yes`
  * Visibility: `inline`
  * Name: `days`
  * Label: `Display content newer than number of days:`

#### Putting it all together

 - Create the Template and assign it to a configuration set named `Content Report`
 - Assign the `Content Report` index block to the Block section of the DEFAULT region
 - Assign the Velocity format created from the `format.vm` file to the format region
 - Create a Content Type named `Content Report` and assign the metadata set created earlier and the Configuration Set created earlier.
 - Create a blank page using the content type and set it not to publish or index.

Once this is done, fill in the inline metadata with a whole number greater than 0. Cascade cannot index pages created in the future. This number goes in the slot asking for a number of days.

## Expected output

An exhaustive list of all pages created or modified within the days specified.

## Troubleshooting

#### There are no items in the list

Double check to make sure you input a valid number into the number of days box.

#### There is an error on the page

If there is an error, ensure that your index block is setup appropriately. The format relies on the Calling Page Data as well as the System Metadata and User Metadata.

Also check to make sure that you named the dynamic field in your metadata set correctly. It should be named `days`. This is case-sensitive.

#### My list of pages is truncated

If the list is not showing pages you know were created or modified, try editing the Max Assets in Index Blocks (found by clicking “My Settings” as a user with admin rights and choosing the “Content” tab). You can set a hard limit that is higher than the number of assets in your instance or you can set it to 0 for unlimited. Alternately you can raise the maximum size of the index blocks in MB in the same area.

#### Not all my folders are showing or some folders are empty that I know should contain content

Not every page/asset is listed, only the ones that have been created or modified within a specified number of days. Folders will appear empty if no pages have been edited within that number of days. Increase the number of days to increase the amount of pages shown.

You can also edit your index block and increase the depth of your index. This might also be a good time to restructure your content if you cannot list pages that are buried more than 10 levels down.

[hsu]: http://www.hsu.edu
