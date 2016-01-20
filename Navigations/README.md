# Site Navigations

This was created on Cascade Server v7.10

This navigation format was created for use on [Henderson State University website] [hsu] for the express purpose of having localized, dynamic navigations for the appropriate sections of the website. This navigation format will search, based on the folder structure of the page that is displaying it, for a navigation from a specific, indexed folder that matches either the folder the page is in, or a parent folder. If neither match it will try to match according to the first folder the page is nested in. Should this also fail, it will default to a "Main Navigation" to avoid displaying nothing.

## Basic Setup

### Installing the components

Copy `format.vm` and `data-definition.xml` into your site in Cascade Server.

### Other setup

#### Additional Components

 - Create a folder named `navigations`
 - Create an index block named `navigations-index`

This index block should have the following options set

 - Index type: `Folder Index`
 - Depth of Index: `1`
 - Max Rendered Assets: `0`
 - Indexed Asset Types: `Blocks`
 - Rendering Behavior: `Render normally, starting at the endexed folder`
 - Page XML: `Do not render page XML inline`
 - Block XML: `Render XHTML/Data Definition block, XML block, and Text block XML inline`
 - Indexed Asset Content: `Regular Content; System Metadata`
 - Other Indexed Info: `Append Calling Page Data`
 - Sort Method: `Alphabetical`
 - Sort Order: `Descending`
 
#### Putting it all together

 - Create an XHTML/Data Definition block in the `navigations` folder.
 - Assign the Data Definition created from `data-definition.xml` to the block.
 - Fill out the content of the block. Click the `+` icon to create more than one link in the navigation.

The System Name of the new block should exactly match the System Name of the folder from which pages will display this navigation. This is case-sensitive.

Finally:

 - Create a new region in your template where you would like the navigation to appear.
 - Assign `navigations-index` to the block section and the format you copied earlier into the format section.
   * This can be done at the Template or Configuration Set level depending on how you plan to reuse your template.

It is advised to create a `Main Navigation` block before continuing or the format will fail. This block can be empty or have only one link but is needed to ensure that the format has something to fall back on in case it cannot find the navigation for the folder your pages are in.

## Expected output

Browsing to a different page asset in Cascade Server should automatically load the navigation from the Navigations folder you created earlier.

## Troubleshooting

If the Main Navigation is always shown, ensure that the system name of the navigation matches the system name of the folder your page is in.  
If nothing is shown or the page loads with an error in Cascade Server, double check all setting and that all the pieces are in place and that the system names of the navigations are correct.

[hsu]: http://www.hsu.edu