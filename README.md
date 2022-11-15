<p align="right"><a href="README-de.md">Deutsch</a> &nbsp; <a href="README.md">English</a> &nbsp; <a href="README-sv.md">Svenska</a></p>

# Edit 0.8.70

Edit your website in a web browser. [Try the demo](https://datenstrom.se/yellow/demo/).

<p align="center"><img src="edit-screenshot.png?raw=true" alt="Screenshot"></p>

## How to edit a website in a web browser

The login page is available on your website as `http://website/edit/`. Log in with your user account. You can use the normal navigation, make some changes and see the result immediately. The built-in web editor allows you to edit content files, upload media files and change system settings. It is a great way to update your website. To show an edit link on your website use an `[edit]` shortcut.

## How to create a user account

The first option is to create a user account in a web browser. Go to the login page. You can create a user account and change your password. The webmaster needs to approve new user accounts. The webmaster's email is defined in file `system/extensions/yellow-system.ini`.

The second option is to create a user account at the [command line](https://github.com/annaesvensson/yellow-command). Open a terminal window. Go to your installation folder, where the file `yellow.php` is. Type `php yellow.php user add` followed by email and password. All user accounts are stored in file `system/extensions/yellow-user.ini`.

## How to remove a user account

The first option is to remove a user account in a web browser. Log in with your user account. Go to the settings. You can remove your own user account at any time. After you have confirmed that you want to remove your user account, you will receive a final email and the user account will be deleted.

The second option is to remove a user account at the [command line](https://github.com/annaesvensson/yellow-command). Open a terminal window. Go to your installation folder, where the file `yellow.php` is. Type `php yellow.php user remove` followed by email. All user accounts are stored in file `system/extensions/yellow-user.ini`.

## How to restrict a user account

If you don't want that pages are modified in a web browser, then restrict user accounts. Open file `system/extensions/yellow-user.ini` and change `Access` and `Home`. Users are allowed to edit pages within their home page, but nowhere else. There are different [access rights](#settings-access), to control what users are allowed do.

If you don't want that user accounts are created, then restrict the login page. Open file `system/extensions/yellow-system.ini` and change `EditLoginRestriction: 1`. Users are allowed to reset their password, but cannot create a new user account.

## Examples

Showing an edit link:

    [edit]
    [edit - Log in]
    [edit - You can edit this page]

Content file with edit link:

    ---
    Title: Example page
    ---
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut 
    labore et dolore magna pizza. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris 
    nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit 
    esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt 
    in culpa qui officia deserunt mollit anim id est laborum.

    [edit - Log in].

Configuring a user account with maximum user access rights:

```
Email: anna@svensson.com
Name: Anna Svensson
Description: Designer
Language: en
Access: create, edit, delete, restore, upload, configure, update
Home: /
Hash: $2y$10$j26zDnt/xaWxC/eqGKb9p.d6e3pbVENDfRzauTawNCUHHl3CCOIzG
Stamp: 21196d7e857d541849e4
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Configuring a user account with default user access rights:

```
Email: niklas@svensson.com
Name: Niklas Svensson
Description: Editor
Language: en
Access: create, edit, delete, restore, upload
Home: /
Hash: $2y$10$zG5tycOnAJ5nndGfEQhrBexVxNYIvepSWYd1PdSb1EPJuLHakJ9Ri
Stamp: e4138bbd338881147a5d
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Configuring a user account with restricted user access rights:

```
Email: english@example.com
Name: Demo
Description: For testing website
Language: en
Access: edit, upload
Home: /demo/
Hash: $2y$10$zG5tycOnAJ5nndGfEQhrBexVxNYIvepSWYd1PdSb1EPJuLHakJ9Ri
Stamp: 1a1d1699df534913a823
Pending: none
Failed: 0
Modified: 2000-01-01 13:37:00
Status: active
```

Configuring different toolbar buttons in the settings:

```
EditToolbarButtons: auto 
EditToolbarButtons: format, bold, italic, strikethrough, code, separator, list, link, file, undo, redo
EditToolbarButtons: bold, italic, h1, h2, h3, code, quote, ul, ol, tl, link, file, preview, help
EditToolbarButtons: format, bold, italic, separator, quote, code, link, file, separator, emoji
```

Configuring different upload locations in the settings:

```
EditUploadNewLocation: /media/@group/@filename
EditUploadNewLocation: /media/@group/@timestamp.@type
EditUploadNewLocation: /media/@group/@folder/@filename
EditUploadNewLocation: /media/uploads/@filename
```

Showing available user accounts at the command line:

`php yellow.php user`  

Creating a user account at the command line:
 
`php yellow.php user add email@example.com password`  

Changing a user account at the command line:

`php yellow.php user change email@example.com password`  

Removing a user account at the command line:

`php yellow.php user remove email@example.com`  

## Settings

The following settings can be configured in file `system/extensions/yellow-system.ini`:

`Author` = name of the webmaster  
`Email` = email of the webmaster  
`EditSiteEmail` = email of the website, used for generated messages  
`EditLocation` = login page location  
`EditUploadNewLocation` = location for uploaded media files, [supported placeholders](#settings-placeholders)  
`EditUploadExtensions` = file formats for upload, `none` to disable  
`EditKeyboardShortcuts` = keyboard shortcuts and commands, `none` to disable  
`EditToolbarButtons` = toolbar buttons, `auto` for automatic detection, `none` to disable  
`EditEndOfLine` = line endings, e.g. `auto`, `lf`, `crlf`  
`EditNewFile` = content file for new page  
`EditUserPasswordMinLength` = minimum length of passwords  
`EditUserHashAlgorithm` = hash algorithm used for encrypted password  
`EditUserHashCost` = hash cost used for encrypted password  
`EditUserAccess` = default user access rights for new user account  
`EditUserHome` = default home page location for new user account  
`EditLoginRestriction` = enable login restriction, 1 or 0  
`EditLoginSessionTimeout` = validity of login in seconds  
`EditBruteForceProtection` = number of failed login attempts  

<a id="settings-placeholders"></a>The following placeholders for uploaded media files are supported:

`@filename` = file name  
`@timestamp` = file upload date as timestamp  
`@date` = file upload date, YYYY-MM-DD format  
`@type` = file type  
`@group` = file group  
`@folder` = folder name of source page  

<a id="settings-user"></a>The following settings can be configured in file `system/extensions/yellow-user.ini`:

`Email` = email of the user  
`Name` = name of the user  
`Description` = description of the user  
`Language` = language of the user, e.g. `en`  
`Access` = user access rights, [supported access rights](#settings-access)  
`Home` = home page location  
`Hash` = encrypted password  
`Stamp` = unique token for authentication  
`Pending` = pending changes  
`Failed` = number of failed login attempts  
`Modified` = modification date, YYYY-MM-DD format  
`Status` = user status, [supported status values](#settings-status)  

<a id="settings-access"></a>The following user access rights are supported:

`create` = user can create page  
`edit` = user can edit page  
`delete` = user can delete page  
`restore` = user can restore deleted page  
`upload` = user can upload media files  
`configure` = user can configure website  
`update` = user can update website  

<a id="settings-status"></a>The following user status values are supported:

`active` = user is active  
`inactive` = user has been deactivated temporarily  
`unconfirmed` = user has not confirmed user account  
`unapproved` = user has not been approved by webmaster  
`unverified` = user has not confirmed new email address  
`unchanged` = user has not confirmed pending changes  
`removed` = user has not confirmed pending deletion  

<a id="settings-files"></a>The following files can be customised:

`content/shared/page-new-default.md` = content file for new page  
`content/shared/page-new-wiki.md` = content file for new wiki page  
`content/shared/page-new-blog.md` = content file for new blog page  

## Installation

[Download extension](https://github.com/annaesvensson/yellow-core/archive/main.zip) and copy ZIP file into your `system/extensions` folder. [Learn more about extensions](https://github.com/annaesvensson/yellow-update).

## Developer

Anna Svensson. [Get help](https://datenstrom.se/yellow/help/).
