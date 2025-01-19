#software/windows
# DopStack





**Installation:**

*   Download: (1.5.3 requires DOpus 12.21) [DopStack.osp](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/uploads/short-url/1QODszTnezPKAPlG72w8nSoyQnK.osp) (139.6 KB)
*   Drag the .js.txt file to Preferences / Toolbars / Scripts.

**Usage:**

*   Download: [Dop Stack.dcf](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/uploads/short-url/u0GXo0RrdwqPvR2UtstkvsiqrLz.dcf) (677 Bytes)
*   Select "Settings / Customize Toolbar..." from your Lister and then drag the button file to any toolbar you like. Left click the button to open DopStack and if you're running DOpus 12.20.6 or better you can right click the button to open the configuration for DopStack.

Use the command line argument **STACKLABEL** to override the initial Stack Label in your configuration, which will be useful if you want to run multiple instances with preconfigured labels.  
e.g: `DopStack STACKLABEL="My Stack"`  
You can extend this further so that the button will ask for a stack label each time it's run:  
`DopStack STACKLABEL="{dlgstringS|Enter stack name|[default stack]}"`

The command line argument **ADDTOSTACK** will force DopStack to add all _selected_ items in the source tab to the stack.  
e.g: `DopStack ADDTOSTACK`  
Additional options are available for the **ADDTOSTACK** argument:  
`ADDTOSTACK=allsource`: will add all source files/folders to the stack.  
`ADDTOSTACK=alldestination`: will add all files/folders in the destination tab to the stack.  
`ADDTOSTACK=selecteddestination`: will add all selected files/folders in the destination tab to the stack.

Open the dialog using the button above and then simply drag and drop files and folders from any Lister (or anywhere else that supports the dragging of files) to add them to the stack. When you're ready, simply select Paste in any Lister to copy all items from your stack. You can also drag **from** DopStack to copy your stack to any valid location (left button to copy, right button to copy or copy to new folder).

As you add files and folders to the _stack_, the numbers at the bottom of the dialog will show you the total counts.

The stack label will change colour (orange by default, but configurable) if the clipboard no longer matches the files in the stack (Whenever items are dragged and dropped on the dialog they are added to the clipboard automatically). Double click anywhere in the dialog (or use the _Copy_ option in the popup menu) to re-copy the stack to the clipboard.

You can run as many DopStack instances as you like, allowing you to use multiple stacks.

Right click anywhere in the dialog to show a popup menu with these options:

[![pehJwyPBqb](https://resource.dopus.com/uploads/default/optimized/3X/7/f/7f56657bdb10fdc7021c8c7932a8f64090a3e6e8_2_143x249.png)](https://resource.dopus.com/uploads/default/original/3X/7/f/7f56657bdb10fdc7021c8c7932a8f64090a3e6e8.png "pehJwyPBqb")

*   **Add Selected to Stack**: Adds selected items in the current source Lister to the stack.
*   **Add Source to Stack**: Adds all items in the current source Lister to the stack.
*   **Remove Last**: Removes the last items added to the stack.
*   **Remove All**: Empty the stack and clear the clipboard.
*   **Save Stack...**: Saves the current stack as a plain text file.
*   **Load Stack...**: Loads a previously saved stack, the loaded stack will be added to the existing stack with any duplicates ignored.
*   **Copy**: Re-copies the stack to the clipboard (files and folders dragged to the target are automatically added to the clipboard).
*   **Paste**: Paste any files or folders in the clipboard into the stack.
*   **Copy File Names**: Copies names of items in the stack to the clipboard as text.
*   **Copy Pathnames**: Copies full paths of items in the stack to the clipboard as text.
*   **Copy to Collection**: Copies the stack to a DOpus collection (coll://DopStack). The collection will be created if it doesn't exist.
*   **Empty Collection**: Empties the collection (coll://DopStack).
*   **Compress to archive**: Creates a compressed file of all items in the stack (the archive format can be chosen in the configuration: _archive\_format_. A file request dialog will prompt you for a filename.
*   **Compress and email...**: Compress all items in the stack and emails the archive (uses the _COPY SENDMAIL_ command).
*   **Stack Viewer...**: Opens the Stack Viewer (see below).
*   **Change Stack Label...**: Change the label for this instance of DopStack.
*   **About DopStack...**: Information about DopStack.
*   **Exit DopStack**: Close the dialog and exit the script.

**Stack Viewer:**

[![dopus_LhbU0gFoiA](https://resource.dopus.com/uploads/default/optimized/3X/f/1/f1428827773a0e1415e738e15c8b9916559f72ba_2_345x240.png)](https://resource.dopus.com/uploads/default/original/3X/f/1/f1428827773a0e1415e738e15c8b9916559f72ba.png "dopus_LhbU0gFoiA")

The Stack Viewer allows you to view and manipulate the stack. You can filter the displayed items with the edit box at the top (clear it with the button). This filter has no effect on the stack, it's purely for display. Double click an item to perform the action chosen in the configuration options (_dblclk\_viewer_). Possible options are (Show with DOpus viewer, Default Open action and View Properties).

By default the Stack Viewer will use Details mode, which can be enhanced with additional info, including size, modified date and attributes (use the _extended\_viewer\_info_ option). Additionally, the Stack Viewer can be used in Icon mode (config option for this is _icon\_mode_). In this mode the extended\_viewer\_info will be ignored.

Both Details and Icon mode allow grouped by File and Folder (option _group\_viewer\_list_).

Once the dialog is open you can toggle Icon/Details mode and Grouping On/Off.

Right click an item to show a popup menu with the following options:

![dopus_i9yEP2oZyH](https://resource.dopus.com/uploads/default/original/3X/8/c/8cea0ef4bace01af288727c06287ed0f615bc481.png)

*   **Open**: Opens the item with the Default Open action.
*   **Show**: Show the item in the DOpus viewer.
*   **Go to...**: Open the current item in the source Lister (a new Lister will open if none exist). If the item is a file it will be selected in the Lister, if it's a folder it will just open the source Lister to that folder.
*   **Copy**: Copies the item to the clipboard.
*   **Copy File Name**: Copy the items file name to the clipboard as text.
*   **Copy Full Pathname**: Copy the items full path to the clipboard as text.
*   **Properties**: Show the Properties dialog for that item.
*   **Remove from Stack**: The selected item will be removed from the stack (there is no undo for this).
*   **Clear Filter**: If a filter is set for the viewer, this will clear it (the same as the Clear button).

The Notepad button will show the current stack in notepad.exe - or any configured text editor you prefer (both the button label and the editor path can be changed - see above).


[Source](https://resource.dopus.com/t/dopstack/35671)