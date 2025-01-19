# Release Notes

Don't forget:

-   Buying a license key supports the future development of MailMate.
-   If you already have a license key then consider becoming a **_MailMate Patron_**. Follow the “MailMate ▸ Registration ▸ Become a MailMate Patron…” menu item to learn more.
-   Read the [Introduction](help:anchor=introduction%20bookID='MailMate%20Help') if you are new to MailMate.
-   You can [subscribe](https://freron.com/mm_subscribe) to notifications about new releases of MailMate.

## Revision 5851 (Thursday, December 2, 2021) — **_BETA Candidate_**

This is a **_test_** release. All test release notes since the latest public release (r5673) are reorganized/rewritten in the following subsections. Consider it a work-in-progress of the release notes needed when the next public release is ready.

Recent changes:

-   Fixed: Various issues with the “Find” interface for searching within messages.
-   Fixed: Some alerts have been fixed to have a default action for the space key (without keyboard navigation enabled).
-   Fixed: The old visual “temporarily disappearing line” issue in the composer.
-   Fixed: Added a couple of missing key bindings to the manual (`markAsUnread:`/`markAsRead:`).
-   Fixed: Now ignoring windows saved by older releases of MailMate (this should fix some issue with updating MailMate).
-   Fixed: Saving an attachment did not always set its modification date correctly.
-   Changed: Removed the option to use a scoped stylesheet (it doesn't work). This also fixed some related issues.
-   Changed: Handling of dollar sign at the end of a URL when autolinking.

## Message View

Displaying the content of an email is an important feature of an email client, but it's also a suprisingly complex feature. Since the first release of MailMate, this feature has been implemented using an HTML view known as `WebView` provided by Apple. If an email wasn't already received in the HTML format then MailMate would generate HTML to be displayed. Attachments would also be displayed using HTML and if viewing multiple emails then they would be concatenated including the headers. Given simple emails this was a simple process, but there were also numerous difficult or even impossible problems to solve with this approach. Sooner or later, it had to be replaced with a different approach.

The new approach has resulted in a completely new message view which does not only fix a lot of long standing bugs, it also includes a lot of new features — and it will allow even more of those in the future. Here's a list of changes relative to the old message view:

-   Each (MIME) part of a message is displayed in its own subview ensuring that it's not possible for one part of a message to affect the display of another part (a common security issue with HTML based email clients including MailMate).
-   Given the use of subviews, displaying multiple messages is much more reliable/robust.
-   The subviews used to displayed messages are cached making it faster to switch between recently selected messages.
-   Attachments are now shown in a dedicated view instead of using HTML (see more further below).
-   Uses the `WKWebView` class to display HTML instead of the `WebView` class (deprecated by Apple a long time ago).
-   A `WKURLSchemeHandler` is used to handle so-called `cid:` URLs (embedded images). (Behavior on 10.12 is different.)
-   Context sensive menus have more options to open/copy/download image references.
-   Pinch-zooming works after switching to `WKWebView` (for individual subviews of the message view).
-   Font settings re-implemented (for all views). The menu items have been moved to the View-menu.
-   Safari-like zooming using ⌘+/⌘-/⌘0 changes font size for the entire message view. A HUD indicates the current zoom level in percent.
-   Printing has been re-implemented using the new message view.
-   The use of the `WKWebView` class means that MailMate respects the “Look up and data detectors” setting in the Trackpad System Preferences pane. For example, a three finger tap can be used to detect the data type (or lookup) whatever is currently selected, e.g., to easily detect addresses or flight information.
-   Work-in-progress: Use ⌥+Tab to navigate multiple messages displayed. Margins are then added and a focus rectangle indicates the currently selected message. (No autoscrolling and keyboard actions are applied to all displayed messages.)
-   Work-in-progress: A stylesheet can be used to change the default styling (`main.css`).
-   Debug variable `MmViewInBrowserButtonEnabled` can be used to display a button which opens the currently displayed message in a browser window.

### Image/resource blocking

By default, the `WKWebView` class is configured to block _all_ external resources using a so-called `WKContentRuleList` (macOS 10.13+). Only resource references explicitly recognized by MailMate can be downloaded if allowed, e.g., `img src` references. MailMate then rewrites these references to use a custom URL scheme handled by its own `WKURLSchemeHandler`. This makes it possible to implement much more detailed control of image blocking.

-   Blocked images are clearly shown using colored rectangles (based on an SVG image, coloring depends on `http` /`https`).
-   It's now possible to review the URLs of all blocked images including the reason they were blocked.
-   A specific image resource can be downloaded using a custom key binding while hovering the mouse over its rectangle (`loadImage:`).
-   In some cases, a blocked image can be downloaded by clicking on it.
-   To some extent, it's possible to ⌥+Tab into a message and then use Tab/⇧Tab to move between links. In this case, an image can be loading by using the `loadImage:` key binding.
-   Each resource requested is listed with the type of request, e.g., `img src` or `inline stylesheet`.
-   Resources such as fonts and external stylesheets are also handled.
-   If resources take an insignificant time to be fetched, they are listed as being downloaded (no progress indicator yet).
-   Explicitly allowing images to be downloaded is handled efficiently without reloading the HTML document. It also works when viewing multiple images.
-   By default, blocking is always enabled for known trackers (image references to known tracking services) and unencrypted server connections (`http`). This is configurable in the Security preferences pane. It is based on a general file format for known trackers which allows fast checking of image URLs.
-   The previously described feature can be disabled in the Security preferences pane.
-   Whenever resources are allowed to be downloaded, they are now also allowed to be saved in a cache. This means that, usually, a server is only notified the first time an image is needed _and_ images may be shown even if image blocking is enabled. Images might also be shown for new messages if the same resource references have been used in other messages.
-   Explicitly reports when/if 1x1 pixels were downloaded (a very likely indication of email tracking). This can be disabled in the Security preferences pane.
-   Reports unknown URL schemes found when looking for image references.
-   Reports some types of suspiciously formatted image URLs.
-   No longer uploads drafts, by default, if they are signed and/or encrypted. This is a safety catch in case of compromised connections/servers/accounts.

Known issue: Some rarely used image reference styles are not yet recognized by MailMate and will therefore not be displayed or listed as a reference at all.

### Details View (Banners)

An HTML view is also used to display any information related to the currently displayed message (or part of a message). Some of these include buttons with actions such as allowing images to be downloaded. Compared to the old message view, there is usually much more information available when expanding details.

-   Works well even when selecting multiple messages or when messages have been attached.
    
-   Junk state releated details are now independent of image blocking.
    
-   A phishing warning is displayed if the server utilizes the `$Phising` IMAP keyword.
    
-   Experimental: The hidden preference `MmShowSubscriptionDetails` enables the display of options to unsubscribe from mailing/marketing lists if the headers of the message allows it. Feedback is welcome if you use this. It supports 3 different unsubscription methods: `mailto`, `https`, `https-one-click`. A notification is shown when the one-click variant fails/succeeds (asynchronously).
    
-   Experimental: The hidden preference `MmShowParserDetails` enables the display of any parsing issues registered by MailMate. Most users would not want to do this since they can be both incomplete (or badly written) and too “sensitive” — or even wrong in some cases. As a side-effect, this also enables running `tidy` on any HTML displayed in order to look for any issues.
    

### Find

The old message view used third party code to provide highlighted search results in the message view, but this was based on the `WebView` class and not the `WKWebView`. The new message view has its own custom code based on JavaScript. The “Find” (⌘F) interface itself has also been re-implemented.

-   Searches all displayed messages (or parts of messages).
-   Shows number of matches.
-   Previous/next buttons in addition to the existing standard shortcuts (macOS 11.x+).
-   Styling can be overridden using JavaScript.
-   Styling depends on the use of light/dark appearance of macOS.
-   Automatically updates when switching messages (kind of like having a live search).

### Headers View

The headers view is currently also based on a `WKWebView`.

-   Context sensitive menus have more options including “Edit as New Message”, “Reply” variants, “Forward” variants, “Redirect”, and “Detach” (for any messages attached to an incoming message).
-   The headers view is also used for any attached messages (`message/rfc822`MIME parts) or other `message/*` types. (This is much better than the old message view.)
-   Specialized handling of `message/delivery-status` which is now nicely formatted and includes clickable header titles leading to the corresponding RFC describing the use of each header.
-   Improved capitalization of headers in general.
-   Email addresses are now draggable in a sensible way (proper string on the pasteboard).

Known issue: Configurability of displayed headers is still very limited.

### Attachments View

Previously, (non-inlined) attachments were shown using HTML which did not offer much information or functionality. The new attachments view is much more flexible and will also be easier to improve in the future. The same view is used in the Composer window and some of the following only applies to this use of the view:

-   Improved drag'n'drop behavior including support for so-called promised files (which works better with some apps including Calendar/Contacts).
-   Dragging also puts URLs on the pasteboard. This means that dragging to a Terminal window inserts space-separated file paths. Each path defaults to the most recent save location (which might be a location in the MailMate cache).
-   Selecting multiple attachments is allowed.
-   Double-click to open/view an attachments.
-   Buttons to “Quick Look”, “Save” and “Remove”.
-   Holding down a qualifier can turn “Save” into “Save as...” (⌥) or “Show in Finder” (⌘).
-   Removing attachments from non-drafts makes them appear stroked out. This works with undo/redo.
-   Saving attachments most often happens asynchronously.
-   In some cases, removed attachments can still be, e.g., opened if MailMate knows if and where they were previously saved.
-   Cut/copy/paste works within MailMate and from/to other applications.
-   Quick Look allows navigating to next/previous attachment.
-   Context sensitive menu with a lot of new functionality including a system-based “Share” menu and an “Attach to New Message...” menu item which works with any set of selected attachments.
-   Thumbnails used as icons for attachments.
-   New system for saving attachments in files, e.g., needed when asked to display an attachment. They are saved in `~/Library/Caches/com.freron.MailMate/Attachments/` which is always safe to delete. This also means that these files do not take up space in backups. (The previous location was `~/Library/Application Support/MailMate/Attachments`.)
-   Quarantines saved attachments (which enables Gatekeeper malware checking if the user attempts to execute an attachment).

Composer only functionality:

-   Drop target at the bottom of the Composer for explicitly attaching (dropping on the text view will inline images if using Markdown).
-   Dropping text onto the attachments view will make it attach a text file.
-   Reordering attachments is allowed.
-   Renaming attachments allowed.
-   Undo/Redo works for _all_ actions
-   Pasting a link from Safari (an possibly other apps) creates a Markdown link including a title.
-   Drag'n'drop attachments between any open composer windows.
-   Always showing total size of attachments and not just when saving.
-   Defaults to the encoded size of attachments in the composer since this is what's relevant for SMTP sending limts.
-   Click attachments size in the status bar in the composer to switch between encoded size (most often base64+newlines) and file size. This also changes the sizes displayed in the attachments view.

## Composer

The composer, in general, has also gone through massive changes. Functionality hasn't changed much, but it is (or at least has the potential to be) more robust and responsive than the old composer. (Some parts of the old composer suffered under some early bad design decisions which made it hard to improve/fix other parts of the composer.)

### Message generation

Low level, a draft is now handled differently/explicitly and this makes it easier for the composer to handle the various states of a draft. A very long standing issue in MailMate has been that any structural change to a message (MIME structure) would force a message to be saved since all message parts needed to exist in the internal database. For example, emphasizing a word using Markdown would trigger the message to be saved clearing the “edited” state of the composer window. This is no longer the case.

Other changes include:

-   Uses CommonMark (Github flavor) by default instead of `sundown` (which has not been updated for a long time). It's both faster and better. Task lists (checkmarks) are now supported and explicitly styled (to remove bullet points).
-   Much better asynchronous behavior when cleaning up embedded HTML, inlining CSS, syntax highlighting code, and more. This should make the editor more responsive while writing.
-   The preview (when displayed) also does most of its work asynchronously.
-   “Edit as New Message” works better than before with unsaved drafts -- allowing one to spawn variants of a currently open draft if needed.
-   Autoscrolling the preview is more robust with the new Markdown conversion. This includes scrolling to, e.g., the location of footnotes.
-   Converting non-Markdown plain text to HTML is handled by compiled code instead of an external script (much faster when editing).
-   Generation (preview) is automatically updated when changing the theme used by default or for the current signature.
-   Inlined images are always limited to the width of the message view/preview.
-   Detects Retina images and uses CSS to control its displayed size. Also uses HTML to make it work in Outlook and possibly other email clients.
-   Uses `libtidy` to more easily and more efficiently clean up embedded HTML.
-   Cleans up Markdown image links in order to avoid generating HTML unnecessarily in replies.

### Headers Editor

-   Recipient header fields switch to showing a scroller when the number of lines needed to display recipients is large.
-   The hidden preference `MmComposerPreviewHeadersEnabled` can be used to display headers as part of the preview (if shown). Mainly useful for debugging.
-   “Edit” menu item for tokenized addresses (in addition to doing this with double-click or the space key).

### Text Editor

Again, a lot has been reimplemented and it will be easier to maintain/improve in the future.

-   The HTML preview resizes the window when toggled (both when this happens manually or automatically).
-   “Edit ▸ Paste as Plain Text” forces MailMate to convert anything on the paste to plain text if possible.
-   Pasting from Microsoft apps is forced to prefer plain text (instead of the image available on the pasteboard).
-   Pasting from Excel auto-generates a simple plain text table (in Markdown format).
-   Soft wrapping supported (see “View ▸ Soft Wrap Column ▸ ...”).
-   The “Scan Documents” menu item in the context sensitive menu works by attaching a PDF.
-   Improved/Explicit handling of signatures.
-   Discard/Edit signature suggested if trying to edit the current signature. (Known issue: Discarding doesn't really work well in practice.)
-   Signature updated in all open composer views (also if changed in Preferences).
-   Discard/Edit Signature available in a context sensitive menu.
-   Improved handling of the signature when using undo/redo.
-   Improved handling of embedded HTML (when replying/forwarding).
-   “Discard Embedded HTML” in context senstive menu
-   Spelling suggestions in the context sensitive menu can be selected using a numeric key.
-   Pasting works with HTML (similar to replying/forwarding HTML), e.g., after copying part of a page in Safari. For now, this is disabled by default, but this feature can be enabled using `MmEmbedPastedHTMLEnabled`.

## S/MIME and OpenPGP

Partly as a side effect of some of the changes above, the S/MIME and OpenPGP handling has also gone through a lot of changes. There's still a lot to improve, but here's a list of some of implemented changes:

-   Much better at handling complex message structures including multiple signed/encrypted parts and/or embedded messages.
-   Works when showing multiple messages (the old message view simply disabled reporting verification status, because it couldn't handle it).
-   Asynchronous verification of OpenPGP messages.
-   Since message parts are never merged into a single HTML document, MailMate is now much more robust against both existing and future HTML-based attacks.
-   Issues with signing/encrypting outgoing messages is clearly displayed in the composer -- also when the preview is disabled.
-   OpenPGP (`gpg` command) output is now always available in the details displayed.
-   Signing/encrypting is only done when changing related settings/headers, when sending, and when saving (⌘S).
-   Some types of errors now offer a “Retry” button.
-   The Bcc warning for S/MIME encryption offers to move Bcc recipients to Cc.
-   When failing to find an S/MIME certificate for a recipient, MailMate completes the search for any other recipients instead of stopping.
-   S/MIME code now explicitly first looks for a user certificate in the default keychain.
-   S/MIME sign/encrypt debug output now includes the keychain location for all certificate candidates founds.
-   “View Certificate” button shown when a signature has a mismatching address (S/MIME).
-   Explicitly lists all of the email addresses found within the signing certificate (S/MIME).
-   S/MIME searches for email addresses were not case insensitive.
-   Various issues with S/MIME. The “Security.plist” file now supports using sha256 instead of serial since the latter was not a robust solution (only guaranteed to be unique for each CA).
-   If identical S/MIME certificates are found then MailMate should now be better at picking the first one returned by the keychain search.
-   Replaced a deprecated S/MIME certificate related function on 10.13+.
-   MailMate forces the use of sha256 when making S/MIME digests.
-   Improved handling of a signature address mismatch for both OpenPGP and S/MIME.
-   Various S/MIME related issues. Thanks to Heike Knobbe for the report!
-   Attempt to improve the handling of certain types of encrypted OpenPGP messages.
-   Text attachments were incorrectly checked for inlined OpenPGP attachments.
-   Slightly better error message when failing to parse OpenPGP output.
-   MailMate is a bit better at showing the correct signed/encrypted icon for messages using `smime-type=signed-data`.
-   Most of the S/MIME related code has been refactored.
-   No longer trusts the body content of a `mailto:` link if it contains anything which could be parsed as inline PGP.

Known issue: Some earlier test releases were able to clearly display which parts of a message were decrypted and/or verified. This feature will eventually return.

Known issue: More could and should happen asynchronously since neither OpenPGP or S/MIME actions are always fast to complete.

## Coding/Building related changes

-   All executables are now universal. In other words, MailMate has native support for Apple Silicon (M1 / `arm64`).
-   Requires macOS 10.12 (previously public release required 10.10).
-   Many parts of MailMate use AutoLayout now, including the most used windows. This fixes a lot of issues and will be easier to maintain going forward.
-   Simplified/improved code by using newer Apple classes such as `NSStackView`and `NSSplitViewController`.
-   All parts of MailMate use ARC now.
-   No longer depends on any `openssl` code.
-   Removed various files no longer needed.
-   Uses `libidn2` with new dependencies `libpsl` and `libunistring`.
-   Build process is more robust with regard to only linking with libraries working on the minimum required version of macOS (currently 10.12).

## Other

-   Supports OAuth2 for Office 365 accounts.
-   OAuth2 is now always handled using an external browser (Safari) for the authentication process.
-   Incoming email notifications support writing a single line reply (top-posted).
-   On macOS 11+, SF Symbols are now used for the icons of the Preferences panes.
-   “View ▸ Copy as Link” works for multiple messages.
-   Dragging a message to, e.g., TextEdit creates a titled `message:` link in rich text mode and a `message:` text URL in plain text mode.
-   The Signatures preference pane has some new options.
-   “Go to Mailbox” updated including new mailbox images (can be disabled using `MmMailboxImagesEnabled`).
-   “Go to Mailbox” actions are now part of the history, for example, this allows you to switch back to previously selected mailboxes using a shortcut.
-   Hidden preference to disable account icons: `MmAccountImagesEnabled`.
-   Default shortcuts for back/forward in history match what is used in other applications, e.g., Safari (⌘[/⌘]).
-   Built-in CSS inlining based on Juice (JavaScript). This will replace Premailer going forward.
-   Removed the option to use a “Scoped Stylesheet” (it no longer works in any browsers or email clients).
-   Conversion from HTML to Markdown (plain text) based on Turndown (JavaScript). This is both faster and more robust than the old approach (but both methods are still in use).
-   Simplified the sharing extension included with MailMate (removing the use of an intermediate GUI).
-   Bundle commands now support an action to show an HTML result (`showHTML`). Supports `filePath` and a dictionary of parameters. This is going to be used to make the Visualize bundle functional again.
-   The `emate` command allows setting an explicit `#signature-uuid`.
-   Format-strings can be used to specify virtual headers (in `specifiers.plist`).
-   The skull previously used for warning about spoofing-attempts is gone. Instead, a warning sign is shown and an explanation is available in the message view. As a special case, anything that matches the format of a Github username is not marked as a spoofing attempt.
-   Shows a localized/abbreviated file path in the saving attachment notification.
-   Shows an Open button in the saving attachment notification (clicking elsewhere opens the attachment in the Finder).
-   Allows multiple mailboxes to be selected in the mailbox subscriptions editor.
-   Added “Expunge Deleted Messages” menu item (this is part of some still missing GUI settings for configuring deletion behavior).
-   Warns when moving or copying a large number (500) of messages (this warning can be suppressed).
-   Switch panes in the mailbox editor using the keyboard (⌘1-⌘n). Dynamic submenu in the Window menu shows the available shortcuts.
-   Added `MmSubaddressCharacterClass` to control the subaddress separator used for the `tag` specifier (for email addresses). The default value is `+-` which should work in most cases.
-   Added `MmSimpleForwardedString` as a primitive stop-gap solution until something better can be done about custom wrote/forwarded-strings.
-   Added `MmAlwaysSaveDraftsOnQuit` which is mainly useful for a developer repeatedly relaunching MailMate.
-   Added `psl-top-level` and family to work around issues with the regular domain specifiers which are a bit useless for the Submailboxes feature. (This feature is likely to be renamed.)
-   The `PREAUTH` command (IMAP) is now always rejected when the connection is not encrypted (if encryption is enabled for the account).
-   Disabled the support for `PREAUTH` (IMAP) by default. Use `MmAllowPREAUTH` to explicitly enable it if needed.
-   Temporary workaround for a lack of configurability in the interface: `MmRulesForwardWithoutAttaching`
-   Introduced `MmSendMessageDelayString` (a string alternative to `MmSendMessageDelay`).
-   Encoding/decoding attachment names according to RFC2231 when non-ASCII exists (improvements still needed).

Known issue: The interface for importing accounts breaks with almost every macOS release and it will be removed. Some work has been done on a new connection “wizard” for setting up accounts (using both autoconfig and SRV records). This should hopefully lead to an easier setup process.

## Changes/Fixes

All kinds of, more or less, boring changes/fixes which are mainly here when/if searching for some particular issue.

-   The Bundles and Software Update panes (Preferences) have been updated.
-   The experimental LDAP support uses `ldaps` instead of `ldap` when port 636 is specified.
-   The check for a duplicate email address within the name part of an address header is now case insensitive (ASCII). This has the side effect of also avoiding unlikely spoofing warnings.
-   No longer showing the Submailboxes pane or Rules for the main accounts mailboxes (except if rules already exist).
-   “Format ▸ Indentation ▸ Increase” will insert a tab character if nothing is selected.
-   Various issues with renaming mailboxes.
-   The message list and the mailbox list can show a context-menu for non-selected items.
-   Notifications now respect the “Do not disturb” system settings.
-   Automatically setting subject based on an added attachment. Now also works with undo/redo.
-   Clicking to enable/disable a flag did not work in the first line of the message list.
-   `MmNeverDisplayHTML` now falls back to displaying raw HTML if sanitizing the HTML fails.
-   Minimum width of the Security column now adapts to the font size in order to never show ellipsis for truncated text.
-   Messages importer window looks a bit better in dark mode.
-   Some warnings displayed with a “Cancel” button did not work correctly in the mailbox list when the user chose “Cancel”.
-   Crash if using a custom key binding to create a new message when no identities exist.
-   Issue with setting headers in new messages via bundle commands.
-   Slightly more robust behavior when moving files within the database.
-   Very old bug in the global threading of messages triggered when permanently deleting multiple messages (also when this is triggered by server-side changes).
-   Long standing issue with messages not being removed from a dynamic submailbox after some order of events which included a keyword-change — such as marking as read.
-   Some issues with identically named attachments when using bundle commands.
-   A bundle command using file paths to attachments as input should now work with encrypted messages (untested).
-   Issue with address completion when only a last name is available in Contacts.
-   Yet another attempt at better handling of parentheses when autolinking (now similar to GFM).
-   Crude workaround for a special case of the use of an unnecessary use of the Unicode LRE character in the name part of a sender.
-   Replying to a specific (buggy) message did not work well, because MailMate did not treat an unknown multipart subtype as if it was `multipart/mixed`.
-   Reencoding body parts failed to correctly remove any existing transfer encoding headers.
-   Issue with base64 decoding if segments of 4 input characters were split between lines.
-   Some long-standing issues fixed by replacing a prefixed tab with 4 spaces whenever a quote symbol (>) is added to a line of a Markdown message (when replying/forwarding).
-   Issue when merging base64 encoded words in headers, e.g., some type of subject headers would be partly displayed with garbage characters.
-   Various (old) issues with HTML signatures only being inserted _after_ editing a new message.
-   Ignore hidden files when listing available sounds in sound popups.
-   Re-implemented how the sent mail sound is played (if enabled in the Composer preferences pane).
-   Failed to check for existence of `List-ID` when trying to get a list description.
-   Notifications on 10.14+ are implemented using a newer API making it work better with the system in general.
-   Sounds triggered by rules should now respect the “Do Not Disturb” setting.
-   Includes a sound for sending a message since the previous solution no longer worked after fixing MailMate sounds to respect the “Do Not Disturb” macOS feature.
-   Forced to disable the availability of Apple sounds when configuring Counters. If needed, the sounds can be copied to `~Library/Sounds`.
-   Some RFC-violations concerning the use of quoted strings in address headers.
-   Simplified `specifiers.plist` a bit based on improved handling of quoted strings.
-   Improved detection and removal of unexpected NUL characters when adding text to drafts. This was an issue if the user pasted text into the composer which containted NUL characters.
-   Various issued related to failed parsing of JSON strings.
-   Some issues with certain types of unicode characters when saving/loading settings.
-   Renaming sources did not properly propagate to universal mailboxes (without relaunching MailMate).
-   Improved the use of images in mailbox menus (including mailbox popup buttons).
-   Allows longer header field names without reporting it as a possible error (200 chars instead of 50).
-   Prefers port 993 over 143 for IMAP. No longer automatically tries port 25 for SMTP.
-   Better at trying SMTP without authentication when using a non-standard port.
-   Server logs leave out long `UID FETCH` responses to make debugging bandwidth-issues easier. It can be disabled using `MmServerLogTruncationDisabled`.
-   Parsing of `mailto:` URIs is more robust with regard to the use of newlines.
-   Remembers the “Automatically Identifies Languages” setting when it differs from the system setting.
-   The `emate` command should work with python3.x.
-   Added a 32 bit check to avoid database corruption for _very_ large database header files.
-   Refactored code to fix various issues with “Send Later” and updating the “Date” header, including issues related to using “Cancel Send Later”.
-   Issue with too frequent passwords requesters for IMAP when connections break during authentication.
-   An old issue with a temporarily disapparing line in the composer.
-   Handling of a dollar sign at the end of a URL when autolinking in the message view.

Various workarounds:

-   Added workaround for `euc-jp` encoded content wrongly labelled as `iso-2022-jp`.
-   Workaround for an email client generating `Message-ID`s like this: `<uuid@domain.com>>`
-   A bit more aggressive when it comes to sizing incoming images to the width of the message view.
-   Issue handling attachments for which the system fails to provide a UTI given a MIME type (the issue was triggered by an `application/rtf` attachment).
-   Base64 decoder is more robust when encountering bad input.
-   Prefers the casing of an IMAP keyword used by the IMAP server involved (as reported in the `PERMANENTFLAGS` response). This works around at least one server bug (ProtonMail).
-   Ignores unexpected NO responses to QUOTA requests (working around an IMAP server issue).
-   Handles nonsensical QUOTA responses from an IMAP server by quietly warning instead of failing.
-   IMAP code fails a bit more gracefully when a hierarchy delimiter for a submailbox cannot be derived.
-   Workaround to handle `.ips` files on Monterey (based on `ips2crash`).

For debugging purposes, the variable `MmParseMessagesFromIndex` can be used to force MailMate to load, parse, and decode all messages in its database (on startup).

## Revision 5673 (Thursday, September 3, 2020)

-   Fixed: _Sent_ signed and/or encrypted messages were not uploaded to the Sent Messages mailbox.
-   Fixed: The “Open with” menu for attachments would make MailMate hang.

## Revision 5672 (Friday, August 28, 2020) — Version 1.13.2

-   Changed: No longer uploads drafts, by default, if they are signed and/or encrypted. This is a safety catch in case of compromised servers/accounts.
-   Changed: Explicitly checks for and ignores OpenPGP content in the (optional) body argument of a `mailto:` link.
-   Fixed: Various S/MIME related issues. Thanks to Heike Knobbe for the report!
-   Fixed: Startup issue on Big Sur (macOS 10.16).

## Revision 5671 (Thursday, December 5, 2019)

-   Fixed: Using HTML signatures in the composer could crash MailMate.
-   Fixed: Printing was broken for some types of messages (on 10.12+).

## Revision 5670 (Thursday, December 5, 2019) — Version 1.13.1

This is a maintenance release which includes various important fixes for Catalina.

-   Changed: Missing intermediate certificates for S/MIME signed messages was not handled gracefully. MailMate now makes it easier to allow network access when needed (on a case by case basis).
-   Changed: Running scripts is now much quicker on Catalina, especially when using a bad/slow internet connection.
-   Changed: Numerous changes in preparation of making more message composer/viewer related actions happen asynchronously.
-   Changed: Bundle types and icons added for easier import of custom bundles/commands/filters/themes.
-   Changed: Added a workaround for an IMAP server unable to return the correct hierarchy delimiter when synchronizing a mailbox.
-   Changed: Printing on 10.10/10.11 now uses the old code for printing as a stop-gap solution.
-   Changed: Slightly better performance when formatting dates for the messages list.
-   Changed: Mailbox images used for submailboxes of universal mailboxes.
-   Changed: Stop-gap solution to work around an issue with a third party utility not liking that MailMate some times moves counters to the left (when they need to be resized): `MmStatusBarCountMinimumWidth`
-   Fixed: Undoing pasted/inserted (multiple) attachments would often remove all attachments.
-   Fixed: The headers view now properly resizes when it needs to get smaller.
-   Fixed: Issues on Catalina with respect to editing bundles.
-   Fixed: Displaying raw HTML source had some text encoding issues.
-   Fixed: Workaround for what seems to be a Catalina-bug in CMSDecoderCopySignerStatus(). This affected S/MIME verification in general.
-   Fixed: Now respects “Load Once” when printing.
-   Fixed: Printing multiple emails is done on separate pages. This can now be disabled using `MmPrintMessagesOnSeparatePages`.
-   Fixed: Date formatting code issue.
-   Fixed: No longer allows dragging a universal mailbox into a smart mailbox. Such a change was previously lost when quitting/relaunching MailMate (which was very confusing for users).
-   Fixed: Potential crash bug related to the mailbox list.
-   Fixed: The “Message ▸ Open Attachments” menu item (and its shortcut/selector) was broken.
-   Fixed: Issues handling an invalid sender address in the Composer.
-   Fixed: The “All Body Parts” setting did not stick for the “is in” comparison method.
-   Fixed: Some script warnings triggered on Catalina.
-   Fixed: Bug in the code for asking if a reply should be to sender or all.
-   Fixed: User agent string used the version number instead of the revision number.
-   Fixed: `MmLocaleDateIdentifier` did not work for the time of day part of the date related columns.
-   Fixed: Various issues after switching to the 10.15 SDK.
-   Fixed: Added uninstall instructions to the manual.
-   Fixed: Some issues in the composer when non-standard line-feeds are in play.

## Revision 5655 (Monday, September 30, 2019) — Version 1.13

This version of MailMate adds support for macOS 10.15 (Catalina) and removes support for macOS 10.8-10.9. In other words, MailMate now requires macOS 10.10.

There are no major new features in this release of MailMate, but there have been some major internal changes to MailMate in preparation for some future changes/features.

The following is a list of changes since the most recent public release (r5635).

-   New: Hidden preference to enable some “work-in-progress” mailbox graphics: `MmMailboxImagesEnabled`.
-   Changed: Major changes to the build system and various related issues. MailMate is now 10.10+.
-   Changed: Slightly more robust layout code should fix an issue with the widescreen layout on Catalina (and some other issues).
-   Changed: Optimization for the display of attachment icons in the message view (this had become increasingly slow with new macOS releases).
-   Changed: Hardcoded MailMate to make mailbox images into templates when the filename is prefixed with Sidebar. This works better for the hack described in the manual to use Mail mailbox images when using Mojave/Catalina dark mode.
-   Changed: Mailbox images are now treated as templates when the name is suffixed with Template.
-   Changed: “Mark messages read after X seconds” now always displays a decimal-point to hint that it does not need to be an integer.
-   Changed: Replying/forwarding should now be a bit faster.
-   Changed: Converts email address to lowercase before searching for S/MIME certificates.
-   Changed: `MmLocaleDateIdentifier` (experimental setting to hardcode, e.g., `de_DE`, the default language used for displayed dates).
-   Changed: Internal changes to make MailMate compile with c++2a and some newer APIs.
-   Changed: Minor performance improvement when analyzing incoming HTML.
-   Fixed: Crash bug when replying to some types of S/MIME emails.
-   Fixed: The `retiredAddressPattern` feature is no longer case senstive.
-   Fixed: Duplicate image files in the resources folder removed (added by accident).
-   Fixed: Changes to the format string in the Counters preferences pane were not stored unless Enter was explicitly hit.
-   Fixed: Various issues with custom identities in the Composer window.
-   Fixed: Two bugs in the embedded Spotlight importer plugin.
-   Fixed: QuickLook did not always behave correctly, some times leaving a blank view.
-   Fixed: Improved handling of bad recipient addresses.
-   Fixed: Crash bug related to cancelling a search. Also fixed some related issues and removed some debug output.
-   Fixed: Potential crash when deflowing text.
-   Fixed: Closing a search (implicitly) while the window is, e.g., minimized did not work correctly. Also fixed some similar problems.
-   Fixed: Various problems on Catalina (including standard folders like the Inbox not having submailboxes).
-   Fixed: Sent message sound was not played on macOS Catalina.
-   Fixed: Increased minimum width of preferences panes.
-   Fixed: Hitting space to edit an address token in the composer would wrongly result in black text in dark mode.
-   Fixed: Stopped using various deprecated APIs.

## Revision 5635 (Monday, May 27, 2019)

-   Fixed: A last minute change (before the public release today) had an unexpected side-effect which broke the behavior of mailbox rules.

Note: Look out for any messages not correctly handled by rules since the public release earlier today. Sorry about the inconvenience!

## Revision 5634 (Monday, May 27, 2019) — Version 1.12.5

This is the first public release of MailMate with a so-called “hardened runtime”. It is also the first release “notarized” by Apple. In short, this means that this and every future release of MailMate has been scanned by Apple before being released (this includes beta/test releases). Apple documentation currently states they they scan for malicious content and code-signing issues.

Note that the next public release of MailMate will probably _not_ support macOS 10.8 and 10.9. This should affect very few users (less than 0.5%).

The following are all changes since the most recent public release (1.12.4):

-   New: Hidden preferences file `Security.plist` now supports `signingEnabledPattern`, `signingDisabledPattern`, `encryptionEnabledPattern`, and `encryptionDisabledPattern`. More about this on the hidden preferences help page.
-   New: Special warning when following `http:` links in a signed/encrypted messages. This can, optionally, be suppressed.
-   New: Selector `toggleCode:` for the composer which behaves like `toggleBold:` and `toggleItalic:`. There's no menu item or default key binding yet.
-   New: Supports the IMAP `LITERAL-` capability (RFC7888) when using `APPEND`(this limits the maximum size of a non-synchronizing literal to 4096 bytes).
-   New: Detection and handling of the `TOOBIG` response code and the `APPENDLIMIT=` capability (IMAP).
-   New: Allows all types of URLs to be auto-linked. Warning when opening an “unknown” URL scheme in an external application (this can be suppressed per URL scheme).
-   New: `MmComposerTabSize` to change the tab size used in the Composer (the default is 4 and it does not affect outgoing messages in any way).
-   New: `MmSendLaterWarningEnabled`, `MmSendLaterWarningLimitEnabled`, `MmSendLaterWarningLimitMinutes` (control when to be warned about messages scheduled to be sent later).
-   New: Hidden preference `MmDisableExchangeSafetyCatch` which disables that MailMate does not allow the deletion of “internal” Exchange emails (which are not really emails).
-   New: Key binding selectors for scrolling to top/bottom of a list (`scrollToTop:`/`scrollToBottom:`).
-   New: Hidden preference to control the line width of thread arc colored circles (`OakThreadArcsCircleLineWidth`).
-   Changed: Use `/usr/local/bin/gpg` by default for OpenPGP. This works with both GPGTools and brew (the `gpg` and `pinentry-mac`packages). Updated the manual.
-   Changed: The sharing extension now supports sharing movies from, e.g., Photos using the “Share” menu.
-   Changed: Slightly faster decryption of encrypted messages.
-   Changed: The toolbar search field explicitly states which mailbox is configured to be searched by default.
-   Changed: Optimizations with respect to updating the mailbox outline when the state of one or more mailboxes change.
-   Changed: Added (hardened runtime) entitlement for Contacts.
-   Changed: Added basic support for the `$Phishing` keyword.
-   Changed: `scrollPageDown:` now only scrolls a page down when used in key bindings. Introduced `scrollPageDownOrNextMessage:` which is used as default behavior.
-   Changed: Handling of non-existing parent IMAP mailboxes.
-   Changed: Added the ability to compute an md5 value based on an email address (useful for displaying gravatars).
-   Changed: Reduced trust in the `Delivered-To` header.
-   Changed: Tweaked image blocking a bit for encrypted messages.
-   Changed: Does not mute a message if the subject body has changed.
-   Changed: Minor optimizations of the muting feature.
-   Changed: Message list is now automatically re-sorted when changing a sorting-related value.
-   Changed: Always generate `Content-Type` header even when it's not strictly needed.
-   Changed: Dark mode for help pages within MailMate.
-   Changed: Release notes support dark mode on Mojave 10.14.4.
-   Changed: Reduced beeping when doing text search within a message.
-   Changed: Workaround for emails in which headers and body are not separated by a newline while a MIME boundary string can still be detected.
-   Changed: Slightly better at handling unknown/incorrect “Content-Type” charsets like `en_US.UTF-8`.
-   Changed: Slightly better output when failing to convert text for the Composer.
-   Changed: Conversion issues reported a bit differently.
-   Fixed: Long standing bug causing, for example, the Correspondents column to forget its values under certain circumstances.
-   Fixed: The “Prefer Plain Text” option unintentionally also disabled the HTML preview in the Composer.
-   Fixed: Including messages from submailboxes in an IMAP mailbox no longer leaves out the messages of the mailbox itself.
-   Fixed: Issue when an address book group contains an invalid email address.
-   Fixed: The `DOCTYPE` used for HTML internally and for outgoing messages has been changed.
-   Fixed: Hang when changing identity in the composer.
-   Fixed: Recompute maximum width (in characters) when changing font in the composer.
-   Fixed: Some display issues when emails contained unexpected URLs (for example, non-existing `cid:` URLs).
-   Fixed: Some issues getting the delivery address based on some types of `Received:` headers and/or an `X-Envelope-To:` header.
-   Fixed: Some issues with simple renames of IMAP mailboxes.
-   Fixed: Creating a mailbox some times failed if the mailbox already existed on the server (for whatever reason).
-   Fixed: Codesigning issue related to the use of the embedded html2text command.
-   Fixed: _All_ embedded executables are now codesigned.
-   Fixed: Drag’n’drop of mailboxes (smart and IMAP) did some unnecessary redrawing.
-   Fixed: Workaround for iCloud servers which some times (wrongly) output multiple continuation requests.
-   Fixed: Long standing bug in the Activity Viewer which could wrongly color lines, or worse, terminate MailMate.
-   Fixed: Issue finding the correct identity when given a non-lowercase email address.
-   Fixed: Issue parsing invalid Gmail keywords.
-   Fixed: Issue in dark mode with `MmNeverDisplayHTML`.
-   Fixed: Some date-based searches (toolbar search) at the end of a month could fail.
-   Fixed: Too many emails were shown in the dark mode style.
-   Fixed: Always style digest messages.
-   Fixed: Behavior when trying to delete a non-selectable IMAP mailbox.
-   Fixed: Issue when quitting MailMate with the main window closed.
-   Fixed: Various issues with “[Gmail]/All Mail” (and possibly other mailboxes) when not having any Gmail labels explicitly defined.
-   Fixed: Visual issue when enabling/disabling the Composer preview (on right).
-   Fixed: Issue with removing accounts containing incomplete internal moves.
-   Fixed: Hitting Enter at the end of the text in the Composer could hang MailMate.
-   Fixed: Coloring issues in dark mode for signing/encryption alert.
-   Fixed: The Composer preview was not always correctly shown for OpenPGP messages when an HTML part was generated.
-   Fixed: Markdown issue when, e.g., having a link at the end of the text in the composer (without a newline).
-   Fixed: Recent bug in the message view affecting the display of, e.g., attached messages.
-   Fixed: Detecting when to attempt to style an HTML email did not work well for encrypted messages.
-   Fixed: Some times OpenPGP was the default protocol for a new message even if only S/MIME was enabled in the settings.
-   Fixed: Wording of the error message shown when the `gpg` command cannot be found.
-   Fixed: Minor composer status bar issues.
-   Fixed: Problem with messages marked read disappearing from Unread immediately (triggered when the mailbox list was hidden).
-   Fixed: Sorting a numeric column with multiple sorting keys (spam scores) did not work well.
-   Fixed: The look of the attachment icon in dark mode.
-   Fixed: Some DNS prefetching issues.
-   Fixed: Information about embedded HTML segments was not always deleted from headers when it was no longer needed.
-   Fixed: Improved handling of embedded HTML when enabling/disabling sign/encrypt.

## Revision 5594 (Tuesday, January 22, 2019) — Version 1.12.4

-   Changed: The Thread Arcs view displays a colored ring around a node if the message coloring feature (hidden preference) is enabled and the corresponding message is colored.
-   Changed: It should now again be possible to do SMTP without authentication, e.g., when using localhost to send.
-   Changed: Make sure the the From field in the Composer is displayed if “Format ▸ Show Identities” is used.
-   Changed: MailMate now handles wrongly used surrogate pairs (CESU-8) in UTF-8 text.
-   Changed: Message views are automatically updated when changing the minimum font size in the Viewer preferences pane.
-   Changed: Added `MmMessagesOutlineScrollToNewEnabled` hidden preference to allow users to disable that MailMate scrolls to new emails when the the previously newest message is already scrolled into view.
-   Changed: Wording of the “Premailer” install alert.
-   Changed: Performance optimization when editing emails with many separated quoted parts.
-   Fixed: Various problems triggered when using date comparisons with “months”.
-   Fixed: Issue with toolbar menus on 10.13+.
-   Fixed: Bcc was not automatically updated for forwarded messages.
-   Fixed: A low level customization could trigger the composer window to be without a From header selection.
-   Fixed: An invalid email address in account settings could make the Composer crash.
-   Fixed: Hiding the From field in the Composer did not work correctly when sending.
-   Fixed: Displaying the alternative SMTP choice (hidden preference).
-   Fixed: Moving an INBOX would result in the wrong mailbox becoming the default inbox.
-   Fixed: Holding down ⌥ when adding the initial row(s) to a rule editor (conditions, mailboxes, rule actions) could trigger MailMate to hang.
-   Fixed: The Bcc header did not always update automatically when changing the sender of a message.
-   Fixed: Various issues with the “Command ▸ Export” commands on Mojave.
-   Fixed: “Download Linked File/Image” in HTML emails now respects the default download folder setting in the General preferences pane.
-   Fixed: More gracefully handling if/when there is a decoding issue triggered by unknown characters in UTF-8.
-   Fixed: Signature fix accidentally added a newline to each signature after every launch of MailMate.
-   Fixed: Issue related to the recipient field of the Composer.
-   Fixed: Issue with signatures and newlines affecting various parts of the signature system.
-   Fixed: The Viewer preferences pane option to apply themes to HTML emails could interfere with the handling of embedded HTML when replying/forwarding.

## Revision 5579 (Wednesday, December 12, 2018) — Version 1.12.3

-   New: The selection of sender (From) is now at the top of the headers of the Composer window.
-   New: A simple visual indication when using `toggleFilterKey:` and related experimental key bindings.
-   Changed: Behavior of Composer preview when using “Prefer Plain Text”.
-   Changed: Workaround for iCloud `GETQUOTAROOT` issue.
-   Changed: The timeout on UID FETCH is now configurable (`MmIMAPFetchTimeOut`) in case of extremely slow IMAP server responses.
-   Changed: Composer/single-message windows can now again open on top of a full screen main window.
-   Changed: When a charset was not provided in any headers or the body of a malformed message, MailMate would previously not try to make a guess.
-   Changed: Toolbar menus are now handled by “new” API available on 10.13+.
-   Changed: Minor improvement to the derivation of sender of new messages.
-   Fixed: Any disabled conditions would prevent MailMate from saving changes (recent bug).
-   Fixed: MailMate could attempt to use SSL even if explicitly configured not to.
-   Fixed: Crash bug related to `toggleFilterKey:` used on an undefined mailbox.
-   Fixed: Long standing illusive crash bug which could be triggered when removing/re-synching a mailbox. It could also be triggered when the `UIDVALIDITY` value of a mailbox changes.
-   Fixed: Issue with the “Include messages in submailboxes” feature not always behaving correctly when switching mailbox.
-   Fixed: Explicitly providing a “Bcc” header, e.g. using the `emate` command, did not work correctly if, e.g., changing the sender.
-   Fixed: Old bug which caused sender (From) derivation to fail to behave correctly for most new messages.

## Revision 5568 (Friday, November 23, 2018)

-   Fixed: Bundle commands did not work correctly in the previous update.

## Revision 5567 (Thursday, November 22, 2018) — Version 1.12.2

-   Changed: Mojave-friendly status bar in the Composer. This also fixes other issues, in particular, for VoiceOver users.
-   Changed: Switched the order of the status bar and the header fields in the Composer. This is mainly to make it work better with “Full Keyboard Access” enabled.
-   Changed: Prevent macOS App Nap as long as there are open server connections in MailMate (which is most of the time for most users).
-   Changed: Added an “All / Junk / Deleted” mailbox to the default set of mailboxes.
-   Changed: Forwarding `multipart/report` is now forced to work like “Forward as Attachment”.
-   Changed: Displaying `multipart/report` is now less likely to hide a `message/deliver-status` subpart.
-   Changed: Minor performance improvement when synchronizing empty IMAP mailboxes.
-   Changed: The “automatically mark as read” feature has been tweaked to make it less likely to repeatedly mark messages read without user interaction.
-   Changed: Only open a single message when opening/following `message:`/`mid:`/`cid:` URLs even if multiple candidates are found.
-   Changed: Sticky messages now only affects the key window.
-   Changed: Account importer improved to be better at deriving hostnames and usernames based on email address.
-   Fixed: Various issues coloring quoted text and links in dark mode (Mojave).
-   Fixed: The `environment` key now also works for non-single-message bundle commands (without message value expansion).
-   Fixed: No longer forgets previous window frame on relaunch after going into full screen mode.
-   Fixed: Another tweak for handling Inbox vs INBOX.
-   Fixed: Various issues with the delta line height preference of the mailbox outline.
-   Fixed: Printing _after_ using the “Load Once” button to fetch images now works as expected.
-   Fixed: fn-return did not always work in the Composer (for opening links in a browser).
-   Fixed: `selectWithFilter:` with a format string now works if more than 1 message is selected (and if 0 are selected).
-   Fixed: Various coloring issues.
-   Fixed: Various VoiceOver related issues.
-   Fixed: IMAP busy loop issue when moving a message is rejected by the IMAP server. This could, e.g., happen if trying to move an email to the Gmail drafts mailbox.
-   Fixed: Coloring issue after collapsing/expanding mailbox items with a custom color/style.
-   Fixed: Parsing of parameters in `Content-Type` headers is a bit more robust. This also handles some incorrectly defined MIME boundary strings.
-   Fixed: Background color of preview.
-   Fixed: Various issues with the key view loop and initial first responder in the previous public release.
-   Fixed: Bright lines in draggable splitter on Mojave in dark mode.
-   Fixed: Issue where mailbox selection got lost after, e.g., moving a message.
-   Fixed: Mailbox chooser did not work correctly on macOS 10.10 and earlier.
-   Fixed: Crash bug for the “Message is (not)” menu in the conditions editor.

## Revision 5552 (Saturday, November 3, 2018) — Version 1.12.1

The following are all changes since the most recent public release (1.12). A lot is related to Mojave dark mode, but there are also many other improvements.

-   New: Mailboxes status bar updated for Mojave.
-   New: Mailboxes status bar now includes a quota level indicator if supported by the currently selected IMAP account.
-   New: Hidden preferences for detailed control of new quota display: `MmShowQuotaLevelIndicator`, `MmQuotaWarningLevel`, `MmQuotaCriticalLevel`.
-   New: Completely reimplemented the mailbox list (should fix various issues on both Mojave an earlier macOS releases).
-   New: `MmUseStandardBadgeLabel` hidden preference to force MailMate to use the system to draw the primary (red) dock badge.
-   New: Basic AppleScript support to access the selected messages of the front-most window and getting its header values.
-   New: The `MmWindowTitleFormatString` hidden preference is now also used in the Composer. Alternatively, use `MmComposerTitleFormatString` to set something explicitly for the composer.
-   New: The `mlmt:` URL scheme now supports selecting a specific mailbox.
-   Changed: Improved the default guesses for IMAP/SMTP hostnames based on the email address provided.
-   Changed: No longer making messages sticky if changes are caused by changes on the IMAP server.
-   Changed: MailMate is more patient when IMAP servers are slow at starting to return, in particular, large emails.
-   Changed: Improved updating the mailbox list when IMAP accounts synchronize.
-   Changed: Improved separator colors used in Mojave dark mode.
-   Changed: Slightly better at handling emails which claim to be UTF-8 but still contain a few errors.
-   Changed: Slightly better at finding standard mailboxes in IMAP accounts.
-   Changed: `MmDefaultBccHeader` now accepts a dictionary-mapping in order to be more flexible.
-   Changed: MailMate will not allow the user to move or delete dummy emails from 'Microsoft Exchange Server'. This should help users to avoid accidentally deleting various nonsensical non-emails provided by Exchange via IMAP.
-   Changed: Minor improvement when needing to derive a sender identity based on a “Received” header.
-   Changed: No longer silently fails if SpamSieve is enabled while MailMate has not been allowed to communicate with SpamSieve.
-   Changed: Optimization for determining when to display mailbox spinners.
-   Changed: Refactored some of the code used for rule editors (Mailbox/Conditions/Actions).
-   Changed: Internal code changes making it a bit less likely that future changes accidentally break MailMate on earlier macOS releases.
-   Fixed: Various issues with adding/removing inline images in Markdown mode.
-   Fixed: Various issues with layout of rule editors (Mailboxes/Conditions/Actions), in particular the off-by-one text placement in popups on Mojave.
-   Fixed: The action button menu below the mailbox list also includes quota information if available.
-   Fixed: Badge counters scale better now when resizing the mailbox list font.
-   Fixed: Long standing issues with empty values when creating menu items for finding related messages.
-   Fixed: Behavior when clearing a short display name for a tag.
-   Fixed: Drafts mailbox outgoing counter in proper red in Mojave dark mode.
-   Fixed: Colors of tips on Mojave.
-   Fixed: Simplified the use of styling for HTML messages to make dark mode usable until something better can be implemented.
-   Fixed: Some times MailMate would fail to save mailbox state when closing MailMate.
-   Fixed: It was possible to paste newlines into the subject header.
-   Fixed: Issue with “Edit Subscriptions” triggered when changing the hostname.
-   Fixed: Issue when deleting a tag which is also configured for display in the Tags toolbar button.
-   Fixed: Major rewrite to handle various issues with message selection in, e.g., the Unread mailbox (this might have introduced new bugs since it's a complex issue).
-   Fixed: Issue where creating some types of smart mailboxes resulted in an infinite recursion.
-   Fixed: Issue with the name part when adding to Contacts in the Composer.
-   Fixed: The shortcut for “Send Now” has been changed because the one recently added was already taken by the system.
-   Fixed: Some autolink issues with third party URLs.
-   Fixed: A warning about attaching folders some times disappeared immediately after being displayed.
-   Fixed: VoiceOver and other issues with the “View ▸ Layout” menu.
-   Fixed: Some times the message view would go blank in some types of layouts.
-   Fixed: Issue with enabling/disabling OAuth2 in the IMAP account settings window.
-   Fixed: Bug which caused MailMate to create a wrong Date header when close to changes in daylight savings time.
-   Fixed: Issues caused by line wrapping when redirecting a message.
-   Fixed: Raw display modes (source or HTML) did not work well in Mojave dark mode.

## Revision 5523 (Monday, September 10, 2018) — Version 1.12

The following are all changes since the most recent public release (1.11.3, July 10th).

-   New: Search by date using the toolbar search field. See “View Search Syntax” in the toolbar search field menu.
-   New: Date comparisons “is (not) within” has an option to limit the date to the current day/week/month/year/hour/minute. This allows, e.g., proper “Today” and “This Week” mailboxes.
-   New: For convenience, added “Message is Received Today/Yesterday/This Week/This Month/This Year” to the set of available conditions.
-   New: Automatically derived values in the account editor. In some cases, entering an email address is all it takes to setup an account.
-   New: Access group for AppleScript named `com.freron.MailMate.compose`. This allows sandboxed applications to create new messages with MailMate.
-   New: Explicit `open mailto` command for AppleScript to be used with AppleScript access groups.
-   New: An “X-Mailtags ▸ Keywords” specifier makes it easier to create a smart mailbox based on the `X-Mailtags` header of existing emails.
-   New: Smarter indentation behavior when pasting text at an indented caret position.
-   New: Hidden preference for users wanting to change the compliance setting of OpenPGP (`MmOpenGPGComplianceString`).
-   New: Hidden preference `MmHideImageBlockingBanner` (quick fix for users never wanting to see the image blocking view).
-   New: Key binding selectors `setFilterKey:` and `removeFilterKey:`
-   New: Control the margin in the Composer text field using `MmComposerMargin`.
-   Changed: Now automatically marks as read when emails are muted.
-   Changed: Now using the `.sdef` format for AppleScript.
-   Changed: AppleScript dictionary includes some of the standard commands (no new functionality).
-   Changed: The “Send/Cancel Send/Send Now/Edit as New Message” menu items and shortcuts have been changed. “Edit as New Message” works everywhere and the sending shortcut works when a draft is open. Trying to send an already pending message cancels the send (if possible) and opens the Composer window. Holding down ⌃ reveals a menu item which can be used to “Send Now” (useful in the drafts mailbox and/or for delayed emails).
-   Changed: Gracefully handling some types of invalid email addresses in Contacts.
-   Changed: Slightly better behavior when handling unexpected IMAP `BYE`responses.
-   Changed: “Take Online/Offline” are a bit more flexible now.
-   Changed: Allows split screen for all types of windows.
-   Changed: The `copyToMailbox:` key binding selector now works without a destination mailbox.
-   Changed: A notification is shown when messages are copied. Use `MmCopyMessagesNotificationEnabled` to disable this.
-   Fixed: Added `NSAppleEventsUsageDescription` to solve some of the problems talking to other applications on Mojave.
-   Fixed: Issue with context sensitive menu in address headers.
-   Fixed: Missing `NSContactsUsageDescription` caused a crash on Mojave. Also changed when MailMate asks for permission to access Contacts.
-   Fixed: A “top” inserted signature now appears below any text already entered in the Composer (this makes adding a signature after writing an email behave as expected).
-   Fixed: Issue with IMAP mailbox going from the `\\Noselect` state to normal state.
-   Fixed: Filename was invalid when attaching a `message/rfc822` file with no subject header.
-   Fixed: A sender configured without a name part did not work well in the From popup menu when re-opening the menu.
-   Fixed: Various issues with adding IMAP accounts with atypical mailbox names such as Inbox instead of INBOX.
-   Fixed: Attachment size in the message view no longer includes the size of the headers of the attachment. (It's still the encoded size and not the decoded size.)
-   Fixed: Now handles attachments of size 0 correctly when attaching.
-   Fixed: MailMate couldn't attach files with the `.xsl` file extension (and possibly others) due to a problem deriving a suitable MIME type.
-   Fixed: Some issues with completion of tag names.
-   Fixed: Improved completion ordering when the same email address is found in Contacts (or LDAP) and in previous recipients (but with differences in names).
-   Fixed: Issue with `toggleFilterKey:` not always applying to the currently selected mailbox.
-   Fixed: The popup for selecting a tag would often incorrectly show the corresponding IMAP keyword instead of the tag display name.
-   Fixed: Renaming never-synchronized “local” mailboxes did not work well.
-   Fixed: The code for displaying signed+encrypted emails was a bit too aggressive when identifying suspicious MIME structures.
-   Fixed: The `synchronize:` key binding did not work correctly without an argument.
-   Fixed: Image blocking now works when printing.
-   Fixed: `selectPreviousCountedMailboxRow:` did not work correctly.
-   Fixed: Crash related to “Include messages in submailboxes”.

## Revision 5509 (Tuesday, July 10, 2018)

The following is a list of some minor corrections to the recent 1.11.3 release. See further below.

-   Changed: Reverted back to the old code for expanding Contacts groups since Apple's “new” Contacts framework does not seem to support distribution lists.
-   Changed: The “delete” key works when focus is in the mailbox list.
-   Fixed: The previous release did not properly include the intended version bump to 1.11.3.
-   Fixed: Autolinking plain text URLs in HTML was broken.
-   Fixed: Issue with some custom key bindings in the Composer (related to the status bar).
-   Fixed: “Synchronize All” menu item was broken in recent releases.
-   Fixed: Detect when the image blocking mailbox configured no longer exists.
-   Fixed: Editing existing date-conditions with “exists/not exists” was broken.

## Revision 5507 (Thursday, July 5, 2018) — Version 1.11.3

The following are all changes since the most recent public release (1.11.2). Further below, you can also find a list of changes made for making MailMate work better on Mojave.

-   New: GUI setting in mailbox editor for including the messages in submailboxes. It is mutually exclusive with the existing Submailboxes feature. This is not strictly necessary, but combining them is not very useful (and very confusing).
-   New: Adding an attachment triggers the subject header in the composer to become the filename of the attachment (if the subject is empty).
-   New: Use `M` to include quoted text when searching headers and message bodies (`m` does not include quoted text).
-   New: LDAP now supports simple binds with username (dn) and password.
-   New: Key binding `synchronize:` can, optionally, be given a mailbox UUID as argument.
-   New: “Reset to Default” added to the “Synchronization Schedule” menu.
-   New: `selectPreviousCountedMailboxRow:` / `selectNextCountedMailboxRow:`
-   New: Single message window can initiate searches when clicking on header items.
-   New: “Show Thread/Correspondence” works in the single message window.
-   New: Hidden preference to explicitly control line spacing in the composer: `MmComposerLineSpacing`
-   New: The `orderFrontMessageViewer:` key binding can be used to bring the messages viewer window to front, e.g., when it's minimized.
-   Changed: The attachments-check (Composer preferences pane) now ignores the signature used in the message.
-   Changed: An address pattern triggers the “From” popup to appear even if only one account/address exists.
-   Changed: Workaround for server which (incorrectly) double quotes (some?) IMAP keywords.
-   Changed: Replaced many of the uses of the ABAddressBook framework with the CNContacts framework on 10.11+. This is work in progress which might be hard to complete without removing existing features.
-   Changed: Added workaround to better display emails generated by Thunderbird using blockquotes with `type="cite"`.
-   Changed: “Go to Source” menu item can now handle multiple emails.
-   Changed: Small optimization in the trial check.
-   Changed: Disabled automatic quote-substitution for HTML signatures in the Signatures preferences pane.
-   Changed: Added workaround to make `perform` work with JSX.
-   Changed: Rewritten code to handle any signed/encrypted emails with a suspicious HTML/MIME structure.
-   Changed: Renamed “Common Headers and Body Text” to “Common Headers and Unquoted Text”. Added a “Common Headers and Text” variant.
-   Changed: Now treating `message/delivery-status` as plain text to make it searchable.
-   Changed: IMAP strategy when failing to fetch messages due to server issues.
-   Changed: ⌥→ in the messages list always expands the entire thread even if the current item is already expanded.
-   Changed: Toggling online/offline for IMAP mailboxes now affects submailboxes if the mailbox is collapsed.
-   Changed: Updated the manual to describe the “Synchronization Schedule” setting.
-   Changed: “Synchronization Schedule” can be changed for multiple selected mailboxes.
-   Changed: Added tooltip to emphasize that drag'n'drop only works for attachment icons.
-   Changed: Major refactoring of how updated queries/sets are updated internally, in particular, how changes are reported to the various parts of the user interface. Some common actions are now a bit snappier, for example, navigating the message list with the message preview enabled.
-   Changed: “Print” menu item is greyed out when it's not available (relevant for the two pane and the statistics layouts).
-   Changed: Attempt to make MailMate fail a bit more gracefully when dealing with read-only mailboxes.
-   Fixed: Improved robustness of the `changeHeaders` bundle command action.
-   Fixed: Some times MailMate would try to make an encrypted connection even if it was asked not to do so.
-   Fixed: Recently introduced issue with the “File ▸ Synchronize” menu.
-   Fixed: The `synchronize:` key binding did not work as intended.
-   Fixed: Removed some useless menu items from context sensitive menus in the headers view.
-   Fixed: Bug making submailbox counts fail to work after adding new account(s). (It used to stay this way until relaunching MailMate.)
-   Fixed: Bug causing IMAP/SMTP connections to crash under certain types of connection issues. This primarily affected users with unstable networks (connection timeouts).
-   Fixed: Workaround for a “Send Feedback” and “Send Server Logs” related keyboard focus issue.
-   Fixed: Issue resizing the composer window which could result in a partially empty window.
-   Fixed: Issue where changes to mailbox conditions might be ignored if recomputing the mailbox query was slow.
-   Fixed: Changing the date in a condition using the before/after/equal comparison method did not dynamically update. In some cases, the changes were also ignored.
-   Fixed: Drag'n'drop in the “Mailboxes” pane and the “Conditions” pane did not work well. In some cases, the dragged conditions were removed when closing the window.
-   Fixed: Issue using “Send Now” on messages pending for submission.
-   Fixed: Issue using “is not” with multi value (virtual) headers (like “To” or “Any Address”). The bug has been present since the release of version 1.11 and affected new/changed mailbox conditions.
-   Fixed: Various issues with IMAP accounts using Inbox instead of INBOX.
-   Fixed: Some issues with menu/toolbar items being unavailable in tagging mode.
-   Fixed: Potential crash for IMAP accounts configured without a proper username.
-   Fixed: Minor memory leak and some potential bugs revealed by compiler.
-   Changed: Blacklisting email addresses (for address completion in the Composer) did not work well for non-lowercase email addresses.
-   Fixed: Blacklisting a recipient matching on both name and email address never really worked when completing recipients in the Composer.
-   Fixed: “Distortion Mode” has been broken for some time for the message view.
-   Fixed: Occasional crashes when getting access tokens on multiple threads. This was, in particular, an issue for users with numerous Gmail and/or Outlook accounts.
-   Fixed: Updating headers with multiple values (like recipient headers or the virtual headers handling IMAP keywords) did not always work correctly. This might fix _some_ of the known issues with the Tagged mailbox.
-   Fixed: Duplicating a mailbox (using the “Mailbox ▸ Duplicate” menu item) would often result in messing up the order of mailboxes after relaunching MailMate.
-   Fixed: Some times emails were incorrectly stuck in the currently displayed mailbox, e.g., after an undo operation.
-   Fixed: Thread size column resize issue.
-   Fixed: Looping behavior when offering the user to cancel deletion of messages for a read-only IMAP folder.
-   Fixed: Issue where the blocked-images-banner was incorrectly displayed.

The following is list of changes for working better with macOS Mojave. There are still many things to improve, but it should be usable for anyone already working on Mojave:

-   Fixed: Account import list background color in dark mode.
-   Fixed: Dark mode in messages import window.
-   Fixed: Rule editors look a bit better in dark mode on Mojave (still some layout issues).
-   Fixed: Message view background color when no messages are selected in dark mode.
-   Fixed: Coloring issues in search path controller in dark mode.
-   Fixed: Thread arcs background color in dark mode.
-   Fixed: Coloring issues in the Activity Viewer in dark mode.
-   Fixed: Various issues with coloring in the composer window in dark mode.
-   Fixed: Signature editor fixed for dark mode.
-   Fixed: Dark mode issue in the Security preferences pane.
-   Fixed: Unreadable banners in dark mode.
-   Fixed: Headers view and messages view changed to work better in dark mode (a bit of a hack for now).
-   Fixed: Message list now works in dark mode.
-   Fixed: Simplified layout code which implicitly fixed margin issues on Mojave.
-   Fixed: “Go/Move to Mailbox” in Mojave dark mode.
-   Fixed: “Send Later” text field in dark mode.
-   Fixed: Headers/Message view updates dynamically when switching to/from dark mode on Mojave.
-   Fixed: Dark mode improvement for attached emails.

## Revision 5479 (Tuesday, April 24, 2018) — Version 1.11.2

The following are all changes since the most recent public release (1.11.1):

-   New: Rules can be reordered. Hold down ⌥ to copy.
-   New: Rules can be dragged to other rule lists. Hold down ⌥ to copy.
-   New: Rules can be hierarchical (use drag'n'drop to make subrules or use the new actions menu).
-   New: Rules work with cut/copy/paste.
-   New: Rules can be deleted using the delete key.
-   New: A rule can be edited using the return/enter key.
-   New: Undo/redo works for rule reordering/dragging/cutting/pasting/deleting.
-   New: Actions menu in the rule editor which includes “Duplicate” and “Add Subrule...” menu items.
-   New: Boolean setting `includeSubmailboxMessages = 1;` can be used by manually editing `Mailboxes.plist`. A GUI for this feature is going to be added later.
-   New: Hidden preference `MmAutomaticallyExpandThreadsEnabled`(experimental).
-   New: Hidden preference `MmAutomaticallyExpandOnlyWhenCounted`(experimental).
-   New: If `MmReplyWroteString` is quoted then the following blank line is also quoted.
-   Changed: The description is no longer editable in the list of rules. Double-click opens the rule editor.
-   Changed: Added tooltip for the “Type” column in the rule editor.
-   Changed: New icon for the Expunge toolbar button such that it differs from the trash icon. (Thanks to Matt Petrowsky.)
-   Changed: IMAP code now able to cancel deleting messages when the messages are, for example, in a read only mailbox.
-   Changed: Any `text/rfc822-headers` MIME parts are now parsed as headers and displayed a bit nicer. This includes decoding the headers.
-   Fixed: Various issues related to collapsing a mailbox with any selected submailboxes.
-   Fixed: Sending a multipart draft could fail to work correctly if the draft had not been opened/viewed during the current launch of MailMate.
-   Fixed: Clicking on an `mid:` link in the composer preview had the weird and wrong effect of replacing both text view and preview with the linked message.
-   Fixed: Various minor issues and a few rare bad memory access bugs.

## Revision 5471 (Monday, April 9, 2018) — Version 1.11.1

The following are all changes since the most recent public release (1.11):

-   New: Hidden preference `MmDeleteBehavior`: `moveToDeletedMessages`, `markAsDeleted`, `expunge`, `archive`.
-   New: Hidden preference `MmAutomaticExpungeBehavior`: `mailboxSwitch`, `never`.
-   New: Accounts can be given their own `deleteBehavior` overriding the global default.
-   New: An Expunge toolbar button (which reuses the trash icon).
-   New: `MmRelativeDayDisabled` which can be used to disable the use of today/tomorrow in regular date columns.
-   Changed: Improved performance of some types of “is in” conditions when, e.g., moving/deleting emails. This should be very noticeable for some users.
-   Changed: The `expungeDeletedMessages:` key binding has been improved a bit to more easily allow a menu item.
-   Changed: The IMAP `GETQUOTAROOT` command has been changed a bit in an attempt to work around an iCloud IMAP bug (only affecting a subset of Apple servers).
-   Changed: Working around an issue with Gmail when sending without the Composer window (scripting).
-   Changed: Increased minimum width of the Tags column to allow at least 1 emoji.
-   Fixed: Improved behavior in low disk space situations (this should fix some rare cases of database corruption).
-   Fixed: Don't go to the “failed” state if already “offline” for a given mailbox (this fixes a race condition).
-   Fixed: A `multipart/related` inline image in a reply was not removed when dropping the embedded HTML if HTML was also generated for some other reason, e.g., when using Markdown.
-   Fixed: Removed some redundant conditions used in the default set of standard mailboxes.
-   Fixed: Various minor issues with completion of addresses, e.g., when these are automatically sorted.
-   Fixed: Workaround for unexpected `BAD` response from some servers with QUOTA support (iCloud).
-   Fixed: Some issues with mixed-case tag completion. Some minor improvements to other string field completions.
-   Fixed: It appears some servers just return NO when asked for quotas on an (existing) INBOX.
-   Fixed: The QUOTA support did not work correctly for IMAP accounts with no INBOX.
-   Fixed: Bug in the “Trial” mode handling.

## Revision 5462 (Monday, March 12, 2018) — Version 1.11

These are all changes since the latest public release (r5443, December 12th).

-   New: The conditions pane (also in rules) now have a “Message is” menu and a “Message is not” menu. These have submenus to easily match the “read” state, (colored) flags, and various other frequently used search conditions. It is not new that these searches can be made, but they should be much easier to do now.
-   New: Showing reminder that “Detach Message” is a useful feature when working with `multipart/digest` messages.
-   New: GUI setting for automatically adding trusted S/MIME certificates to the keychain. This includes telling the user when it happens and warning if a certificate already exists for the same email address.
-   New: A dedicated “Two Panes” layout with no message preview (see the “View ▸ Layout” menu).
-   New: First shot at support for . If the IMAP server supports this extension then MailMate shows the used quota (percentage) in the list of SOURCES.
-   New: The context sensitive menu of an IMAP account (with QUOTA support as described in RFC2087) displays the exact storage quota usage and limit. If multiple so-called quota roots exist then they are shown in a submenu.
-   New: The `MmQuotaWarningLevel` preference can be used to control when the used quota percentage is shown for IMAP accounts. The default is 80.0.
-   New: If the above fails for one or more servers then it can be disabled completely using `MmIMAPQuotaDisabled`.
-   New: Forwarding (as an attachment) is now available as a rule action.
-   New: Loop detection for forwarding actions.
-   New: Hidden preference to disable spoof detection (`MmNospoofSymbolDisabled`). You need a good reason to use this.
-   New: Hidden preference `MmComposerUsesScreenFonts`.
-   New: Hidden preference _only_ to be used for experiments: `MmNeverAllowFormatFlowed`.
-   Changed: Major refactoring of _all_ so-called rule editors (mailboxes pane, conditions and rule actions). This should make it much easier to add features to these in the future.
-   Changed: Major refactoring of the internal query system (e.g., used by smart mailboxes). This includes bug fixes and simpler (more robust) code.
-   Changed: Added newline after insertion of a `cid:` URLs.
-   Changed: The “Send Unencrypted” button is no longer the default (to make it less likely to do it by mistake).
-   Changed: Improved support for tags in the Composer window. Also, the Tags popup button is available for the Composer window.
-   Changed: Tweaked date parser to handle yet another type of invalid date header.
-   Changed: Improved handling of long URLs in encrypted emails.
-   Changed: Image blocking is no longer optional for encrypted emails.
-   Changed: “Set Tag” rule action renamed to “Set Tag/Keyword” to make it clear that it handles more than tags.
-   Changed: MailMate now reports whether or not S/MIME signature certificates are in the keychain and/or if they have recently been automatically added by MailMate (if `MmAutomaticallyAddCertificatesToKeychain` is enabled).
-   Changed: No longer tries to send via SMTP if a username is provided for an account while the server has no authentication methods available on that port (this can happen for port 25 on some servers).
-   Changed: Disabled some misleading “distortion” in the Composer when Distortion Mode is enabled (distortion mode is not intended to be used with the Composer at all).
-   Changed: `MmCommandsIncludeCollapsedMessages` is now enabled by default.
-   Changed: Removed an old and unnecessary workaround used when message files cannot be found on disk.
-   Changed: The “Copy to Folder” command is now a bit more flexible with the use of an `MmExportPattern` preference. A better and more general solution is needed though.
-   Changed: A message marked as both `\Deleted` and `$NotJunk` no longer blocks image references if the image blocking setting tells MailMate to not block images for `$NotJunk` messages.
-   Changed: Slightly better at handling the creation of a new uppercase tag like “TODO” when something like “Today” already exists.
-   Changed: Lowered minimum width for the Activity Viewer.
-   Changed: Detect and handle Exchange-style connection throttling.
-   Changed: If changing the “Bcc” header manually then the change sticks even if the sender is changed manually/implicitly.
-   Fixed: “Detach Message” did not work correctly if the message was encoded (using QP or Base64).
-   Fixed: The `#nospoof` specifier also works for `*.name.first` and `*.name.last`.
-   Fixed: Attempt to fix rare crash bug when subscribing/unsubscribing a mailbox.
-   Fixed: Some times MailMate auto-extracted (to be specific, an Apple framework auto-extracted) certain types of files when saving them.
-   Fixed: Some issues with the sharing extension including a crash (after sharing).
-   Fixed: When setting up the displayed tags for the “Tags” toolbar button then it wouldn't work properly until after relaunching MailMate.
-   Fixed: Disabling a rule action had no effect.
-   Fixed: The “Search with Google” menu item in the message view was broken.
-   Fixed: `MmInternalRecipients` is now automatically interpreted as being case insensitive.
-   Fixed: Issues with a single letter/symbol at the beginning of the name of an identity (“Email Address(es)” in the account editor).
-   Fixed: Keep the hidden state of views when opening a new mailbox window.
-   Fixed: Crash related to the new non-spoofing code combined with low-level user specifier customizations.
-   Fixed: Somes issues with autolinking HTML messages.
-   Fixed: Added “decade(s)” to date parsing :)
-   Fixed: Various security related issues.

## Revision 5443 (Tuesday, December 12, 2017) — Version 1.10

These are all changes since the latest public release (October 11th, r5425):

-   New: Whenever MailMate displays the name part of an email address, any occurence of `@` is replaced with `💀`. This helps the user spot attempts to spoof an email address.
-   New: `#nospoof` specifier to use when displaying email address headers.
-   New: Another workaround for Exchange IMAP. Some uploaded messages are rejected with a nonsensical IMAP BAD response. It appears this can be triggered by certain types of encoded headers. MailMate now tries to automatically fix these headers before uploading again.
-   New: Hidden preference to always launch in an offline state: `MmInitialOfflineStateEnabled`
-   New: Key binding for toggling all accounts offline/online: `toggleOnlineStateOfAllAccounts:`
-   New: `MmStripXMailerBeforeSending`
-   New: Optional toolbar buttons to mark unread/read (needs better gfx).
-   New: Experimental scripts for stripping signatures and banners when replying.
-   New: Bundle commands can request attachments (or any other message parts) to be provided as files.
-   New: Bundle commands can return attachments to be included in created emails (both new ones and replies).
-   New: Bundle commands can return actions in JSON format.
-   New: Hidden preference for reply behavior when no text has been selected: `MmNoTextForRepliesByDefault`
-   New: The primary dock badge counter now looks like other applications. The old style counters can be enabled using `MmUseOldStyleCounters`.
-   Changed: Printing respects order in the message list.
-   Changed: Single-click can toggle a flag in the message list.
-   Changed: The parser is now “skipping” an email address in the name-part of address headers if it is identical to the real address of the same header.
-   Changed: Now capable of displaying `text/x-watch-html` if explicitly told to do so (using “Previous/Next Alternative”).
-   Changed: MailMate behaves the same with respect to OAuth2 for `imap.outlook.com` and `imap-mail.outlook.com`. The same goes for `smtp`.
-   Changed: Renamed `runScript` to `runCommand` for bundle command actions since this was more accurate.
-   Changed: If possible, MailMate now deselects a mailbox before renaming. This works around an iCloud IMAP bug for the `IMAP RENAME` command.
-   Changed: Renaming mailboxes is now a bit more robust when mailboxes are in an unexpected state (various combinations of subscribed/created).
-   Changed: Minor optimization to avoid the overhead of single-line bash-scripts in commands.
-   Changed: Added script for more easily creating a new bundle (`SharedSupport/bin/create_bundle`).
-   Changed: Added tooltip for very long attachment names in the Attachments popup in the Composer.
-   Changed: Collapsed thread still shows attachment icon in message list if any attachments exist in the thread.
-   Changed: An outlined flag is now shown when a collapsed thread contains one or more flagged messages.
-   Changed: The correspondence outline no longer includes unexpanded children when, e.g., archiving -- except if the correspondence outline is focused.
-   Changed: Updated the embedded command for parsing `tnef` files.
-   Changed: Optimized some date related computations (this should make date-based smart mailboxes _much_ faster).
-   Changed: Sending to a group (Contacts) works when done with a `mailto:` URL. This includes when it's done using the “Send...” menu item in Contacts.
-   Changed: “Last of Thread” also works when multiple messages are selected (a bit random though).
-   Changed: Log when a key bindings file cannot be loaded or parsed.
-   Changed: Using `MmAdditionalComposerHeaders` now also affects the set of allowed headers when constructing new messages, e.g., using a `mailto:` URL or `emate`.
-   Changed: Blacklisting now also allows blacklisting a specific name/address combination.
-   Changed: Switched various text fields to single line mode.
-   Changed: Undo/Redo now works for attachments added in the Composer.
-   Changed: Added warning when pasting in the Composer results in attaching one or more files.
-   Changed: Attempt to detect and handle when Outlook accounts go into a throttled mode.
-   Changed: The `internalAddressPattern` is now case insensitive by default.
-   Fixed: Consistently use `script` instead of `command` in the included commands/filters.
-   Fixed: The parser now handles the Mailsploit test cases.
-   Fixed: Small improvement to avoid the cancellation of HTML signature insertion in the preview.
-   Fixed: An issue with extraneous whitespace above an HTML signature in non-Markdown mode.
-   Fixed: Wrong “shebang” in some of the included bundle commands.
-   Fixed: Some layout and coloring issues in the mailbox editor (High Sierra).
-   Fixed: Improved parsing of email client version strings.
-   Fixed: Behavior of `goToMailbox:` when having an active search -- and some related focus issues.
-   Fixed: The `mailto:` handler skipped the `body` argument.
-   Fixed: Group names (from Contacts) in the Composer were forgotten if closing/sending without first hitting return.
-   Fixed: Issue in the message preview in which the HTML signature was some times not shown.
-   Fixed: Attempt to prevent a rare crash when updating the preview after changing sender.
-   Fixed: Various issues in the Tags preferences pane.
-   Fixed: Some issues with auto-scrolling the preview related to code/math segments.
-   Fixed: An issue on 10.8 with opening the Rules pane.
-   Fixed: Case sensitivity issue for blacklisting email addresses.
-   Fixed: Scrolling did not work well in text fields when editing conditions.
-   Fixed: The “Mailbox ▸ Edit Rules” menu item often failed to do what it was supposed to do.
-   Fixed: Crash bug when renaming accounts.
-   Fixed: Attempt to fix a problem with a crash while quitting.
-   Fixed: Closing the single message window automatically did not work for “Move to/from Junk”.
-   Fixed: Spotlight and the custom location feature now use relative paths. The previous approach would lead to problems if the username of the account was changed.
-   Fixed: Some issues with the Spotlight importer and the sharing extension on High Sierra.
-   Fixed: `MmOpenMessageURLInContext` also works when opening `.eml` files.

The bump to version 1.10 (instead of 1.9.8) is motivated by the fact that there has been _a lot_ of improvements to MailMate since version 1.9 was released in March 2015, but the version numbers have not reflected this. It would have been nice to bump it to 2.0, but MailMate is just not ready for that yet.

## Revision 5425 (Wednesday, October 11, 2017)

These are all changes since the latest public release. Several of them are related to High Sierra.

-   New: Hidden preference `MmCommandsIncludeCollapsedMessages` which changes the behavior when running a command on collapsed message threads. This is likely to become default behavior.
-   New: Hidden preference `MmOpenMessageURLInContext` to tell MailMate to handle `message:` URLs by opening a window with the IMAP mailbox of the message selected.
-   Changed: Disabled dragging attachment file names on High Sierra since I cannot make it work correctly. Drag the icon instead.
-   Changed: Changed `<pre>`-segments to wrap text when printing (instead of nonsensical scrolling).
-   Changed: Various minor changes needed to compile with the 10.13 API and Xcode 9.
-   Changed: Workaround for a server wrongly returning a 64 bit `UIDVALIDITY`value. (This is not 100% robust, but it's good enough given the server is to blame for the problem.)
-   Changed: The `changeHeaders` action can also handle virtual headers now.
-   Changed: Experimental workaround for a Yahoo IMAP server issue (the server issue might be fixed now though).
-   Fixed: The sharing extension is now a bit better at handling text input, e.g., when sharing a note in the Notes app. (Only plain text handled for now.)
-   Fixed: Workaround for High Sierra WebView issue affecting, e.g., some emails from PayPal.
-   Fixed: Issues using toolbar buttons in an unfocused window (holding down ⌘).
-   Fixed: Window title did not always show the correct number of selected messages.
-   Fixed: Don't try another IMAP authentication method when the first one fails due to a timeout.
-   Fixed: Sorting was incorrect for the “Correspondents” column.
-   Fixed: Enabling/disabling some types of mailbox/search conditions would clear the text field or fill it with some old value.
-   Fixed: MailMate did not allow adding some types of S/MIME certificates to the keychain.
-   Fixed: “Open Attachment” now works for attached emails.
-   Fixed: Table in key bindings manual page was not readable.

## Revision 5419 (Friday, September 22, 2017) — Version 1.9.7

It has been a long time since the latest public release of MailMate (r5347, February 17), but this does not mean that nothing has happened. You can find the detailed release notes further below in the Beta 1-3 descriptions.

The following is a shorter (slightly rewritten) list of some of the most notable highlights:

-   Improved single message window behavior. It is now “connected” to the main window such that undo/redo behavior is better and features (key bindings) such as “Move to Mailbox...” work as expected.
-   The “Apply Rules” menu item is now a menu which allows applying rules to either selected messages or the entire mailbox.
-   “Export ▸ Copy to Folder” command which exports `.eml` files into a folder hierarchy matching the original accounts. Duplicates are automatically avoided and the command can be used as an action in mailbox rules.
-   Internal changes to provide an action for bundles which allows changing header values of existing emails. This feature is currently used to implement “Command ▸ MailMate ▸ Change Subject”.
-   Email addresses can now be blacklisted such that they are not used for completions in the Composer.
-   Low-level, the message list supports coloring and styling lines. This feature is described in more detail [here](https://freron.lighthouseapp.com/projects/58672-mailmate/tickets/204#ticket-204-7).
-   Numerous new hidden preferences for users that like to tinker with the details.
-   Manual pages updated to include some of the previously undocumented features.
-   Improved behavior for various problematic IMAP servers including Gmail and Exchange IMAP.
-   Uses the IMAP `RENAME` command when an IMAP mailbox is renamed (also when a hierarchy is involved). This is both more robust and more efficient than before.
-   Now doing Gmail “OAuth2” authorization through an external browser.
-   Improved composer text view including fixing various display issues.
-   Improved autoscroll in the composer preview.
-   Improved and fixed S/MIME handling which now also allows separate certificates for signing/encrypting.
-   Improved behavior for window tabs on Sierra and later macOS versions.
-   Fixed various issues on High Sierra.

## Revision 5418 (Thursday, September 21, 2017) — Version 1.9.7 Beta 3

The following are all changes since the Beta 2 release (r5412):

-   New: “Mailbox ▸ Edit Rules...” menu item added for convenience. Opens the mailbox editor and switches to the Rules pane.
-   New: The “Apply Rules” menu item is now a menu which allows applying rules to either selected messages or the entire mailbox. There are shortcuts for both variants.
-   New: “Copy to Folder” command which exports `.eml` files into a folder hierarchy matching the original accounts. Creates unique filenames using date and a SHA256-substring.
-   New: Experimental `goToDestinationMailbox:` key binding.
-   Changed: Using the sharing extension now brings the created message to the front.
-   Changed: The “Message ▸ Edit as New Message” menu item now creates a new draft if a draft is selected.
-   Changed: Updated manual pages with various missing information including some hidden preferences and key bindings.
-   Changed: Workaround for Exchange IMAP issue which seems to have gotten worse lately. MailMate now detects the non-sensical error message and temporarily takes the account offline (“unavailable” state) without disturbing the user.
-   Fixed: Minor visual bug in the default mailbox menu in the toolbar search field.
-   Fixed: The redirect rule action was broken.
-   Fixed: Under certain circumstances “File > Import Messages...” would wrongly be in a disabled state.
-   Fixed: Cancelling a folder panel after selecting the “Other...” menu item in a folder popup would lead to an inconsistent state.
-   Fixed: Recipient headers have more consistent context sensitive menus. This is better for VoiceOver users.

## Revision 5412 (Monday, September 4, 2017) — Version 1.9.7 Beta 2

Mostly fixes and minor changes and new features. Also see the Beta 1 release notes further below since it was never properly released as a beta.

If you are on MacOS High Sierra (10.13) then please report any issues you might have seen.

-   New: “Move to Mailbox...” works in the single message window.
-   New: Hidden preference `MmComposerMaximumNumberOfRecipientLines`(default value is 6).
-   New: Hidden preference `MmAttachmentButtonsOnLeft`.
-   New: Hidden preference `MmSaveAttachmentNotificationEnabled` (enabled by default).
-   New: Hidden preference `MmHTML2TextArguments` can be used to provide additional arguments to `html2text`, e.g., `--ignore-links`.
-   New: Hidden preference `MmAllowedImageURLRegexp`.
-   New: Hidden preference `MmMessagesWebViewMarksUnreadOnlyIfSingleMessage`.
-   Changed: Hide password fields (instead of just disabling) when OAuth2 is enabled.
-   Changed: Updated the embedded version of `html2text`.
-   Changed: Optimized all PNGs and stripped metadata (using `optipng -strip all`).
-   Changed: Better handling of some types of connection problems when sending.
-   Changed: Refactored `MmAutomaticUnwrapEnabled` a bit. It now also applies to displayed plain text (useful when combined with “Prefer Plain Text”).
-   Changed: Now much smarter about updating colors and links in the composer window. This should solve some display issues (temporarily disappearing lines).
-   Changed: Most key bindings (menu items) now work in the single message window.
-   Changed: Improved the S/MIME code for finding certificates.
-   Changed: Avoid duplicate `--recipient` arguments when using `gpg2`(OpenPGP) to encrypt messages also sent to one self.
-   Changed: Attempt to improve handling of throttled connections.
-   Fixed: Behave nicely if `MmDefaultBccHeader` is not a string value.
-   Fixed: Issue with using the toolbar button to disable an enabled flag for the root message of a collapsed thread.
-   Fixed: Issue with moving/deleting messages failing in the single message window under certain circumstances.
-   Fixed: Issue with dragging a Calendar event to the MailMate dock icon (and possibly related issues).
-   Fixed: The relative date column combined with organizing by thread did not work well when sorting.
-   Fixed: Some times MailMate would try regular SMTP authentication methods (unsuccessfully) even if OAuth2 was enabled.
-   Fixed: Application icon now works correctly on High Sierra.
-   Fixed: Users with a 12 hour clock locale setting would often see wrongly formatted dates.
-   Fixed: The `MmSingleMessageWindowClosesAfterMove` preference would fail if there was no next message selected in the main window.
-   Fixed: Broken link in the About window.
-   Fixed: Issue which might cause a slow or flickering composer window for some users.
-   Fixed: Some times the SMTP code would fail to retry sending (after certain types of network errors).
-   Fixed: Issue saving plist files using certain types of UTF-8 characters. This implicitly fixes an issue with some smart folders not displaying any messages after launching MailMate.
-   Fixed: Now works as expected in the message preview if space has been remapped to `scrollPageDownOrNextUnreadMessage:`.
-   Fixed: Exception when printing an email.
-   Fixed: Issue handling some extremely long header lines with a large number of encoded words.
-   Fixed: Various issues with editing in the Mailboxes pane of the mailbox editor when one or more mailboxes used no longer exists.
-   Fixed: The `MmDefaultBccHeader` hidden preference did not work correctly for “Edit as New Message”.
-   Fixed: Issue with a workaround for malformed emails which wrongly uses `quoted-printable` encoding for a `multipart/*` message part.
-   Fixed: Better detection of overflowed UID values in the IMAP code.
-   Fixed: Bug in the experimental `MmDisableMatchEmailAddressIfPresent`S/MIME related setting.
-   Fixed: It appears MailMate can some times register a negative “last seen UID” (possibly triggered by a buggy IMAP server). This is now handled more gracefully.

## Revision 5383 (Wednesday, June 21, 2017) — Version 1.9.7 Beta 1

Cleaned up release notes. The following are all changes since the latest public release in February (1.9.6r5347):

-   New: Hidden preference `MmSingleMessageWindowClosesAfterMove`.
-   New: Tags can now be sorted alphabetically by clicking on the “Display Name” column header.
-   New: Hidden preference to automatically add valid signing certificates to the keychain: `MmAutomaticallyAddCertificatesToKeychain`.
-   New: “Send Unencrypted” button whenever encryption fails for a message, e.g., when certificates cannot be found for one of the recipients.
-   New: Hidden preference `MmInternalRecipientsCheckEnabled` (this doesn't affect exclamation mark, but it can be used to silence the window alert).
-   New: “Import All” option when restoring autosaved drafts.
-   New: Hidden preference `MmNotificationInlineReply`.
-   New: Strikethrough support using the Unicode combining character (“Format ▸ Strikethrough”).
-   New: Some “Copy”-related menu items for email addresses entered in the composer window.
-   New: Experimental key binding to force MailMate to trust quoted paragraphs to be Markdown: `assumeQuotedTextIsMarkdown:`.
-   New: Experimental key binding selector for LTR justification in the editor: `toggleWritingDirection:`.
-   New: Experimental hidden preference `MmDoNotSendFromOfflineAccounts`.
-   New: Very experimental hidden preference `MmDarkModeEnabled` (don't ever expect this to completely work as expected).
-   New: It's now possible to manually (low level) setup multiple SMTP servers for 1 IMAP account.
-   New: Internal changes to provide an action for bundles which allows changing header values of existing emails.
-   New: “Command ▸ MailMate ▸ Change Subject” as an example of the feature noted above.
-   New: The message list coloring feature has been changed to a message styling feature also allowing bold/italic fonts. Note that the `Colors.plist` file should now be named `Styles.plist`.
-   New: Email addresses can now be blacklisted (such that they are not used for completions).
-   New: Event type `display_html` to be used for experimental bundle commands.
-   Changed: Some malformed messages with S/MIME signed content would inconveniently make MailMate hide subparts.
-   Changed: Improved handling of the ordering of tags.
-   Changed: If the current focus is lost when switching layout then MailMate now puts the focus in the message list.
-   Changed: The Statistics layout now caches its settings such that switching layout does not reset them.
-   Changed: Improved behavior when trying to synchronize an LSUB'ed mailbox which doesn't actually exist.
-   Changed: Added some tooltips for the Bundles preferences tableview.
-   Changed: Header values are now also distorted in distortion mode in the statistics layout.
-   Changed: Added “Sender” header to the list of headers supporting “Correspondent/Identity”.
-   Changed: Added the “Sender” header to the list of headers which allow the Name and Address specifiers.
-   Changed: The Mailboxes pane in the mailbox editor now allows no mailboxes to be configured. This makes it a simple empty mailbox useful for grouping mailboxes.
-   Changed: Group mailboxes (smart mailboxes with no mailboxes defined in the Mailboxes pane) are now (again) displayed using a general folder icon.
-   Changed: The `\\Recent` flag is now handled better for servers supporting the CONDSTORE IMAP capability.
-   Changed: System menu items now included in the context sensitive menu of the headers view.
-   Changed: No longer showing empty framed parts for partly signed messages.
-   Changed: Some improvements to the single message window which should make its integration with the mailboxes viewer better -- including undo when deleting.
-   Changed: Slightly improved behavior for `MmNotificationInlineReply`.
-   Changed: Now makes an effort to _not_ generate long IMAP commands. Some servers, e.g. Exchange IMAP, cannot handle it.
-   Changed: Uses IMAP RENAME when an IMAP mailbox is renamed (also when a hierarchy is involved).
-   Changed: Rewrote code looking for certificates when doing S/MIME signing/encryption. Should be better at handling separate certificates for signing/encrypting. Also better prepared for a possible future GUI to select certificate among multiple candidates.
-   Changed: MailMate now handles inline OpenPGP content even if it is wrongly placed within a standalone HTML body part.
-   Changed: Improved embedding of some types of HTML emails when replying/forwarding.
-   Changed: Slightly better at handling not having any identities available.
-   Changed: MailMate now suggests trying application specific passwords when authentication fails for iCloud/Yahoo accounts.
-   Changed: Allows “Flags >> Color” in the popups (this is a temporary solution to allow submailboxes based on colors).
-   Changed: Now doing Gmail “OAuth2” authorization through an external browser.
-   Changed: Autoscroll in the composer preview should work much better now.
-   Changed: Stylesheets are now inlined in order to avoid some flickering issues.
-   Changed: Network changes are now detected in order to improve behavior for accounts in the “unavailable” state.
-   Changed: Now allows `--header "#markup: markdown"` to be used with the `emate` command.
-   Changed: Optimized some types of “is in” queries.
-   Changed: Strategy for how long to wait before re-issuing the IMAP IDLE command.
-   Changed: Improved error messages for bad/untrusted signatures for S/MIME messages.
-   Changed: Improved error message when decrypting an OpenPGP message which is signed by an identity for which no public key can be found.
-   Changed: Improved behavior for window tabs on Sierra. Note the setting in the Dock System Preferences pane. Hold down the command key when clicking plus to open a composer window. Hold down option/alt when opening a new window to get a tab (in 'manual' mode in the Dock system preferences pane).
-   Fixed: Some times MailMate would wrongly try password-authentication for Gmail connections.
-   Fixed: Better handling of uncommitted text field changes in Preferences.
-   Fixed: Issue when adding a signing certificate to the user keychain.
-   Fixed: When using `MmInternalRecipients` then drag'n'drop some times misbehaved. This also affected copy vs. move behavior (the display of a plus is still wrong).
-   Fixed: Replies created from selected text did not handle extraneous whitespace very well.
-   Fixed: _Some_ issues with selecting text before replying/forwarding.
-   Fixed: “Mark as Not Junk” button did not work when the focus was in the mailbox outline.
-   Fixed: Enabling Markdown mode or window resizing would some times insert what seems to be an unwanted newline (it's actually a deleted space character).
-   Fixed: Minor menu title bug related to showing HTML source.
-   Fixed: CSS-styling in the preview when using Markdown in a message with non-Markdown quoted content.
-   Fixed: Quote level issue when generating HTML for HTML-styled non-Markdown emails.
-   Fixed: Various issues with retrying IMAP authentication with passwords. In particular with servers (like iCloud) which immediately close a connection when authentication fails.
-   Fixed: IMAP issue with EXPUNGE (deleted messages) during initial synchronization of a mailbox.
-   Fixed: Issue when changing a password without storing it in the keychain (while a different password is stored in the keychain).
-   Fixed: Some inefficiencies when permanently deleting messages.
-   Fixed: Various issues renaming/moving/deleting IMAP mailboxes.
-   Fixed: Improved/optimized behavior when new IMAP mailboxes appear within an IMAP mailbox.
-   Fixed: Extra code check to ensure that emails are never sent with unresolved OpenPGP or S/MIME related problems.
-   Fixed: Issue with forwarding messages with an empty Subject header.
-   Fixed: IMAP subscriptions editor did not work correctly when holding down ⌥(option/alt) when trying to client-unsubscribe all mailboxes.
-   Fixed: Subscriptions window Server column was too narrow to display the header.
-   Fixed: IMAP issue when a mailbox is deleted server-side while it still has non-uploaded emails client-side.
-   Fixed: The “red” link display did not work well when links contained `<wbr>` tags (which appears to be inserted somewhat randomly in links by some email clients).
-   Fixed: “Cancel and Edit Message” did not work correctly for redirected messages scheduled to be sent later.
-   Fixed: Sudden termination issue when replying/forwarding certain types of messages without using the preview in the main window.

## Revision 5347 (Friday, February 17, 2017)

These are the changes since the latest public release (r5344, February 8).

-   New: Hardcoded a dynamic filter system. Setup a key binding like this to try it out: `"u" = ( "toggleFilterKey:", "unread" );`.
-   New: “Drafts” display count menu now also has a special counter counting all pending messages (which includes message to be sent later).
-   Changed: The “MailMate ▸ Copy...” menu items also sorts and removes duplicates now.
-   Changed: If a signature does not end with a newline character then a newline is inserted before it's used. This solves issues with missing newlines when inserting signatures, e.g., when forwarding.
-   Changed: Improved feedback when verifying signatures fails. This applies to both OpenPGP and S/MIME signed messages.
-   Changed: Improved OpenPGP GUI feedback for messages both encrypted and signed.
-   Fixed: Various issues with verifying S/MIME signed messages.
-   Fixed: The toolbar “Redirect” icon is no longer identical to the Forward icon.

## Revision 5344 (Wednesday, February 8, 2017)

These are all the changes since the latest public release (r5319).

-   New: Mailbox display counts now support a mailbox condition and a color. This is used to emphasize the number of pending unsent drafts.
-   New: “Delete” and “Delete Permanently” mailbox rule actions.
-   New: “Command ▸ MailMate” now includes various “Copy” menu items to easily collect subjects or senders from a selection of messages.
-   New: Optional “Redirect” toolbar button (currently reuses the graphics used for the “Forward” button).
-   New: Hidden preference: `MmAlwaysMarkRepliedEmailsAsRead`.
-   New: First (low level) shot at allowing coloring messages in the messages outline ([ticket #204](https://freron.lighthouseapp.com/projects/58672/tickets/204)).
-   New: “Show in IMAP Mailbox” in the submenus of the main menu (counters).
-   New: `sortOrder = reverseAlpha` can be used to reverse the ordering of submailboxes in the `Mailboxes.plist`. This is a quick fix to allow reversing the order of date based submailboxes.
-   New: “Outgoing” count available for the Drafts folder. This is red to clearly indicate when something is pending to be sent. This should make unexpected behavior and/or bugs when sending more apparent.
-   New: Hidden preference to open URLs in background by default `MmOpenURLsInBackground` (revert behavior with the ⌘ key).
-   New: `MmIMAP4rev1CheckDisabled` (workaround for buggy or maybe just very old server).
-   Changed: Encrypted signed messages are now generated in a 2-step process for both OpenPGP and S/MIME. The goal is to make it work better with iOS Mail and possibly other email clients.
-   Changed: Only look for non-expired S/MIME certificates and only use expired certificates if they are explicitly trusted (and then still prefer any available non-expired certificates).
-   Changed: Improved display of links in the Composer.
-   Changed: Allow UTF-8 in URLs when auto-linking.
-   Changed: Default count for the universal Drafts mailbox is now “Outgoing” (a red counter counting pending messages).
-   Changed: Removed “Show Colors” menu item since it had not purpose.
-   Changed: Attempt to work around a rare crash bug related to mailbox spinners.
-   Changed: Debug output includes the serial number of certificates found when signing/encrypting.
-   Changed: Workaround when forwarding emails with a PDF within `multipart/alternative` (the PDF is now attached).
-   Changed: Missing charset in header encoded words is now assumed to mean UTF8.
-   Changed: Cancelling an empty search now also returns focus to the message list.
-   Changed: Reversed ordering when opening multiple message windows (oldest at top).
-   Changed: Reversed ordering of windows when replying to multiple messages.
-   Changed: Slightly better at handling an HTML signature when it's not clearly separated from the main body with an empty line.
-   Changed: Slightly better behavior when replying to selected text (far from perfect).
-   Changed: Experimentally caching syntax highlighted sections. This is work-in-progress.
-   Changed: When printing, `Resent-` headers are now included.
-   Fixed: Finally found a solution to the Gmail looping issue seen by some users (related to “[Gmail]/All Mail”).
-   Fixed: Moving from “[Gmail/All Mail” to another mailbox could some times result in the `\Deleted` flag being set on the message (side effect of non-standard Gmail behavior).
-   Fixed: Crash bug when trying to create a new message while not having any identities configured (missing or invalid email addresses in all IMAP account settings).
-   Fixed: Focus in the message list was lost when switching mailboxes.
-   Fixed: Various bugs when deriving the default sign/encrypt state when based on history.
-   Fixed: “Edit as New Message” now also maintains security settings (protocol, sign/encrypt).
-   Fixed: Some issues with the hidden preference for mapping to specific S/MIME certificates.
-   Fixed: Opening multiple mailbox editors in one go would make MailMate hang.
-   Fixed: The colors of mailbox counters in the mailbox list were not updated when switching key window.
-   Fixed: Improved behavior when using toolbar buttons to move messages while using, e.g., the Correspondence layout.
-   Fixed: Issues with plain text conversion to HTML on macOS 10.8. This, e.g., affected HTML signature insertion.
-   Fixed: The context sensitive “Remove Attachment” menu item was accidentally unavailable.
-   Fixed: The code for parsing multiple recipients in address headers was broken when used to complete email addresses in the composer.
-   Fixed: Increased width of Security column in order to display symbols on Sierra.
-   Fixed: Improved behavior when using drag'n'drop with a `data:` URI.
-   Fixed: Issue when generating HTML from plain text (the last character was some times swallowed).

## Revision 5319 (Wednesday, December 21, 2016)

-   Changed: MailMate now requires macOS 10.8. For anyone interested, 0.4% of MailMate users are on 10.7. This is less than the number of users still using MailMate on 10.6 (0.7%).

## Revision 5318 (Saturday, December 17, 2016)

The following are all changes since the latest public release (r5310). It should also fix some issues reported concerning authentication of Gmail accounts. If you still have issues with Gmail then let me know via “Help ▸ Send Feedback”.

-   New: Thread Size column for the messages list.
-   New: Key binding selectors `saveMailboxExpansions:` and `restoreMailboxExpansions:`.
-   Changed: `NSSupportsAutomaticGraphicsSwitching = YES` in the Info.plist. In theory, this should prevent MailMate from using the discrete GPU.
-   Changed: Ignore the command key when using key binding selectors to trigger `goToMailbox:`.
-   Changed: Small change to how a refresh/access token is fetched which might be more robust with Gmail.
-   Changed: Now allowing `*` in URLs when auto-linking.
-   Changed: Improved code for making server connections (should improve behavior for SMTP port 587).
-   Changed: Never accept send later dates in the past.
-   Changed: Minor changes to sharing extension.
-   Changed: Opening a new mailbox window now copies the layout from any existing (front-most) mailbox window.
-   Fixed: Long standing issue with ⌥F2 selecting the wrong word in the composer window.
-   Fixed: Some `message:` URLs were not properly interpreted.
-   Fixed: Hang in the rules action editor when setting up redirection.
-   Fixed: Using an HTML signature failed if inlining any paragraph styling.
-   Fixed: Various missing Retina graphics.

The new features below are experimental and currently only work with the following hidden preference enabled:

```
defaults write com.freron.MailMate MmTwoPointOhFeaturesEnabled -bool YES
```

-   New: “Remove Attachment” in the context sensitive menu of each attachment. Synchronizes with the IMAP server. Note that undo works.
-   New: **Experimental** new keybinding selector `removeAttachments:`. Removes all attachments of all selected messages. Note that undo works.

There's an unresolved issue when using the above with Gmail accounts. The original message ends up in the “[Gmail]/All Mail” folder. It's currently unclear why this happens and how to work around it.

## Revision 5310 (Tuesday, November 29, 2016)

The first item on the list below affected most users with SMTP/IMAP servers _not_ using standard ports like 25, 587, 143, and 993. Sorry about the inconvenience.

-   Fixed: Refactored server connection code in order to get around a recent issue with SMTP servers using non-standard ports.
-   Changed: The `mlmt` URI scheme now treats `+` as a space character in the query part.
-   Fixed: Issues with the new “Edit ▸ Add Link” menu item.
-   Fixed: Performance bug for the “Identity” and “Correspondent” specifiers available for address headers.

## Revision 5307 (Tuesday, November 22, 2016) — Version 1.9.6

The following includes all changes since the latest public release (r5263).

-   New: “Edit ▸ Add Link” menu item (⌘K). Inserts Markdown code to create a link based on the current word. Also inserts a URL if it's on the pasteboard.
-   New: URL scheme for doing toolbar-like searches: `mlmt:quicksearch?string=s%20mlmt`
-   New: “New Message With Attachment” and “Copy Attachment” in the context sensitive menu for an attachment.
-   New: `MmSMTPFixedHostname`
-   New: `MmCreateCIDURLForImageAttachments` can be used to disable the insertion of a `cid:` URL for images. Holding down ⌥ reverts the behavior whether or not this setting is enabled or disabled.
-   New: `MmWindowTitleFormatString`
-   New: Use `ignorePermanentFlags=1;` to ignore the `PERMANENTFLAGS`response for a specific server (for buggy servers). This is very experimental and did not fully solve the issues with the problematic server.
-   New: A `userDefaultsIdentifier` option for message lists/outlines. This can be used to get separate font settings when having multiple message lists in a layout.
-   New: `MmDisableThrottleDetection` (for debugging purposes)
-   New: Added `MmSOCKSProxyDisabled` in a simple attempt to work around an issue with proxy settings.
-   Changed: Generation of the HTML alternative for plain text (non-Markdown) messages is now handled using a dedicated script. For compatibility reasons this uses `whitespace:normal` and `<p>` instead of `<div>`. This should resolve various issues when corresponding with Outlook users.
-   Changed: The `insertText:` specifier works when the toolbar search field is focused. This can be used to make shortcuts to pre-fill the toolbar search filter: `"f" = ( "searchAllMessages:", "insertText:", "f " )`
-   Changed: Undoing move actions now re-selects messages if they exist in the current mailbox.
-   Changed: Show a tooltip for very long attachment names.
-   Changed: Now sanitizes headers before retrying an upload _if_ the server rejects an uploaded message. This is a quick workaround for a FastMail issue concerning badly formatted emails.
-   Changed: The compact header view format now indicates when a message has one or more non-identity recipients.
-   Changed: “Seen” IMAP keyword changed to “Seen (Read)” to make it a bit more obvious that it's the same thing.
-   Changed: Better at deriving a received date in unusual messages with no `Date`header and multiple `Return-Path` headers.
-   Changed: Workaround for buggy Sanebox emails. Now ignores non-text alternatives in a `multipart/alternative` if they have a `Content-ID`.
-   Changed: Workaround for wrongly formatted signed/encrypted emails (most likely caused by Exchange SMTP servers).
-   Changed: More gracefully handle an otherwise rare unresolved issue with missing message flags for messages to be uploaded.
-   Changed: Attempt to be a bit smarter when looking for Apple Mail accounts.
-   Changed: Don't crash when failing to convert text for a reopened draft.
-   Changed: The Cancel button is no longer the default button in the OAuth2 window.
-   Changed: Using the Boyer-Moore algorithm for some types of string search.
-   Changed: OAuth2 behavior changed a bit to work better when a password has been changed.
-   Changed: Improved sorting of the Source Mailbox column.
-   Changed: Now saves a draft if the user attempts to print it. Otherwise, the most recently saved version of the draft would be printed.
-   Changed: Improved parsing of `Message-ID` response from a `name.com` IMAP server (more gracefully handling a somewhat schizophrenic response).
-   Changed: Less greedy identification of subject prefixes. It's also configurable if needed, but this is undocumented for now.
-   Changed: Handle buggy `Content-Transfer-Encoding` headers which contain more than a single word (simply handled by ignoring anything but the first word).
-   Changed: Single click in the “Move to Mailbox” window no longer moves a message.
-   Changed: Minor improvement when `SMTP EHLO` fails with a timeout.
-   Changed: Using copy/paste with email headers now includes the colons.
-   Changed: Updated account importer to read the correct database file on Sierra.
-   Changed: The “List” format is now the default for the headers view.
-   Changed: Resizing the headers view some times resulted in parts of the headers view being hidden.
-   Changed: Improved sanitation of the (optional) email addresses setting used for signatures.
-   Changed: Added an icon to the Counters preferences pane.
-   Changed: Better debug output when timing out during an SSL handshake.
-   Changed: SMTP code slightly better at retrying before reporting an issue.
-   Changed: Always show link targets even if it matches the displayed string.
-   Changed: Display `multipart/related` subparts if they are not referenced by the main part _or_ if the main part is not `text/plain`. Works around various buggy email sending software.
-   Changed: Only skip inlining a stylesheet when it's not part of the HTML `<head>`. This should help handle some types of Outlook messages.
-   Changed: Some toolbar icon titles and tooltips.
-   Changed: Auto-display the accessory view (options) in the file panel shown when importing messages.
-   Changed: Mac OS X to macOS.
-   Fixed: Improved the use of tracking rects for thread arcs of large message threads.
-   Fixed: Various scrolling and font related issues. This should also make switching focus to the message list faster.
-   Fixed: Now trimming whitespace in front of bracketed email addresses. This could otherwise be a problem when creating replies.
-   Fixed: Distorted numbers now stay fixed when scrolling the message list.
-   Fixed: Increased column width such that emojis in the tags preferences pane are correctly displayed on Sierra.
-   Fixed: Related message parts were shown too often when emails were structured like this: `multipart/related { multipart/alternative { { text/plain text/html } image/png } }`.
-   Fixed: Issues indexing HTML message parts. In particular, `<table>`-based HTML.
-   Fixed: An issue with generating emails (replies or forwards) based on selected text.
-   Fixed: Handle the (apparently) non-standard Hebrew `iso-8859-8-i` encoding by treating it as `iso-8859-8`.
-   Fixed: Various text decoding issues.
-   Fixed: Saving a search as a smart mailbox frequently failed.
-   Fixed: Issue with text attachments for which only the last line is very long _and_ it has no newline character.
-   Fixed: Wrongly removed empty lines when displaying plain text emails or generating HTML for plain text emails.
-   Fixed: “Message ▸ Open in Apple Mail” failed for some types of incorrect `Message-ID` headers.
-   Fixed: Various issues with HTML embedding when forwarding HTML messages with attachments.
-   Fixed: “Edit as New Message” did not work correctly for inlined attachments.
-   Fixed: Crash bug related to handling drafts with multiple HTML embedded segments.
-   Fixed: Improved display of signed and/or encrypted HTML messages.
-   Fixed: Issue with the choice of Drafts mailbox (and implicitly SMTP server) when an identity could not be derived and an explicit one had not been configured.
-   Fixed: Issue with MailMate opening a new mailbox viewer when clicking on a notification (without holding down the command key).
-   Fixed: Bug in workaround for servers with no support for UIDPLUS when moving messages.
-   Fixed: For some servers, MailMate would try to setup encryption twice and this would fail.
-   Fixed: Shortcuts for the layout menu should now work more reliably.
-   Fixed: The initial state of the Preview toggle in the toolbar.
-   Fixed: Various issues related to toggling the preview in the Composer.
-   Fixed: The checkmark button for disabling an HTML signature did not work.
-   Fixed: Working around an issue with increasing connection timeout values.
-   Fixed: Account importer issue where the SMTP server gets an IMAP hostname.
-   Fixed: When using the “View ▸ Headers” menu, MailMate did not remember the most recently used format (which is used when viewing mailboxes with no explicitly chosen format).
-   Fixed: HTML code some times leaked into the headers view.
-   Fixed: Performance issue with displaying large HTML messages.
-   Fixed: Drag'n'drop emails to the Finder on Sierra.
-   Fixed: Visual glitch when using Find (⌘F).
-   Fixed: Workaround for some IMAP servers did not work well when multiple messages failed to be fetched at the same time.
-   Fixed: Infrequent crash when using the context sensitive menu in the messages outline.
-   Fixed: The junk toolbar button was not disabled when no messages were selected.

## Revision 5263 (Thursday, September 15, 2016) — Version 1.9.5

This is a major update even though the version bump is minor. The following is a list of all changes since the latest public release (1.9.4, March 15th).

-   New: Added “MailMate ▸ Registration ▸ Become a MailMate Patron…” menu item (only enabled for registered users).

There are numerous HTML/Markdown related changes. Most of the new options are documented in the Preferences documentation (“Help ▸ MailMate Help” menu item):

-   New: Options for embedding HTML when replying/forwarding (Composer preferences pane).
-   New: Option for a default HTML generation theme (Composer preferences pane).
-   New: Option for a signature related HTML generation theme (Signatures preferences pane).
-   New: Option for enabling math styling using ASCIIMath or TeXMath (Composer preferences pane).
-   New: Option for enabling code styling using Pygments (Composer preferences pane).
-   New: Added `MmDefaultCSS` for global css changes -- could be used for explicit fonts, but it's not recommended.
-   New: Markdown syntax can be used while MailMate still treats quoted text as plain text.
-   New: “Format ▸ Bold/Italic” menu items which inserts/removes Markdown syntax to emphasize text.
-   New: Updated default look of outgoing emails. Introduced alternative “Simple” theme to let users get the old style.
-   New: Setting to set a default display theme (Viewer preferences pane).
-   New: Added some default stylesheets for viewing/composing emails (they vary very little for now).
-   New: Setting to force MailMate to always generate HTML (useful if a theme always needs to be applied). This is disabled by default -- as it should be.

Other changes:

-   New: MailMate icon replaced (designed by Eli Schiff).
-   New: Toolbar icons (designed by Eli Schiff).
-   New: Support for tags and colored flags in the toolbar.
-   New: The (optional) Tags toolbar item can be configured to show multiple tag buttons.
-   New: Flag and Tags menus both in the main menu (Messages) and the context sensitive menu.
-   New: The old text-based toolbar is still available using this hidden preference: `defaults write com.freron.MailMate MmUseOldToolbar -bool YES`
-   New: Hidden preference named `MmToolbarFlagStrategy`. Possible values are `none` and `mru` (the latter is “most recently used” and is the default).
-   New: Composer preferences to control what is used to complete email addresses.
-   New: Network code now uses CFNetwork instead of OpenSSL. This implicitly means proxy support (System Preferences), IPv6 support, and TLS 1.2 support.
-   New: Redesigned headers view (using a WebView now).
-   New: GUI setting to control when the Composer preview is shown. Options are “Always”, “when generating HTML”, and “never”.
-   New: Context sensitive menu for addresses in the recipient fields of the Composer.
-   New: Menu items to explicitly apply SpamSieve to the selected messages (see the “Message > Junk State” menu).
-   New: Hidden preference `MmNeverInlineAttachments`
-   New: Identities now support `retiredAddressPattern` which can be used to tell MailMate to recognize addresses without ever using them for From/To headers.
-   New: Key bindings `selectPreviousCountedMailbox:`/`selectNextCountedMailbox:` which can be used to skip to the next, e.g., unread mailbox.
-   New: Added `centerSelectionInVisibleArea:` for the mailbox/message lists (bound to ⌃L by default).
-   New: Preview toolbar button in the Composer.
-   New: LDAP code now supports the `searchFilter` option.
-   New: `MmSourcesAboveMailboxes` (stop-gap temporary solution for users wanting sources above mailboxes).
-   New: Added `MmFollowUpBasedOnAddressOnly` (when checking for follup messages then MailMate ignores differences in the sender name).
-   Changed: Now showing an error window (instead of crashing) when failing to set attributes on a file.
-   Changed: By default, no longer allowing cross message `CID:` urls.
-   Changed: Quickly reduces fetching to a single message per request when fetching a set of emails fails.
-   Changed: Default toolbar items (also added more toolbar items).
-   Changed: Logs the SSL/TLS protocol used for all connections (CFNetwork).
-   Changed: New default look of inlined code segments.
-   Changed: Improved VoiceOver behavior for the header text fields in the Composer.
-   Changed: Date headers now also allow the use of “exists”/“does not exist”. This is useful for the virtual “Date-Last-Viewed” header.
-   Changed: Attempt to, more gracefully, handle Google IMAP throttling.
-   Changed: Display themes force a sans-serif font to work around an issue with an ugly default font setting with Outlook (and maybe other email clients).
-   Changed: Various Markdown related settings removed. Few of them make sense when quoted text can be skipped when doing the Markdown conversion.
-   Changed: Updated the included version of `html2text`.
-   Changed: If a `multipart` or `message` subpart has an unknown encoding then it is now assumed to be 7bit (workaround for some buggy emails).
-   Changed: No longer fetching headers before the bodies of messages. This was error prone and inefficent. It also fixes some issues with smart mailboxes and searches involving message bodies.
-   Changed: An error is now reported by MailMate if using an email address with a non-ASCII username with an SMTP server not supporting SMTPUTF8.
-   Changed: Disabled flowing very long words (1000 characters) for `format=flowed`. Instead this relies on the use of quoted printable.
-   Changed: Styles are scoped although that works in almost no email clients -- including MailMate (`<style scoped>`).
-   Changed: Behavior when handling quoted signature separators in `format=flowed`. Additional prefixed spaces are now allowed.
-   Changed: Redesigned how scripts are used for text conversions. Introduced `eventFilters`. Moved default scripts to embedded bundle. (Work in progress.)
-   Changed: Default counter colors updated (dock and menu).
-   Changed: Changed message redirection loop limit to 5 instead of 1.
-   Changed: The date header parser is now better at handling weird orderings of date elements.
-   Changed: The flags column can sort colored flags.
-   Changed: Now clearing cookies when doing OAuth2 to make it less likely that the wrong account is used for authentication.
-   Changed: It's possible to bind the wrong Gmail credentials to a Gmail account when using OAuth2. This and any similar issues now results in MailMate asking to re-authenticate the account.
-   Changed: When getting a new access token (when OAuth2 authentication fails) and it's identical to the old one then try getting a new refresh token instead. This is an attempt to work around a Gmail issue.
-   Changed: Auto-disable HTML signature alternative if the text field is essentially empty.
-   Changed: When completing email addresses in the composer then don't suggest addresses already in the header.
-   Changed: Added `image-orientation: from-image;` to the default stylesheet even though it doesn't currently work for Webkit.
-   Changed: Copying names and addresses in the headers view no longer includes double quotes.
-   Changed: Refactored “OAuth2” code such that re-authentication should only happen when new access tokens repeatedly fail to work.
-   Changed: Fetching access tokens now happens on a separate thread. This might make MailMate a bit more responsive for some users.
-   Changed: `MmDefaultCSS` is now appended instead of prepended to the stylesheet.
-   Fixed: Various issues with macOS 10.12 (Sierra).
-   Fixed: Some times after sleep mode and/or being offline, MailMate failed to send all pending messages in Drafts (until relaunching MailMate).
-   Fixed: Very old issue handling non-unique `cid:` URLs.
-   Fixed: Weird and persistent issue with toolbar icons being 1 pixel off (vertically) on Retina displays.
-   Fixed: Various issues compiling with the 10.11 SDK.
-   Fixed: Some inefficiencies when fetching emails, in particular, if some emails fail to be fetched.
-   Fixed: The composer preview buttons now reflect the current state.
-   Fixed: Various issues using “Find” in the message view. Now also uses third party code to highlight all matches.
-   Fixed: No longer opens tags editor when no messages are selected or a message is not visible.
-   Fixed: More gracefully handling if MailMate somehow gets into a state where some messages exist in non-existing IMAP mailboxes.
-   Fixed: OAuth2 issue for Gmail accounts in the account importer.
-   Fixed: Issues with replying/forwarding some types of HTML-only messages, e.g., created by Outlook.
-   Fixed: Various issues with auto-detection of IMAP/SMTP ports.
-   Fixed: Various issues with header lines containing multiple non-sequential encoded words.
-   Fixed: Headers with a large number of values are now capped at 10 and showing a link which can expand it.
-   Fixed: To/Cc/Bcc buttons in the address panel reintroduced.
-   Fixed: Address pattern can now only be edited when it's enabled (IMAP account settings).
-   Fixed: Race condition when updating an access token for OAuth2.
-   Fixed: Reencode emails with nil characters (but only if the IMAP server rejects the message).
-   Fixed: Pasting email addresses separated by return characters now works as one would expect (pasting Excel data triggers this issue).
-   Fixed: Toolbar search works (again) in the Statistics layout.
-   Fixed: “Edit Subscriptions” is now able to setup an OAuth2 token.
-   Fixed: Resizing issue with the path control.
-   Fixed: An issue triggered by Xcode on 10.9 and earlier. Various side-effects including no window opened on startup.
-   Fixed: Various issues with certificate/password verification.
-   Fixed: Editing a draft with a modified Bcc header did not work well when using `MmDefaultBccHeader`.
-   Fixed: Some times connection failures would unnecessarily trigger MailMate to ask for OAuth2 re-authentication.
-   Fixed: Pasting a set of email addresses in the composer could fail if newlines were involved.
-   Fixed: Various (minor) memory leaks.
-   Fixed: Crash related to signature handling in the Composer preview.
-   Fixed: The Share extension now handles links by putting them in the body of the new message.

## Revision 5234 (Tuesday, March 15, 2016) — Version 1.9.4

This public release includes a lot of small improvements and bug fixes. The most interesting changes are various new hidden preferences, including `MmSMTPAlternativeEnabled` and `MmSMTPUTF8Enabled`. More information in the manual and in the release notes for the beta releases provided further below.

Additional changes after the latest beta release:

-   Changed: Experimental workaround for Exchange IMAP bug.
-   Fixed: The link displayed in the message view (when hovering over a link) was not always correct.

## Revision 5232 (Thursday, March 10, 2016) — Version 1.9.4 Beta 3

The following are all changes since the latest beta release (r5226, February 20th).

-   New: Hidden preference `MmSortRecipientHeaders` which enables automatic alphabetical sorting of recipient headers in the Composer.
-   New: The `refreshMailbox:` key binding which can, e.g., be used to “remove” read emails from the Unread mailbox without switching mailboxes.
-   Changed: Handling of dummy messages improved. (Dummy messages are used to work around various IMAP server issues and any local issues with disappearing files, e.g., caused by antivirus software.)
-   Changed: Offline accounts are now listed using a red color to make them stand out. This should make it easier to spot if MailMate takes an account offline (which is not supposed to happen without warning the user).
-   Changed: Arrow in correspondence column is a bit more discreet.
-   Changed: Double-clicking entries in the address book panel now adds items to the focused header in the composer.
-   Changed: An extra safety catch to never upload dummy messages.
-   Changed: Slightly better at _not_ ignoring commented email addresses in email recipient headers.
-   Fixed: Issue with Gmail accounts some times going offline when authentication fails.
-   Fixed: Improved detection of mismatching HTML links in message viewer.
-   Fixed: Export action (rules) did not work with the default Downloads folder.
-   Fixed: Issue with sorting descriptor in messages list.
-   Fixed: Some MailMate related URLs were not changed from `http:` to `https:`.

A hidden preference has been introduced for BusyContacts users. It affects the behavior of the “Show” and “Add” menu items for email addresses in the headers view.

```
defaults write com.freron.MailMate MmDefaultAddressBook -string com.busymac.busycontacts
```

## Revision 5226 (Saturday, February 20, 2016) — Version 1.9.4 Beta 2

The following are all changes since the latest beta release (r5213, February 2nd).

-   New: First complete shot at supporting `SMTPUTF8`. It is enabled using `MmSMTPUTF8Enabled`, but this is highly experimental. Don't enable it if you don't know what you are doing. Review your outgoing messages (⌥⌘U) and make sure both server and recipients can handle it.
-   New: Hidden preference to disable UID MOVE if needed (`MmNeverUseIMAPMOVE`).
-   Changed: Using Quick Look on a specific attachment now (again) makes the other attachments available via the arrow keys.
-   Changed: Additional sanity check of the default selected range (caret location) when replying/forwarding.
-   Changed: Changed all uses of `http:` to `https:` now that `freron.com` and `mailmate-app.com` supports it (thanks to “letsencrypt”).
-   Changed: UID MOVE disabled for `imap.yandex.ru` which has a buggy implementation of this IMAP feature.
-   Changed: Various performance improvements.
-   Changed: Changed handling of external scripts in an attempt to avoid some delays.
-   Changed: Added `selectWithFormatString:` as an alias for `selectWithFilter:`.
-   Changed: Copyright lines updated to 2016.
-   Fixed: Some issues related to misplacing the caret when replying/forwarding.
-   Fixed: Issue handling multiple spaces after quote marks when deflowing (`format=flowed`).
-   Fixed: When puny-coding domain names MailMate used the unencoded addresses when talking to the SMTP server.
-   Fixed: Crash bug in latest beta release when using encryption with OpenPGP.
-   Fixed: Crash bug in latest beta release when no identities can be found.
-   Fixed: Issue related to (El Capitan) account import bug in r5187.
-   Fixed: `MmShowAttachmentsFirst` did not work well for attached messages.

## Revision 5213 (Monday, February 1, 2016) — Version 1.9.4 Beta 1

The following are all changes since the latest public release (r5187, November 26th).

-   New: Attached emails can now be detached with the “Detach Message” menu item in the context sensitive menu. It is saved in the same IMAP mailbox with the same IMAP keywords. It is selected if it's in the currently displayed mailbox.
-   New: Different and less intrusive type of tooltips (only enabled when experimental 2.0 features are enabled in the General preferences pane).
-   New: Heuristically altering the wait on responses from IMAP IDLE. Shorter wait if the connection is often lost.
-   New: Bundle commands now support a `conditions` key which can be used to specify which messages are relevant for a given command. This is useful for commands like those available on ⌃O (Open in Browser).
-   New: Created simple Trac bundle for opening an issue in a browser (⌃O).
-   New: Smart mailbox conditions and rule conditions now take a default value from the most recently selected email in the mailbox.
-   New: Extended toolbar search to allow `A` (capital a) to search attachment filenames. It searches “Content-Type ▸ Name” and “Content-Disposition ▸ Filename”.
-   New: Added “Filename” to the initial set of headers available in “Edit ▸ Find ▸ Mailbox Search”.
-   New: Hidden preference to enable an experimental popup to select an alternative SMTP server in the Composer (`MmSMTPAlternativeEnabled`).
-   New: Signatures preferences now has an option to insert newlines when caret is at top combined with signature at bottom.
-   New: Attempt to handle side effects of antivirus software more gracefully (when it removes MailMate database files).
-   New: Spotlight importer now also generates a value for `com_apple_mail_dateReceived`.
-   New: Stop-gap solution for users wanting attachments to be displayed first in the message view: `MmShowAttachmentsFirst`.
-   New: IMAP/SMTP settings now allow you to force a specific authentication method if needed (e.g., `authMechanism = "PLAIN";`).
-   New: The `Security.plist` file now supports S/MIME and empty values to disable signing/encryption for specific email addresses.
-   Changed: Default toolbar search (and “Common Headers and Body”) includes searching attachment filenames.
-   Changed: The Lighthouse and Github bundles use the new `conditions` key (⌃O).
-   Changed: Respect `personal-digest-preferences` for OpenPGP (`.gnupg/gpg.conf`).
-   Changed: Hash function for OpenPGP signing now defaults to `sha256` instead of `sha1` if the user has no preference.
-   Changed: The green, red, and yellow frames used for signed/encrypted body parts are now styled via the default stylesheet (instead of being hardcoded).
-   Changed: Processing rules of a mailbox now stops if the message is no longer in the mailbox (due to an action of an earlier rule).
-   Changed: Added `MmMessagesOutlineVerticalDragSelects` (hidden preferences in the manual).
-   Changed: Clarified the use of empty values in `Security.plist` (hidden preferences in the manual).
-   Changed: Added some details about Spotlight in the manual.
-   Changed: Added some details about tags in the manual.
-   Changed: Added help anchor in the General preferences pane (to section about Spotlight in the manual).
-   Changed: Hardcoded the default use of port 993 for Gmail (for some reason Gmail does not allow port 143).
-   Changed: Workaround for email recipients with `<` in a non-quoted display name (caused by a sender email client bug).
-   Changed: Faster skipping of date parsing in “Received” headers after a received date has been found/parsed.
-   Changed: No longer crashes if a disk cached attachment cannot be deleted, e.g., if the file is locked.
-   Changed: Cleaning up user ids provided via `Security.plist` (OpenPGP).
-   Changed: Now auto-watching for changes to key binding files.
-   Changed: Added some extra checks to make sure that messages with signing/encryption issues cannot be sent.
-   Changed: “Quick Look” now defaults to displaying the first non-inlined attachment. This should help skip, e.g., signature images. “Quick Look” now also skips past attachments within `multipart/related`.
-   Changed: Some commands with no input now behave as if in `noMessages` mode.
-   Changed: Slightly better at using the HTML body part when generating a plain text reply when the plain text body part is empty.
-   Changed: Refactored handling of attachments. In particular, `message/rfc822`attachments are now re-encoded if they wrongly contain very long lines.
-   Changed: iCloud icon shown for iCloud accounts using `imap.mail.me.com`.
-   Changed: Workaround for Exchange issue likely triggered by messages with very long lines.
-   Changed: Workaround to handle (non-standard) circled numbers in Japanese encodings.
-   Changed: Workaround for IMAP server issue with an erroneous UID COPY response.
-   Fixed: Infinite loop issue triggered by a local change to the `\Recent` flag of a message.
-   Fixed: Quick Look on a single attachment now only shows that attachment (and never the wrong one).
-   Fixed: Never show `multipart/*` body parts as attachments.
-   Fixed: The wrong account was used if creating a follow up message to a message which had been moved to a different account.
-   Fixed: Database issue which (among many other things) could affect the handling of the “Tagged” smart mailbox and its children when changing tags.
-   Fixed: Changes to IMAP keywords did not work well for servers with support for `UID MOVE`. In particular, moving in/out of the Junk mailbox did not work well.
-   Fixed: El Capitan email account importer did not work correctly for SMTP for some types of accounts (including Gmail).
-   Fixed: Crash bug in Spotlight importer (related to certain types of Japanese messages).
-   Fixed: GUI glitch in the Tips view.
-   Fixed: Disabled the buggy (and old) experimental `MmIMAPWindowInDays` hidden preference.
-   Fixed: The key binding selector `moveToJunk:` is no longer a toggle since the name was counter-intuitive.
-   Fixed: The “Save to ...” menu item for attachments did not correctly show the configured default downloads folder.
-   Fixed: Re-editing a saved draft would some times reset manual changes to the signing/encryption settings of the message.
-   Fixed: The “Empty Mailbox” menu item did not work if account submailboxes were not enabled for a universal mailbox.
-   Fixed: Exporting a body part now uses its filename if one is available.
-   Fixed: The “Export” bundle did not work correctly when the destination mailbox does not exist.
-   Fixed: Various issues with selection of messages when moving messages which are not located in the same IMAP mailbox.
-   Fixed: The “Downloads” folder preference in the General preferences pane was broken.
-   Fixed: “Mark All Messages as Read” did not work when selecting multiple mailboxes.
-   Fixed: Issue using control characters in signatures (fixed by saving signatures in XML plist format).
-   Fixed: Renaming an account in the IMAP account editor did not update the mailbox outlines correctly.
-   Fixed: The “use existing draft” feature now ignores any messages in the Drafts folder not marked as drafts.
-   Fixed: Problem completing names when matching, e.g., o with ø.
-   Fixed: Increased width of emoji column in the Tags preferences pane (needed for El Capitan).
-   Fixed: Various issues regarding scrolling behavior and selected items in the messages outline.
-   Fixed: Issue affecting how “Send Later” messages were handled after sleep mode.

## Revision 5187 (Thursday, November 26, 2015) — Version 1.9.3

This public release is mainly focused on bug fixes and stability issues. The most notable new features are manual ordering of IMAP accounts/mailboxes and OAuth2 support for Gmail and Outlook accounts. Note that OAuth2 is enabled by default. **If you have any issues then please report them and note that you can disable OAuth2 in the IMAP account settings.**

See below for all the changes since the latest public release (r5141, September 29).

## Revision 5184 (Monday, November 23, 2015) — Version 1.9.3 Beta 3

These are all changes since beta 2 (r5180).

-   New: IMAP mailboxes can now be reordered manually.
-   New: Hidden preference `MmForwardingDeriveIdentityFromRecipient`. (Enabled by default.)
-   Changed: MailMate now handles non-empty multiparts with no subparts more gracefully (by displaying the body as if it was plain text).
-   Changed: The “Load Once” button is now always in the same location.
-   Fixed: Smart mailboxes would not stick if placed at the top of a mailbox with autogenerated submailboxes.
-   Fixed: Stability issue with OpenPGP.
-   Fixed: IMAP mailboxes were no longer sorted by default.

## Revision 5180 (Thursday, November 19, 2015) — Version 1.9.3 Beta 2

The following are all changes since the latest beta (r5164). The previous beta had a bug for Gmail which could result in some mailboxes not being synchronized until after MailMate was relaunched. An older issue has also been fixed: Scripts (and MailMate) could hang on El Capitan, for example, when displaying plain text emails.

-   New: Sources (accounts) are reorderable. The order is also used for any mailboxes configured to show account submailboxes.
-   New: Hidden preference to replace “Reply” with “Delete” in notifications: `MmNotificationDeleteButtonEnabled`
-   Fixed: Different approach to running external scripts fixed an issue on El Capitan with hanging scripts.
-   Fixed: Account name changes now dynamically propagate to all related mailboxes.
-   Fixed: OAuth2 bug which resulted in only the INBOX being synchronized after some time (expiration of access token).
-   Fixed: Limit size of error message when reporting an SMTP issue with failed recipients.
-   Fixed: Using `from` in `mailto:` URLs did not quite work as documented in the manual.
-   Fixed: Added to manual that ⌘C can be used get the UUID of a mailbox.
-   Fixed: Make table view headers look right on OS X releases before El Capitan.
-   Fixed: Crash bug in the code for handling the (deprecated) `x-uudecode` content transfer encoding method.
-   Fixed: Issue triggered by updating Boost to version 1.59.
-   Changed: Reverted back to using Boost 1.58. A workaround for a bug in Boost 1.59 turns out to be too slow in some cases.

## Revision 5164 (Tuesday, November 3, 2015) — Version 1.9.3 Beta 1

MailMate now supports the use of OAuth2 to authenicate Gmail and Outlook accounts (more precisely, it's XOAUTH2 for IMAP/SMTP). It is enabled by default and it affects existing Gmail/Outlook accounts. If you have any issues then you can edit the IMAP account settings and explicitly disable the use of OAuth2. Don't forget to report any issues.

Other changes and fixes since the latest public release (r5141):

-   New: A button to “Reset Fonts” in the General preferences pane.
-   New: “New Message to Recipients/Senders/Correspondents” commands available in the MailMate bundle.
-   Changed: Opens a browser instead of searching for similar messages when a URL is present in the headers view (the subject line).
-   Changed: Changed import hack to be able to import Apple Mail account settings on El Capitan.
-   Changed: Small change for servers wrongly configured to use port 587 with SSL (instead of STARTTLS).
-   Changed: The “Date Sent” value falls back to the received date if the message has no “Date” header.
-   Changed: Completion of email addresses no longer require matching accents (still required for Contacts though).
-   Changed: Improved handling of partial (subset of messages) IMAP upload failures. This should generate fewer/no duplicates when something fails.
-   Changed: Generating IMAP dummy messages less frequently.
-   Fixed: The Share extension can now handle `public.image`.
-   Fixed: Various issues with “dummy” messages (dummy messages are used to replace emails which cannot be fetched).
-   Fixed: A problem signing some emails with message/rfc822 attachment(s).
-   Fixed: Issue with “Default Downloads Folder” popup in the General preferences pane.
-   Fixed: Non-IDLE-capable server not handled well if the connection was cut before the timeout was reached.
-   Fixed: The Composer updated the edited message to be previewed even if there was no preview open.
-   Fixed: For some IMAP accounts MailMate could create, e.g., `mail/INBOX` if `mail` was configured as the namespace of the account.
-   Fixed: Handle missing response prefix (`* OK`) gracefully after a UID MOVE (Exchange 2016 bug).
-   Fixed: Handle unexpected `BODY[]` response gracefully (when asking for message headers).
-   Fixed: Handle missing INTERNALDATE after IMAP MOVE on non-UIDPLUS servers.
-   Fixed: Issue with missing markdown value in the `Content-Type` header.
-   Fixed: Some times renaming a mailbox resulted in two mailboxes (old and new name).
-   Fixed: Problem with spinning wheel in subscriptions editor.
-   Fixed: Disabled automatic generation of a debug log file on the Desktop.
-   Fixed: Replying to a `multipart/alternative { text/html }` message improved.
-   Fixed: Issue with an address header containing a nil character.
-   Fixed: When wrapping quoted lines in the Composer, MailMate now counts unicode characters instead of bytes. This works much better (visually) for, e.g., Russian.
-   Fixed: Export bundle did not work on El Capitan because `formail` is no longer a part of OS X.
-   Fixed: Various problems with emails with more than 30 recipients.
-   Fixed: Various issues fixed for the `createMessage` action type.
-   Fixed: No longer crashing when using “Bcc” with S/MIME encryption (an error message is generated instead).
-   Fixed: Very long attachment names could prevent the user from removing them via the attachments menu in the Composer.
-   Fixed: Various issues with caret placement (selected range) in the Composer.
-   Fixed: Switching back to “derive from context” did not work in the Composer preferences pane.

## Revision 5141 (Tuesday, September 29, 2015) — Version 1.9.2

This public release is the first release compatible with El Capitan. An especially noteworthy new feature is the inclusion of a Spotlight importer. This can be enabled in the General preferences pane and it'll allow users to search MailMate emails using Spotlight. It'll also allow searching email files saved elsewhere. The Spotlight support also means better integration with BusyCal thanks to the nice people at BusyMac.

MailMate now also includes a “Share” extension which should provide better integration with various other applications.

See below for all the changes since the latest public release (r5084, April 2).

## Revision 5140 (Tuesday, September 29, 2015) — Version 1.9.2 Beta 2

These are all the changes since the latest beta release (r5107, July 13).

-   New: The `replyMessage` action now supports a `subpart` parameter to specify an explicit subpart to be used for the reply.
-   New: A subpart can be specified for the `replyMessage` action.
-   New: An explicit `From` header can be specified for the `replyMessage` action.
-   New: A `sendMessage` action is available to bundle commands.
-   New: Export bundle added. It uses `formail` to provide a command to generate mbox files.
-   New: Optional “Attach” button for the Composer toolbar.
-   New: Hold down shift in the “Go to Mailbox” interface in order to open a new mailbox viewer.
-   New: Attempt to handle some IMAP issues by injecting a dummy message to replace what cannot be fetched. The goal is to make it easier to debug a certain group of IMAP server issues. Dummy messages include 10 lines of the connection log.
-   New: Hidden preference `MmCounterMaximumNumberOfMenuItems`.
-   New: Experimental preference (`MmSentMailbox`) to point the universal “Sent Messages” mailbox to any (smart) mailbox.
-   New: Experimental preference (`MmTNEFSaveBodies`) tells the `winmail.dat`code to also make the main text body appear as an attachment.
-   New: Added support for the IMAP MOVE extension (when available).
-   Changed: By default, “[Gmail]/All Mail” is now kept in the IDLE state.
-   Changed: The IMAP keyword of a new tag is only automatically updated when initially entering a display name in the Tags preferences pane.
-   Changed: Changing a Gmail label in the Tags preferences pane triggers the list of mailboxes in Gmail accounts to be resynchronized.
-   Changed: When a mapped Gmail label is added/removed server-side then MailMate updates the corresponding IMAP keywords. This helps keep tags and Gmail labels in sync.
-   Changed: The wording of some types of OpenPGP warnings.
-   Changed: Increased timeout for IMAP `APPEND`, `COPY` and `STORE`.
-   Changed: Emails pending to be sent, but not yet in the process of being sent can now be cancelled.
-   Changed: It's now (again) possible to alter the background color of the Composer (`MmMessageTextView/display.plist`).
-   Changed: Passwords are saved in a slightly differently way to the keychain. This should result in fewer “duplicates” entries.
-   Changed: Decrypt/verify can handle various badly formed signed/encrypted messages with “rogue” elements.
-   Changed: Always handle port 465 as an SSL port (and not TLS) since this is almost always the case. It can be forced to use STARTTLS by suffixing a `p` to the port number (`p` for plain text).
-   Changed: Fixed some issues with background/indent of code segments.
-   Changed: Debug variable to learn more about certificate issue with iCloud IMAP: `MmDebugCertificates`.
-   Changed: Removed the use of Growl for notifications. Unfortunately this means notifications only work on 10.8+. For now, it's possible to hover over a notification banner to click on a “Reply” button.
-   Changed: Changed “Run Script” to “Run Command” in the Rules editor since this is exactly what the rule action can do.
-   Changed: Some changes to the Spotlight indexing feature including using `com.freron.MailMate/Messages` for the custom location of messages.
-   Changed: Improved behavior for a certain type of IMAP errors, e.g., when moving/adding a large numbers of messages. This should prevent an otherwise persistent error message.
-   Changed: Utilized an undocumented feature of `libiconv` which allows a callback function to handle invalid bytes.
-   Changed: Use blank instead of “Unknown” as default user name when importing accounts.
-   Changed: TNEF code now checks for `win.*.dat` files instead of just `winmail.dat`.
-   Changed: Hitting `;` behaves like hitting `,` in the address headers of the composer. This is just a convenience feature for users with bad habits.
-   Changed: Various updates to the manual -- in particular, hidden preferences.
-   Changed: Port 465 is now again handled automatically with respect to SSL vs TLS.
-   Changed: Always use `iso-2022-jp-3` when `iso-2022-jp` is specified.
-   Fixed: Issue with S/MIME messages using `x-pkcs7-signature` as subtype.
-   Fixed: Issues with verifying various OpenPGP emails. In particular those using the classic email signature separator (two dashes).
-   Fixed: Deriving attachment name based on subject for a `.eml` file did not work well for long UTF8 strings.
-   Fixed: Google has fixed Gmail IMAP such that it can now eport IMAP keyword changes when IDLE. This is also triggered when a Gmail label changes, but the label changes are not automatically reported. Instead MailMate has to explicitly ask for the Gmail labels.
-   Fixed: Enabled sorting for the Bundles preferences pane.
-   Fixed: Replying to certain types of malformed signed/encrypted messages works better now.
-   Fixed: When permanently deleting a currently displayed message then its external resources could be fetched.
-   Fixed: Calendar attachments could not always be seen via Quick Look (⌘Y).
-   Fixed: Context sensitive menu did not work in the composer for an empty message.
-   Fixed: Issue with escaping Markdown symbols too often in drafts.
-   Fixed: More gracefully handle failed code styling or math styling.
-   Fixed: Improved inline styling to get rid of style-section and replace `body` tag with `div` instead of stripping it.
-   Fixed: Changing port settings did not clear the cached “most recently used” port.
-   Fixed: Extraneous whitespace is removed when using the default “Copy” action in the headers view context sensitive menu.
-   Fixed: Distortion mode now also distorts numbers (replaces with random numbers of the same length).
-   Fixed: Improved behavior for email addresses containing comma or @ in the name part.
-   Fixed: Changed defaultTimeZone to localTimeZone. This should make moving between time zones work better.
-   Fixed: Dragging an email within MailMate to a composer window now attaches it instead of inserting a `message:` URL.
-   Fixed: The “Last Viewed” column did not work correctly.
-   Fixed: “Apply Rules” was always disabled for children of universal mailboxes.
-   Fixed: The automatic decoding of `winmail.dat` files has been broken for some time.
-   Fixed: Some times removing a label on Gmail failed (when mapping a tag to a Gmail label).
-   Fixed: Minor issues on El Capitan.
-   Fixed: Problem with accounts configured to use at most 1 connection (a hidden setting).
-   Fixed: The displayed mailbox count is used for VoiceOver in the mailbox outline.
-   Fixed: A potential issue with `winmail.dat` support triggered if MailMate was installed in a location with spaces in the path.
-   Fixed: Moving mailboxes in the mailbox outline could fail under certain circumstances.
-   Fixed: Crash when editing a non-existing IMAP mailbox (an account-relative child of a universal/standard mailbox).
-   Fixed: Duplicating a mailbox did not copy the display count setting.
-   Fixed: Display counts failed for “Show Accounts” submailboxes after duplicating a mailbox.
-   Fixed: MailMate is now able to tell an IMAP server to delete a non-selectable empty IMAP mailbox.
-   Fixed: Issue with the font of the State column in the Drafts folder.
-   Fixed: The mailbox choosers should now handle unicode properly when ranking.
-   Fixed: Potential crash (race condition) when moving emails in a Gmail account.
-   Fixed: Plain text forwarding is now better at including attachments for certain types of messages, e.g., those with `multipart/mixed` within `multipart/alternative`.
-   Fixed: Moves between 2 IDLE (Connected) mailboxes were not synchronized immediately.
-   Fixed: Removed incorrect database corruption warning related to sorting by UID.

Note: The support for IMAP MOVE has been tested with Gmail and FastMail. For some servers this is more efficient and it might not trigger quota issues which would be triggered by COPY+EXPUNGE. It is also likely that this fixes a whole range of possible issues with Gmail since Gmail does not work well with the standard COPY+EXPUNGE method.

## Revision 5107 (Monday, July 13, 2015) — Version 1.9.2 Beta 1

This is the first beta of MailMate which should work on El Capitan. The following are all changes since the latest public release (r5084):

-   New: Spotlight importer in the application bundle (enables the OS and other applications to search MailMate emails).
-   New: GUI settings to enable/disable the Spotlight integration (see the General preferences pane).
-   New: Application extension for MailMate to appear in the Share menu of other applications. (I'd like this to work without showing a sheet like Apple Mail, but this is not possible for third party applications.)
-   New: An `mlmt` URL scheme has been introduced to implement the Share extension.
-   New: Virtual header transformation to put a date in its local time zone. Useful for configuring Submailboxes based on, e.g., “Date >> Local > Day”.
-   New: Toolbar search allows `T` to match on tags and `K` to match on raw IMAP keywords.
-   New: Toolbar search field supports `a` to search values in any address header (from/to/cc/bcc).
-   New: Toolbar search field supports `!` to negate comparisons. For example, `f !freron` means “From does not contain 'freron'”.
-   New: “Edit ▸ Paste as Quoted Text” (⌥⌘V) (`pasteAsQuotedText:`).
-   New: First shot at handling international domain names (IDN) -- currently only works for from/to/cc/bcc.
-   New: A server connection is now always reserved for the INBOX. This should, in particular, improve the user experience when initially synchronizing accounts.
-   New: Added `emptyMailbox:` key binding to the manual.
-   New: Hidden preference `MmEmptyMailboxMenuItemEnabled` which enables “Empty Mailbox” for all types of mailboxes.
-   New: Hidden preference `MmMessageWindowActionAfterMove`. Given the value `closeWindow` the single message window is closed after, e.g., archiving.
-   New: Hidden preference `MmComposerInitialFocus` to control composer focus. (Use `alwaysTextView` to put default focus in the main text view.)
-   New: Hidden preference `MmMessagesOutlineMoveStrategy` has a new `"none"` option.
-   Changed: Vertical drag in messages outline no longer selects (hidden preference to revert this change: `MmMessagesOutlineVerticalDragSelects`).
-   Changed: Some optimizations to make initialization of the “Tagged” smart mailbox (and related queries) faster.
-   Changed: Improved handling of HTML redirects to make sure they are completely ignored (previously they could blank out the message view even if image blocking was enabled).
-   Changed: Children of universal mailboxes are now editable -- the editor for the corresponding IMAP mailbox is shown.
-   Changed: The selected mailbox and/or message is now prioritized when synchronizing an IMAP account.
-   Changed: Improved behavior for a large number of accounts (more than 50).
-   Changed: The “Reply” toolbar button respects the default reply behavior -- also when it's “Reply All”. Added a “Reply Sender” button.
-   Changed: Gmail key bindings for `U` and `I` are now more like the web interface.
-   Changed: Improved canonicalization of mailbox names when using “Go/Move to Mailbox” such that, for example, `o` matches `ó`.
-   Changed: Now handling `.eml` files by temporarily importing them. They are then displayed while also allowing them to be forwarded/replied.
-   Changed: Mailbox editor uses the full mailbox name in the window title.
-   Changed: Various optimizations of specifiers done as part of implementing the Spotlight Importer.
-   Changed: Some improvements for accessibility.
-   Changed: Disabled “Bottom/Top” options in the signature menu when no signature is selected.
-   Changed: Gmail key bindings default to using the toolbar search field for `/`.
-   Changed: “Select All” in the mailboxes outline is forwarded to the messages outline.
-   Changed: Now forwarding as text even if `multipart/related` exists in the forwarded email.
-   Changed: Increased minimum width for thread arcs. Partly solves a problem for mousing over dots.
-   Changed: Never terminate when failing to delete a folder on disk.
-   Changed: Sorting key for Tags (emojis).
-   Fixed: Sudden termination after editing a signature (El Capitan).
-   Fixed: The redirect rule action could result in the database corruption window being shown (no real corruption though).
-   Fixed: Disabled old workaround which unfortunately made MailMate very slow when clicking links in the headers view.
-   Fixed: The SMTP code wrongly used “From” instead of “Resent-From” for redirected emails.
-   Fixed: IMAP mailbox settings are no longer lost if rebuilding the database from server (or when enabling/disabling a server namespace).
-   Fixed: Some rare crashes related to the composer. They were triggered when quickly sending after editing.
-   Fixed: Crash on exit related to having a large number of accounts.
-   Fixed: Previous/next message in single message window updates the window title.
-   Fixed: The default fixed width font for the Composer is no longer hardcoded.
-   Fixed: Now using the correct menu bar font on Yosemite+.
-   Fixed: Reordered arguments to `gpg2` (OpenPGP) in order to always have options before the command.
-   Fixed: Various issues with “Edit ▸ Substitutions” (including some missing menu items).
-   Fixed: Crash on launch bug related to font settings for the messages/mailbox lists (El Capitan).
-   Fixed: Message outline header images were not displayed (El Capitan).
-   Fixed: Too many reachability checks for unreachable servers (El Capitan).
-   Fixed: Smart mailboxes using the “is not in” condition did not work correctly when new messages arrived.
-   Fixed: Improved behavior when reverting to default columns when a parent mailbox has specific settings.
-   Fixed: Some badly formatted emails couldn't be imported. MailMate is now a bit less strict with `.eml` files.
-   Fixed: The “does not contain” comparison method did not work correctly for body text.
-   Fixed: Some toolbar search titles included implementation details, e.g., “Recipient ▸ Split”.
-   Fixed: Crash bug when trying to attach a folder and one or more files.
-   Fixed: Better handling of `!` in URLs.
-   Fixed: Crash bug for users with a very large number of accounts.
-   Fixed: Bolded messages (unread) were not always immediately updated when read state changed.
-   Fixed: A single-key key-binding could override an otherwise higher priority multi-key custom key binding.
-   Fixed: Do not disable a mailbox in a popup menu if it has selectable children.
-   Fixed: The search menu of the Toolbar search field did not allow a smart mailbox as the default mailbox.
-   Fixed: Some times the Composer window did not have the previously used location/size.
-   Fixed: The “Cancel” button in the password requester did not stop MailMate from retrying.

## Revision 5084 (Thursday, April 2, 2015) — Version 1.9.1

This release provides some important fixes and a few minor changes:

-   Fixed: The new Bundles preferences pane was unfortunately not enabled by default for new users.
-   Fixed: Under certain circumstances the HTML body part of an email could be empty (triggered by plain text emails with HTML signatures).
-   Fixed: Automatic software update was only done when launching MailMate (which also delays the distribution of this release).
-   Fixed: A bug which might have triggered the double letter issue seen by some users.
-   Fixed: Some issues related to framework exceptions.
-   Changed: Removed empty manual pages to avoid them showing up when searching.

## Revision 5078 (Tuesday, March 24, 2015) — Version 1.9

This is the first official release of MailMate since version 1.8 (r4576). The long delay (5 months) between official releases is mainly because of major changes involved in the migration from 32 bit to 64 bit. The good news is that MailMate should now be faster, leaner, and more robust than ever before.

It is important to note that all existing experimental 2.0 features (previously enabled in the General preferences pane) have been made official features of version 1.9. This includes bundles, rules, and the toolbar search field.

The following is a recap of the most interesting changes since the release of version 1.8. Some very detailed notes can be found further below for all beta releases between r4576 and r5077.

-   New: Bundles preferences pane. This allows you to enable/disable bundles of commands for various applications.
-   New: Rules pane in the mailbox editor (previously an experimental feature).
-   New: Toolbar search field activated using ⌥⌘F. Note the search field menu and its options.
-   New: Correspondent/Identity added as special header transformations. This is, e.g., used for the new “Correspondent” column for the messages outline.
-   New: Tags preferences now include a short display variant. It is intended to be used with emojis. Note that ⌘⌃+space opens an emoji keyboard on Yosemite.
-   New: Tags columns using tag display names or emojis. Double-click to search for messages with the same set of tags.
-   New: The Signatures pane now has a separate setting for caret placement (allows placing the signature at the bottom and the caret at the top).
-   New: Display count of a mailbox can be based on the counts of submailboxes (the menu item toggle is named “Include Submailboxes”).
-   New: Added `perform` command to the AppleScript API. Its argument is a list of strings identical to what would be used to define a custom key binding. Details in the help page about custom key bindings.
-   New: “Mark All Messages as Read” in the Mailbox menu.
-   New: Hidden preference `MmShowQuotedTextLimit` (show x levels of quoted text).
-   New: The “Submailboxes” feature can now handle multi-value headers. Very useful for tags and recipient headers.
-   New: Added “Source Account” column to the set of available message outline columns.
-   New: “Default Account” setting for new messages in the Composer preferences pane.
-   New: Automatically add header fields by holding down ⌥ when hitting Return in the header fields of the composer. For example, hit ⌥↩ to add a “Cc” header when focus is in the “To” header.
-   New: First shot at supporting `XOAUTH2` for Gmail IMAP and SMTP. Details in the help page for hidden preferences.
-   New: Signatures can now be restricted to certain email addresses (accounts) using a glob pattern. See the Signatures preferences pane and the manual.
-   New: Several new and improved bundles available in the Bundles preferences pane.
-   Changed: **Numerous** optimizations improving both speed and memory usage.
-   Changed: Default set of mailboxes changed (only brand new users see this since they are only read on first launch).
-   Changed: Updated manual with various missing feature descriptions.
-   Changed: Removed all of the built-in bundles. The user must now explicitly enable the ones needed in the Bundles preferences pane.
-   Changed: Distortion mode now also works for HTML messages and attachment descriptions.
-   Changed: Removed “Date > Relative” from search conditions since it should never be used for this purpose.
-   Changed: First few steps towards improved handling of HTML messages (nothing to test yet).
-   Changed: The HTML signature text field (in the Signature editor) now accepts pasted HTML. It's still best to clean it up by hand though.
-   Changed: Improved behavior when SMTP server reachability cannot be correctly determined.
-   Changed: Updated all executables to 64 bit (also implicitly fixes all issues caused by the 32 bit Apple frameworks on Yosemite).
-   Changed: MailMate now requires 10.7+.
-   Fixed: Several workarounds for several very buggy IMAP servers.
-   Fixed: Long multi-recipient headers in `mailto:` URLs were not always handled correctly (thanks to BusyMac for reporting this).
-   Fixed: Security issue related to the use of `IFRAME` in HTML emails.

## Revision 5076 (Sunday, March 22, 2015) — Version 1.9 Beta (64 Bit)

Changes since the latest beta release (r5066).

-   New: The Signatures pane now has a separate setting for caret placement (allows placing the signature at the bottom and the caret at the top).
-   New: Display count of a mailbox can be based on the counts of submailboxes (menu item named “Include Submailboxes”).
-   New: “Mark All Messages as Read” in the Mailboxes menu.
-   New: Attempted workaround for dealing with anti-virus software removing files from MailMate's cache of messages.
-   Changed: Existing experimental 2.0 features (bundles, rules, toolbar search, ...) changed to be official and enabled features of version 1.9.
-   Changed: Updated manual with various missing feature descriptions.
-   Changed: Default set of mailboxes changed (only brand new users see this since they are copied to `Mailboxes.plist`).
-   Changed: The mailbox outline remembers the expanded/collapsed state of a mailbox with submailboxes.
-   Changed: Some message outline columns (those with numbers) are only user resizable now.
-   Changed: If toolbar is hidden then it's temporarily shown if searching using ⌥⌘F.
-   Changed: Optimized handling of IMAP UID values (memory and speed).
-   Changed: Removed “Date > Relative” from search conditions since it should never be used for this purpose.
-   Changed: Tweaked default widths of preferences panes.
-   Changed: Removed (currently) unused “Events“ field in the Rules pane.
-   Changed: First few steps towards improved handling of HTML messages (nothing to test yet).
-   Fixed: Handles `data:` image URLs correctly.
-   Fixed: Default width of Description column in the Rules pane.
-   Fixed: No longer terminates when showing a context sensitive menu for non-existing `cid:` URLs.
-   Fixed: Some issues with display counts not being updated in the mailbox outline.
-   Fixed: Added missing page title to some manual pages.
-   Fixed: Manual pointed to the standard key bindings file without providing instructions to actually read it.
-   Fixed: The `insertText:` key binding and related key bindings were broken.
-   Fixed: Rare crash bug probably triggered by certain orders of rule actions.
-   Fixed: If the QuickLook panel was open when sending a message then the Composer window didn't close.
-   Fixed: Under certain circumstances MailMate terminated when changing a mailbox display count.
-   Fixed: Issue recomputing split view sizes during window resizing.
-   Fixed: Crash bug when viewing embedded emails.
-   Fixed: Problem parsing encoded message headers with incorrectly split encoded segments.
-   Fixed: Bug involving `$` for the experimental `MmCodeStylingEnabled` feature.
-   Fixed: Improved autolinking of URLs which contain parentheses.
-   Fixed: Attempt to fix an issue where MailMate stopping fetching messages (failed to go IDLE on the INBOX).
-   Fixed: Crude attempt to slow down if Gmail claims to be “throttling”.
-   Fixed: The experimental `XOAUTH2` support did not work well when given an incorrect code.
-   Fixed: Problems parsing addresses like `foo@example.com (Bar (F))` (nested parentheses).
-   Fixed: Changing the format string for “Submailboxes” did not work well if the mailbox also partitioned messages according to accounts.
-   Fixed: Customizing the “From” address in the composer did not work well if the name used did not match an existing identity.
-   Fixed: Minor accessibility improvements.

## Revision 5066 (Monday, February 23, 2015) — Version 1.9 Beta (64 Bit)

Changes since r5060. Make sure to read the release notes for r5055/r5060 as well if you haven't done so already.

-   Changed: Optimization for some queries involving shorthands, e.g., “Common Headers or Body”.
-   Changed: Workaround for issue with Groupwise server (extra NOOP to be able to do multiple APPENDs).
-   Fixed: Bug which (among other things) affected “does not contain” queries.
-   Fixed: Creating new tags or deleting existing ones did not work well for the submailboxes feature.
-   Fixed: Queries involving “does not contain” did not always work correctly.
-   Fixed: Issue when switching from “contains” to “does not contain” for certain headers, e.g., “Unquoted Body Text”.
-   Fixed: The “exists” comparison method did now work well for certain headers, e.g., “Unquoted Body Text”. (Note: Older versions of MailMate are not going to be compatible with this fix.)
-   Fixed: Copying a large number of messages on a non-UIDPLUS IMAP server was broken (as in inefficient).
-   Fixed: Some stability issues.

## Revision 5060 (Wednesday, February 18, 2015) — Version 1.9 Beta (64 Bit)

Changes since r5055. Make sure to read the release notes for that as well.

-   New: Correspondent/Identity added as special header specifiers (see more below).
-   Changed: Workaround for IMAP server bug (APPEND responses reusing UIDs).
-   Changed: Initial first responder in the single message view is now the message view instead of the headers view (when using full keyboard access).
-   Changed: The HTML signature text field (in the Signature editor) now accepts pasted HTML. It's still best to clean it up by hand though.
-   Changed: IMAP changed to more gracefully handle unexpected UNAVAILABLE responses from Yahoo server.
-   Fixed: Removing an attachment from an otherwise empty message could terminate MailMate.
-   Fixed: The toolbar search field did not work in full screen mode.
-   Fixed: Some issues with the mailbox popup button (used in various locations).
-   Fixed: Sorting by spam score in the messages outline could terminate MailMate.
-   Fixed: “Help ▸ Send Server Logs” did not include logs for non-top-level mailboxes.
-   Fixed: More gracefully handling a very buggy IMAP server which returns the same UID for different messages.

### Correspondent/Identity

A new concept has been added to the handling of message headers. MailMate now allows some (hardcoded) transformations of header values as part of the “specifier” system. For example, instead of “Recipient ▸ Address”, one can do “Recipient ≫ Correspondent ▸ Address”. This filters the recipients of the recipient headers (to, cc, bcc) such that no addresses known to be user identities are included. The opposite is also allowed: “Recipient ≫ Identity ▸ Address”. Most importantly, this feature can be used for a “Correspondent” message list column (“Any Address ≫ Correspondent”). This column lists the first address found which is not a user identity. It can also be quite useful for the Submailboxes feature in the mailbox editor.

## Revision 5055 (Tuesday, February 10, 2015) — Version 1.9 Beta (64 Bit)

The following are all changes since the last public 64 bit beta (r5035). Details for some of the features are provided below the list.

-   New: Experimental toolbar search interface.
-   New: Hidden preference `MmShowQuotedTextLimit` (show x levels of quoted text).
-   New: The “Submailboxes” feature can now handle multi-value headers.
-   New: Tags preferences now include a short variant. It is intended for emojis/emoticons. Note that ⌘⌃+space opens an emoji keyboard.
-   New: Tags columns using tag display names or emojis. Double-click to search for messages with the same set of tags.
-   New: Command actions can now tell MailMate to open message windows. This allows the (low level) creation of a canned reply while still opening a composer window to review the message.
-   Changed: Improved URL detection.
-   Changed: Messages with no date now get a “Date Received” header with the current date.
-   Changed: The check for a changed subject line in replies now always detects if the prefix is removed.
-   Changed: Working around IMAP server bug (`mail.net-c.com`) for copied messages (invalid destination mailbox UIDVALIDITY/UID).
-   Changed: Again, numerous performance improvements.
-   Changed: Slightly altered handling of UIDVALIDITY problems.
-   Changed: Given a `multipart/related` MIME message, it is now checked that the related parts can be referenced by the main part. If not, they are still displayed as attachments.
-   Fixed: Long multi-recipient headers in `mailto:` URLs were not always handled correctly (thanks to BusyMac for reporting this).
-   Fixed: The message list would show duplicates under certain circumstances, e.g., when editing smart mailboxes.
-   Fixed: The “All Body Parts” option for conditions did not work correctly.
-   Fixed: Issue with not retrying failed IMAP actions when asked explicitly to do so by the user.
-   Fixed: Markdown conversion was not done by default for plain text markdown messages (no HTML) with attachments.
-   Fixed: Minor issue with the mailbox chooser panels.
-   Fixed: Termination bug in the rebuild code (related to rebuilding draft messages).
-   Fixed: Message outline columns with numbers are now sortable again.
-   Fixed: Improved handling of wrongfully named INBOX'es (such as Inbox and inbox).
-   Fixed: Flags were not stored correctly on servers with limited IMAP keywords capabilities. This could, e.g., result in a sent message being marked unread.
-   Fixed: UIDVALIDITY warning did not always display the correct mailbox name.
-   Fixed: Correctly logging and returning an error when failing to parse a UID.
-   Fixed: Improved handling of IMAP FETCH responses.
-   Fixed: The `selectWithFilter:` key binding could crash MailMate if misused.

Note that since r5035, several new bundles have been introduced and others have been improved. See the Bundles preferences pane (⌘,). New bundles for BBEdit, DEVONThink Pro, Due, and EagleFiler. The Todoist bundle, the Calendar bundle, and more have been improved.

### Toolbar Search (Experimental)

A search field has finally been re-introduced (very early versions of MailMate had it too) to the toolbar of the main window. If you don't see it then right-click the toolbar to “Customize Toolbar...” and drag it into the toolbar (or drag the default set). If you don't want it then drag it out of the toolbar.

By default, a search is equivalent to a search in “Common Headers and Body”, but it also supports a few special one-letter modifiers. Furthermore, “and” and “or” are supported. If neither is used then it's interpreted as an implicit “and”. Here is an example:

```
foo f smith t (smith or joe)
```

This means:

```
Message contains “foo” and From contains “smith” and (To contains “smith” or “joe”)
```

(To be precise, “Message” means “Common Headers and Body” and “To” means “Recipients”.)

Here are the current modifiers:

```
f	From
s	Subject
t	To (Recipients)
b	Body text (unquoted body text)
q	Quoted text
m	Message (Common Headers or Body)
```

Searching is initiated when hitting “Enter”. Holding down ⌥ makes MailMate stay in the current mailbox. The menu of the toolbar search field allows setting the default search mailbox. (If “Current Mailbox” is selected then holding down ⌥ makes MailMate search “All Messages”.)

A default “header” can be specified for the toolbar search field (`MmDefaultSearchScope`). There is no GUI for this feature yet. It is configured in the Terminal like this:

```
defaults write com.freron.MailMate MmDefaultSearchScope -string "subject"
```

You can also search explicit headers like this:

```
delivered-to:joe x-mailer.name:mailmate
```

The search “language” is transformed to a MailMate query using an external script. Eventually, you'll be allowed to create your own search language.

### Hide Quoted Text (Experimental)

It's now possible to make MailMate collapse quoted text beyond some quoting level. Instead a line with “Show/Hide quoted text” appears. Navigation is possible using the tab and space keys.

Here is an example of using the currently hidden preference:

```
defaults write com.freron.MailMate MmShowQuotedTextLimit -integer 2
```

This should hide quote levels of level 3 or more. For testing it might be better with a lower value to see it in action more often. This currently also works for HTML messages, but there might be undesired side effects. Feedback is welcome.

### Improved “Submailboxes” Feature

Previously, using the “Submailboxes” feature of MailMate did not work well with headers with multiple values. In particular, recipient headers and tags. This has now been improved such that a message can appear in multiple submailboxes if it has multiple values.

By default, a mailbox for Tags is now included, but it'll only appear automatically for new users. You can create it manually by creating a smart mailbox with a “Tags exists” condition and then enable “Submailboxes” with the “Tags” header.

## Revision 5035 (Wednesday, January 7, 2015) — 64 Bit Beta

Note that this release requires you to open the new Bundles preferences pane and explicitly enable the bundles you need (bundles/commands are one of the experimental 2.0 features enabled in the General preferences pane).

Changes since the previous public 64 bit beta (r5025):

-   New: Bundles preferences pane. This allows you to enable/disable bundles of commands for various applications. Enabled bundles are automatically fetched from a MailMate server. They are also updated automatically (independently of updating MailMate).
-   New: Autolinking plain text URLs in HTML messages (can be disabled with `MmAutoLinkPlainTextURLsInHTML`).
-   New: Added “Source Account” column to the set of available message outline columns.
-   Changed: Refactored the use of the virtual `#source-name` header. This makes the new “Source Account” column sortable.
-   Changed: Added help anchor to password requester (for now it's just opening the account setup manual page).
-   Changed: Removed all of the built-in bundles. The user must now enable the ones needed in the Bundles preferences pane.
-   Changed: Reenabled the code for `MmEnableKeywordsCheckInIDLEForGmail`(a Gmail specific workaround).
-   Changed: Performance improvements for sorting mailbox messages. Under certain circumstances MailMate could hang for minutes.
-   Fixed: IMAP bug which could result in an infinite loop in a server connection (high CPU usage and preventing new messages from arriving).
-   Fixed: Using escape to cancel the “Find” banner for the message view now works.
-   Fixed: Crash bug related to the “Submailboxes” pane of the mailbox editor.
-   Fixed: When guessing a mailbox for a mailbox type then any already explicitly assigned mailboxes for other mailbox types are skipped.
-   Fixed: Attempt to work around a crash bug when searching or selecting certain mailboxes.
-   Fixed: Copyright lines (2015).

## Revision 5025 (Thursday, December 4, 2014)

This is the first official 64 bit release of MailMate. It includes numerous optimizations compared to the 32 bit builds and should be both faster and use less memory.

Thanks for helping me test the 64 bit release. Make sure you do the following:

-   Enable sending all crash reports in the General preferences pane.
-   Let me know about any performance issues (anything slower than it was with the 32 bit builds).

The following are all changes since the latest 32 bit release:

-   New: “Default Account” setting for new messages in the Composer preferences pane.
-   New: Completion of email addresses now also works for any contacts with a company name (and email address).
-   New: Added `perform` command to the AppleScript API. Its argument is a list of strings identical to what would be used to define a custom key binding. The frontmost window of MailMate is the target even if MailMate is not in focus (activated). Example: `tell application "MailMate" to perform {"toggleFlag:"}`
-   New: Distortion mode now also works for HTML messages and attachment descriptions.
-   New: Added search on double-click for unflagged messages in the messages outline.
-   New: Added “Call via Phone/FaceTime” menu items to headers view to learn more about the `tel:` and `facetime:` URL schemes.
-   New: Hidden preference to work around Fastmail setting `$NotJunk` on new messages: `SpamSieveCheckNotJunkMessages`.
-   New: Temporary crude control of number of the maximum number of displayed messages (`MmMaximumMessagesDisplayed`).
-   Changed: Improved behavior when SMTP server reachability cannot be correctly determined.
-   Changed: Dock counters updated for Yosemite (font change).
-   Changed: Layout file with an invalid transformation string no longer terminates MailMate.
-   Changed: 64 bit versions of all embedded executables.
-   Optimized: Switching mailboxes triggered (invisible?) animations when changing the set of columns. This is only an issue on Yosemite and the current workaround is to wrap it using `setHidden:`.
-   Fixed: Minor bug when finding candidates for address completion.
-   Fixed: Security issue related to the use of `IFRAME` in HTML emails.
-   Fixed: “High priority” image is now a template image (which makes it look better on dark backgrounds).
-   Fixed: Switched from `uri` to `cgi` in Ruby scripts since the former is deprecated (all existing scripts).
-   Fixed: Changed thread arcs to update on mouse up instead of down. Also fixes an issue with the focus not being in a window opened for a message not in the current mailbox.
-   Fixed: Updated thread arcs to use NSTrackingArea. This also fixes a crash bug on Yosemite (possibly triggered by an Apple bug?).
-   Fixed: Workaround on Yosemite for an issue where entering `"-"` would make email address completion fail.
-   Fixed: Codesigning did not work correctly on Yosemite.

## Revision 4587 (Friday, October 24, 2014)

-   New: Automatically add header fields by holding down ⌥ when hitting Return in the header fields of the composer. For example, hit ⌥↩ to add a “Cc” header when focus is in the “To” header.
-   Fixed: Issues related to specifying email addresses for signatures.

## Revision 4583 (Wednesday, October 22, 2014)

-   New: First shot at supporting `XOAUTH2` for Gmail IMAP and SMTP. See more below.
-   New: Signatures can now be restricted to certain email addresses (accounts) using a glob pattern. See the Signatures preferences pane and the manual.
-   Changed: Some icons in the messages outline have been updated for retina displays. (Special thanks to the user providing the graphics!)
-   Fixed: Clicking on a `mailto:` URL in an email now uses the identity related to the current email as the default sender.

To enable OAuth 2.0 for Gmail you need to enable this hidden preference:

```
defaults write com.freron.MailMate MmXOAUTH2Enabled -bool YES
```

After relaunching, a browser window is opened automatically (this needs to be changed). This can be very confusing if you have multiple Gmail accounts. Copy the code from the browser to the MailMate requester and then everything should work as before.

I'm very interested in users accessing non-Gmail servers with `XOAUTH2`.

## Revision 4576 (Wednesday, October 15, 2014) — Version 1.8

The list of changes since version 1.7.2 (r3905) is **very** long and all the details can be seen below in the release notes for 1.8 Beta 1-7. Version 1.8 is best described as a major maintenance release including numerous bug fixes, stability improvements, and minor feature enhancements. The following are some of the most interesting new features:

-   New: Redirection of a message using “Message ▸ Redirect” (⌥⌘E) or the `redirectMessage:` key binding. This opens a special composer window which only allows editing a fixed set of headers. MailMate also adds a `$Redirected`flag to any redirected messages.
-   New: Support for using an external editor to write emails (TextMate, Sublime Text, MacVim).
-   New: HTML signatures can be configured in the Signature preferences pane. They work in both plain text and Markdown mode. (More details in the manual.)
-   New: Remove search items using context sensitive menu (right-click) or by holding down the option key (⌥) when left-clicking.
-   New: “Redirect” and “Export to Folder” are now available as rule actions.
-   New: “Default Downloads Folder” option in the General preferences pane.

## Revision 4575 (Tuesday, October 14, 2014) — 1.8 Beta 7

The following are all the changes since r4451 (1.8 Beta 6).

-   Changed: Some optimizations to make moving/deleting a large number of messages faster.
-   Changed: Warn if the account used for the `MmDefaultAccount` hidden preference is not found.
-   Changed: Disabled workaround for Gmail flag/unread changes. Might be a bit premature though since Gmail has pulled the change for now.
-   Changed: Reorganized a few items in the preferences panes. Added “Enable”-checkmark for the attachments check.
-   Changed: Added optional standalone “Delete” button for the toolbar.
-   Fixed: Improved handling of collapsed/hidden parts of a layout.
-   Fixed: Bundle commands now properly convert HTML-only messages to canonical text (Markdown).
-   Fixed: The `selectWithFilter:` key binding now properly handles multi value headers. Also, MailMate no longer crashes if the given format string is invalid.
-   Fixed: Detecting when the message list is scrolled to top failed (Yosemite). This could, e.g., hide new messages arriving.
-   Fixed: Attempt to fix an issue with the Reminders bundle on Yosemite.
-   Fixed: Changing counters preferences did not work correctly on Yosemite.

## Revision 4551 (Friday, October 3, 2014) — 1.8 Beta 6

The following are all the changes since r4469 (1.8 Beta 5).

-   New: Hidden boolean setting for (crudely) sorting submailboxes on count (instead of alphabetically): `MmSortSubmailboxesByCount`.
-   Changed: When authenticating with an IMAP server, a `NO [ALERT]` response is now treated as a temporary error at first.
-   Changed: Minimized the use of the `RSET` command in SMTP connections since it is very slow for some servers (Exchange IMAP).
-   Changed: Keychain password strategy is now to pick the most recently modified entry even if it does not match the port (protocol type still has to match).
-   Changed: `MmReplyWroteString` now also accepts an advanced formatter.
-   Changed: Slightly fewer NOOP commands issued on IMAP connections.
-   Changed: Changed the use of `max-width:100%` to only apply to image attachments. It didn't work well for HTML messages.
-   Changed: Improved adjustment of layouts when resizing windows.
-   Fixed: Various issues with the muting feature.
-   Fixed: Improved handling of UIDVALIDITY changes (IMAP). Now shows a warning and correctly resynchronizes the mailbox if requested.
-   Fixed: `MmNeverDisplayHTML` mode now displays the images of `multipart/related` as attachments. Previously they were hidden.
-   Fixed: Failed to get UID for IMAP uploaded messages (IMAP APPEND) under certain circumstances.
-   Fixed: Now again able to import iCloud accounts from Apple Mail (only tested on Yosemite).
-   Fixed: The password fields in the account editor did not always work as expected.
-   Fixed: Calculation of minimum size of various parts of a layout was often too large.
-   Fixed: It was not possible to change an IMAP server address back to its original setting.
-   Fixed: Various table/outline related crashes fixed, for example, in the subscriptions window on Yosemite.
-   Fixed: Crash bug when sending messages.
-   Fixed: Crash bug related to deleting an account for which a move of messages was still active.
-   Fixed: Issue (hang) when canceling a message scheduled to be sent later.
-   Fixed: Too many connections could be created to a server under special circumstances.
-   Fixed: Did not properly clean up after the password leak to `Sources.plist`.
-   Fixed: Problems with `Content-Type` and `Content-Disposition` when used without specifiers.

## Revision 4474 (Thursday, August 21, 2014)

Another special intermediate 64 bit test version. Note that shortcuts for bundle commands do not work in the 64 bit test versions.

-   Various optimizations/caching done to improve message outline display (more needs to be done).

## Revision 4469 (Sunday, September 7, 2014) — 1.8 Beta 5

The following are all the changes since r4415 (1.8 Beta 4). Note that, despite the naming, Beta 3 and 4 were never released as betas and therefore you may want to read their release notes as well (further below).

-   New: The hidden preference `MmPrintedKeyword` can be used to set a tag on printed messages.
-   New: Added `MmIMAPForcePlainLogin` as an experiment to work around an Exchange issue.
-   New: Added `MmSelectDuplicatesBasedOnMessageIDOnly` for changing the behavior of “View ▸ Select Duplicates”.
-   New: For debugging purposes introduced `MmIMAPLongLogoutTimeout` and `MmIMAPKeepAliveSeconds`.
-   Changed: Several optimizations mainly making the messages outline faster. This is particularly important on Yosemite.
-   Changed: Trimming trailing spaces from subject lines when using “Subject ▸ Body”.
-   Changed: After creating a new tag (via sheet) MailMate now moves the caret to the end of the line of the tags input text field.
-   Changed: Now handling (wrong) IMAP server responses with unknown sequence numbers more gracefully.
-   Changed: Warning about unknown sequence numbers moved to the server connection log instead of standard error.
-   Changed: Search for “Not flagged” in the messages outline by double-clicking the flags column where no flag is displayed.
-   Fixed: Entering a `-` during completion of an address in the Composer had unexpected behavior on Yosemite.
-   Fixed: Thread arcs did not work properly on Yosemite.
-   Fixed: Dragging multiple folders to the dock icon did not work well.
-   Fixed: Bugs related to the “Redirect” action for mailbox rules.
-   Fixed: Performance bug when selecting a large number of messages.
-   Fixed: MailMate did not handle it gracefully when a server (wrongly) reported an already existing UID for an uploaded message.
-   Fixed: An issue with SMTP settings not being correctly stored/retrieved.
-   Fixed: Crash bug related to an unexpected (temporary?) disappearance of a message in an IMAP account.
-   Fixed: Detecting IMAP server address changes in the IMAP account settings did not work well (a warning sheet was shown too often).
-   Fixed: Improved handling of HTML tags when using Markdown.
-   Fixed: Removed incorrect warning about empty text body parts.
-   Fixed: Various memory leaks.

## Revision 4415 (Friday, August 8, 2014) — 1.8 Beta 4

The following are all the changes since r4374 (1.8 Beta 3).

-   New: Now also searching nick names in Contacts when doing address completions in the composer.
-   New: Specifier to get the tagged part of a tagged email address (`someone+tag@example.com`). Hardcoded for plus-tagged addresses for now.
-   New: “Empty message” warning can now be suppressed.
-   New: Disabling `MmStickyMessagesEnabled` tells MailMate to immediately update a smart mailbox when flags/keywords/tags are changed.
-   New: MailMate now terminates when getting into certain unexpected states. This should help fix various bugs.
-   New: Code styling in outgoing emails (very experimental and undocumented for now).
-   Changed: Counters ordered differently to put unread count in the top right corner by default.
-   Changed: Calendar bundle better at informing about AppleScript errors.
-   Changed: Now a `<div dir=auto>` is generated for each paragraph before displaying an email. This improves the handling of messages with both left-to-right and right-to-left paragraphs.
-   Changed: Manual page about custom key bindings explicitly notes that multi-action key bindings are possible.
-   Changed: Emphasized in the manual how the Counters preferences pane should be interpreted.
-   Changed: Comment about getting a mailbox UUID using “Edit > Copy” (manual page about hidden preferences).
-   Changed: Now warns the user if the logs are empty when using “Send Server Logs”.
-   Changed: Now allowing `Bcc` in `mailto:` URLs (this is explicitly allowed by the latest `mailto` RFC).
-   Fixed: Incorrect use of CIDs for inline images (Hotmail) triggered various bugs in MailMate when saving/opening attachments.
-   Fixed: Email address de-obfuscation was broken. It did not work as stated in the manual (automatically converting, e.g., `user at example dot com` to `user@example.com`).
-   Fixed: Case insensitive comparison of email addresses when looking for S/MIME certificates.
-   Fixed: Rules can be used to copy messages, but this was a problem in some parts of the code which do not expect this kind of “recursion”.
-   Fixed: Hardcoded `emate` to use `/usr/bin/python2.7` to avoid problems with alternative configured/installed versions of python.
-   Fixed: Incorrect error output when “All Messages” has account submailboxes.
-   Fixed: Various bugs related to only including root messages from the message threads when all messages were expected.
-   Fixed: The context sensitive menu for search items no longer worked.

## Revision 4374 (Thursday, July 3, 2014) — 1.8 Beta 3

The following are all the changes since r4214 (1.8 Beta 2).

### New

-   New: “Convert Markdown to HTML” menu item toggle to control whether or not Markdown plain text body parts are converted to HTML.
-   New: Quick Look works in the Composer (currently with the side-effect of saving the message).
-   New: The IMAP/SMTP account editor now includes password fields.
-   New: Various improvements for VoiceOver (messages outline and mailboxes outline).
-   New: Hidden preference to make MailMate use a specific browser for external links (`OakBrowserAppBundleIdentifier`).
-   New: Experimental unwrapping of hard-wrapped plain text body parts (`MmAutomaticUnwrapEnabled`).
-   New: Key binding selector `toggleMarkdown:`.
-   New: Key binding to launch bundle commands: `performBundleItemWithUUID:`.
-   New: Added `#` to Gmail key bindings for deleting messages.
-   New: Added compound-tip (hold down ⌥) to the Mailboxes/Conditions panes in the Smart Mailbox Editor.
-   New: Hidden preference to hardcode the IP used for the EHLO SMTP response (`MmSMTPFixedIP`).
-   New: Experimental fine-grained support for defining internal addresses (`internalAddressPattern` and `internalAddressPatternEnabled` in the `Identities.plist` file).
-   New: Non-internal addresses are now clearly marked in the address fields using a red exclamation mark.
-   New: CSS for outgoing messages (undocumented for now).

### Changed

-   Changed: Disabled automatic conversion of plain Markdown text to HTML for multipart messages. This is more intuitive.
-   Changed: Now better at guessing what `iso-2022-jp` really means (in the `iso-2022-jp-x` family).
-   Changed: Improvements to certificate verification doing as little work as possible on the main thread.
-   Changed: Improvements to password verification doing as little work as possible on the main thread.
-   Changed: Generated HTML changed a bit to be able to hide the headers part with CSS (for printing).
-   Changed: Images are now always limited to the width of the message view. Also in HTML messages.
-   Changed: Messages in the junk mailbox which are not marked as junk (using the `$Junk` keyword) now provide better options in the banner.
-   Changed: Pending “send later” messages are now more clearly marked as such in the State column (“Pending for later”).
-   Changed: Ensured that the INBOX of an IMAP account cannot be renamed.
-   Changed: In the composer, selecting an already selected signature is now equivalent to selecting “No signature”.
-   Changed: MailMate now uses the current version of the OS to look for updates. This allows the update server to provide updates based on OS version.
-   Changed: IMAP code can now work (almost) completely without using `UID SEARCH` with non-`UIDPLUS` servers (this was already true for `UIDPLUS`servers). This should make MailMate better at working with primitive servers such as Exchange IMAP and Davmail (Exchange gateway).
-   Changed: If a `UID SEARCH` (IMAP) is rejected as `BAD` then it's not used in any future use of the same connection.
-   Changed: “Search with Google” in context sensitive menus now uses the default browser instead of the default hardcoded (by Apple) use of Safari.
-   Changed: New improved handling of IMAP UIDs (faster and uses less memory).
-   Changed: Inserting spaces between addresses in multi-address fields is no longer allowed. This prevents the user from “breaking” completion behavior.
-   Changed: The statistics layout now remembers column sizes.
-   Changed: Disabled App Nap by disabling `NSSupportsAutomaticTermination`in `Info.plist`.
-   Changed: Various changes to avoid the “too many connections” error for Gmail.
-   Changed: When closing a search, a single message selected is maintained if possible. No selection still brings the old selection back.
-   Changed: Improved behavior when clicking on links in HTML emails where the `http` URL scheme is (wrongly) missing.
-   Changed: Improved MacVim bundle by O'Shaughnessy Evans (now uses `MM_LINE_NUMBER` to place the caret).

### Fixed

-   Fixed: Bundle commands now work on Yosemite (fixed problem with the use of `ruby`).
-   Fixed: “Show Details” now works for all types of S/MIME encrypted messages (showing the signature certificate if it is available).
-   Fixed: The “None” operator in the Mailboxes pane did not work correctly if used at the top-level in a mailbox with no conditions.
-   Fixed: Styling problem with Markdown tables.
-   Fixed: “Message Body Parts” menu now works correctly (the menu items for specific menu items have not worked for some time).
-   Fixed: Parses and displays “group display names” in recipient headers again (not a perfect solution, but good enough for most use cases).
-   Fixed: Various issues with the existing-draft-warning-sheet.
-   Fixed: URLs in the composer were not visually updated (when written or changed).
-   Fixed: Bug in the database handling of headers (triggered when cleaning up certain header files).
-   Fixed: Search-field for the message view (⌘F) can scroll when searching for long strings.
-   Fixed: Memory-usage issue, in particular, for messages with a deep hierarchy of body parts.
-   Fixed: Saving a draft in an _empty_ Drafts mailbox could trigger a duplicate to appear.
-   Fixed: Handles addresses like this correctly: "'Example' via Example" [foo@bar.com](mailto:foo@bar.com)
-   Fixed: Various issues with MailMate not correctly handling the case insensitivity of IMAP keywords/flags.
-   Fixed: The intra-emphasis detection in Markdown conversion was buggy (a `sundown` bug).
-   Fixed: Restoring drafts could often result in program termination -- this might also fix a related database corruption issue.
-   Fixed: Yet another workaround for a buggy IMAP server.
-   Fixed: Long-standing bug for header specifiers. Under certain circumstances empty values could be reported after a database cleanup event, for example, resulting in an empty “To” column.
-   Fixed: When using the `emate` command (or AppleScript) to create a message with a specific “From” header then MailMate failed to place it in the correct account (and tried to send it with the wrong SMTP server).
-   Fixed: Some “Counter” settings (non-existing mailbox) could trigger empty notifications to be shown.
-   Fixed: Playing sounds could (rarely) lead to a crash.
-   Fixed: Relaunching for rebuilding database did not always work as intended.
-   Fixed: “Edit as New Message” also respects the default “Send Later” value.

## Revision 4214 (Friday, May 2, 2014) — 1.8 Beta 2

The following are all the changes since r4025 (1.8 Beta 1).

### New

-   New: HTML signatures can be configured in the Signature preferences. They work in both plain text and Markdown mode. (More details in the manual.)
-   New: Remove search items using context sensitive menu (right-click) or by holding down the option key when left-clicking.
-   New: Introduced “Message ▸ Open Attachments” (⌥⌘↩). Also works in Quick Look where it opens the currently viewed item.
-   New: Replying to a message for which a draft already exists now triggers MailMate to suggest editing the existing draft.
-   New: “Redirect” and “Export to Folder” are now available as rule actions.
-   New: `MM_LINE_NUMBER` is now provided to commands triggered from the composer. Currently used by some of the text editor bundles to set the initial caret location.
-   New: Hold down ⌥ to do “Save As...” instead of “Save” when clicking the “Save” button.
-   New: Experimental workaround for buggy Exchange IMAP servers: `MmExchangeAuthPlainWorkaround`
-   New: Now logging database corruption events in `~/Library/Application Support/MailMate/database.log` since users rarely note them before rebuilding.
-   New: It's now easier to send all server logs (use “Help ▸ Send/Attach Server Logs”) when reporting server issues. Note that logging is only enabled when the “Activity Viewer” is open.
-   New: MailMate no longer merges replies to multiple messages (except if holding down ⌥ when clicking Reply). A hidden preference `MmMergeReplies` can be used to get the old default behavior.
-   New: Introduced `MmDefaultSearchMailbox` to change the default mailbox for “Edit ▸ Find ▸ Search All Messages”.
-   New: Added `newIMAPMailbox:` and `newSmartMailbox:` to key bindings list.
-   New: Added `copyAsLink:` to key bindings list.
-   New: Configurable maximum log size (number of lines) in the Activity Viewer (`MmMaxConnectionLogSize`).
-   New: MailMate can now handle missing header encodings by guessing the header charset based on the use of charsets in other headers and/or the body of the message.
-   New: Warning sheet is now shown when trying to add a folder as an attachment (which MailMate cannot currently handle automatically).
-   New: Experimental preference, `MmStrongMutingEnabled`, which mutes an incoming message in a thread even if it explicitly uses one of your email addresses.
-   New: Experimental preference, `MmStickySearchConditions`, which disables the code that would usually clear an active search when closing a window or quitting MailMate.
-   New: Distortion mode now also distorts most of the mailbox names.

### Changed

-   Changed: No longer returning to the original mailbox after a search if the mailbox selection has been changed by the user.
-   Changed: Handling non-standard IMAP response from some (unknown) IMAP server when authenticating (lines wrongly tagged with `-ERR`).
-   Changed: Optimized queries (smart mailboxes) with large right hand side sets. Especially important when rebuilding the database.
-   Changed: “Copy as Link” now works in most contexts including the single message window.
-   Changed: Inline emphasis in Markdown disabled.
-   Changed: “Move Out of Junk” now defaults to the Inbox when the previous mailbox is unknown.
-   Changed: Message dividers when selecting multiple messages are now more subtle. When printing page breaks are used instead.
-   Changed: Added time stamps to server logs and changed the timeout strategy.
-   Changed: Improved charset guessing a bit to handle badly formatted Japanese 7-bit messages (`iso-2022-jp`) and some other Asian charset encodings.
-   Changed: MailMate now parses invalid dates like `28-Jan-2014` (which should have been `28 Jan 2014`).
-   Changed: When extracting a TNEF attachment then a comment is added even if it does not contain any real file attachments. This can easily happen since a TNEF attachment might only contain Outlook-specific data.
-   Changed: Window titles in the Windows menu are now slightly different to make it easier to find mailbox windows.
-   Changed: TextMate/Sublime bundles now warn if they cannot find mate/subl.
-   Changed: Rules are no longer applied if they are triggered by mailbox configuration changes (e.g., changing conditions).
-   Changed: Various IMAP improvements.

### Fixed

-   Fixed: Commands now work for both OmniFocus 1 and 2. Improved behavior when adding multiple items.
-   Fixed: For TextMate 2 the title of the window is now the subject of the message.
-   Fixed: The “is not” or “does not contain” comparison methods did not work correctly for multi-value (virtual) headers.
-   Fixed: Collapsed threads in the messages outline show the date of the most recent message (which is already used for sorting).
-   Fixed: Format strings with non-existing values ignored else-clauses (this had many side-effects).
-   Fixed: Documented `defaultValue` for custom composer headers.
-   Fixed: Custom composer headers with default values did not work well with “Use as Default Headers”.
-   Fixed: Custom composer headers are now sanitized to avoid crashes on erroneous input.
-   Fixed: Using “Save as PDF” now has a useful default filename (based on subject body).
-   Fixed: Messages with no subject did not work well for saving messages (also a problem when putting a message on the pasteboard).
-   Fixed: Workaround for an issue where the SMTP password requester was never shown when the current password failed.
-   Fixed: MailMate did not handle an unexpected NIL response gracefully when fetching a message.
-   Fixed: Expanding Contacts (Address Book) groups now only expands the first group found if group names are not unique.
-   Fixed: Composer preview display problem for Markdown.
-   Fixed: Issue with rules when rebuilding database.
-   Fixed: No longer takes account offline if an action fails with “do not exists” for a single mailbox.
-   Fixed: IMAP code no longer tries to `LOGOUT` if a `BYE` response has been received from the server.
-   Fixed: Major bug in the database related code. This could potentially have all kinds of weird side-effects, e.g., empty values in the messages outline or the headers view.
-   Fixed: Startup crash resolved for users with old databases where 0-chars were allowed in headers if they were encoded.
-   Fixed: Crash bug triggered by headers with one or more encoded NULL characters. The bug was triggered when, e.g., basing a search on such a header.
-   Fixed: The open/closed state of the “Activity Viewer” is now again maintained between launches.
-   Fixed: Signing emails with attached/forwarded emails often resulted in the emails being quoted-printable encoded. This was a bug and the resulting emails were not handled well by earlier versions of MailMate itself.
-   Fixed: IMAP keywords were wrongly allowed to include spaces in the “Tags” preferences pane.
-   Fixed: Automatically cleaning up any signatures added using `\r` instead of `\n`. This fixes problems with duplicate signatures for some users.
-   Fixed: Rare crash bug for certain types of key presses.
-   Fixed: Bug in the handling of date based queries.
-   Fixed: Crash bug on startup for some advanced smart mailbox configurations.
-   Fixed: Some bugs related to restoring search conditions from search history or user defaults.

## Revision 4025 (Friday, February 14, 2014) — 1.8 Beta 1

The following are all the changes since r3905 (1.7.2).

### New

-   New: Redirection of a message using “Message ▸ Redirect” (⌥⌘E) or the `redirectMessage:` key binding. This opens a special composer window which only allows editing a fixed set of headers. MailMate also adds a `$Redirected`flag to any redirected messages.
-   New: Support for using an external editor to write emails.
-   New: Support for “TextMate” as an external text editor.
-   New: Support for “Sublime Text” as an external text editor (thanks to Torsten Grust).
-   New: Support for “MacVim” as an external text editor (thanks to O'Shaughnessy Evans).
-   New: Experimental preference to launch external editor automatically. For TextMate: `defaults write com.freron.MailMate MmBundleCommandLaunchedOnTab -string "0CE35D01-7B5D-4112-B379-E7BFC10AC55A"`(it's the UUID of the bundle command).
-   New: “Default Downloads Folder” option in the General preferences pane. This also works for the `saveAttachmentsInDownloads:` custom key binding selector.
-   New: “Save” button in the message view for attachments.
-   New: Date comparisons (“is (not) within last”) now also allows hours and minutes.
-   New: “Format ▸ Indentation ▸ Increase/Decrease (⌘</kbd>] / ⌘</kbd>[)”. Note that this also works for quoted paragraphs (without indenting the quote characters).
-   New: Menu item for applying the rules of the currently selected mailbox. Shortcut is ⌥⌘L (same as Apple Mail).
-   New: Key binding selector to apply rules of the current mailbox to the selected messages (`applyRules:`).
-   New: “Add to Keychain” button when viewing an S/MIME certificate.
-   New: Hold down the ⌥ key in “Go to Mailbox” to “Edit” instead of “Go to”.
-   New: IMAP mailboxes/accounts and universal mailboxes now allow a set of conditions to reduce the set of messages displayed. Think of it as regular mailboxes with built-in smart mailbox capabilities.
-   New: 2Do bundle contributed by Max Rydahl Andersen.
-   New: Gmail key bindings include ⌘-return/enter for sending.
-   New: IMAP connection balancer. Many users experience problems with exceeding a server limitation on the number of connections. MailMate tries to handle this quietly by automatically reducing the number of connections when authentication fails. An error is only displayed if the last connection fails. MailMate also automatically tries to increase the number of connections at a later time.
-   New: Experimental hidden preference: `defaults write com.freron.MailMate MmNeverDisplayHTML -bool YES`
-   New: Hidden preference to enable experimental initialization of the `To` header: `MmListPostLookupEnabled`
-   New: The context sensitive menu item titles for attachments (also inline images) include the save location and filename.
-   New: Using `<.sender.>` as special value for default Bcc makes it behave dynamically (mirroring the sender email address).
-   New: Some copy/paste actions are now supported for the mailbox outline. In particular, the mailbox UUID is put on the pasteboard.

### Changed

-   Changed: “Send and Archive” ignores the archive part if the message replied to is in “Sent Messages”. It is unlikely the user would want to archive when sending a follow-up message.
-   Changed: Improved the initially chosen identity for new messages.
-   Changed: Distortion Mode now works better for non-ASCII languages. It still does not work well for languages with no spacing.
-   Changed: The Markdown setting is now respected for `mailto:` URLs with no body text.
-   Changed: MailMate tries to automatically detect whether or not it's connecting to an SSL wrapped port (like 993). There is a slight delay if it's not the standard 993 port and therefore it's possible to explicitly tell MailMate about this by adding a `s`, e.g., `465s`. Most people shouldn't need this, but it might be useful if connecting via a tunnel to `localhost`.
-   Changed: When undoing MailMate tries to insert a message in the currently displayed list of messages even if it does not belong due to a flag change (this should make the behavior of undo more intuitive).
-   Changed: The `formatted` input type for commands now automatically adds a newline after each message. A `suffixString` value can be used to change this. (This is still work-in-progress.)
-   Changed: Logs the SSL protocol and cipher used for a connection.
-   Changed: Workaround for buggy IMAP server. If INTERNALDATE is NIL then it's treated like it is the current date.
-   Changed: Workaround for buggy IMAP server which occasionally outputs untagged responses like `Bogus sequence in UID FETCH`.
-   Changed: Parsing of `List-ID` identifier is less strict to be able to handle non-standard values.
-   Changed: No longer including Bcc when inline forwarding a message (this would most often be a sent message).
-   Changed: Improved error output when failing to obtain a server connection.
-   Changed: Initial focus is now always in the messages outline.
-   Changed: When switching layout MailMate tries to maintain the current focus.
-   Changed: List-related message headers are now parsed slightly different.
-   Changed: Added `showThread:`, `showCorrespondence:`, and `expungeMessages:` to key bindings list in the manual.
-   Changed: To/Cc now always takes precedence over delivery headers when deriving an identity for a reply using an “Address Pattern”.
-   Changed: MailMate no longer allows the use of the insecure SSLv2 method for the SSL handshake with a server.
-   Changed: Added `MmIMAPMaxNumberOfRetries` for debugging purposes.

### Fixed

-   Fixed: A smart mailbox based on a date comparison now updates correctly and immediately when a message should arrive/leave the mailbox. This includes applying rules in these mailboxes. (not tested thoroughly)
-   Fixed: Use of `<,>,&` was not correctly escaped in `<pre>` blocks when generating HTML.
-   Fixed: Verifying/decrypting parts of an embedded message could fail if the `message/rfc822` part wrongly used QP/base64 encoding.
-   Fixed: Major problem with read/write timeout values growing to a size which would eventually prevent establishing IMAP/SMTP connections. This is likely to fix various problems with accounts becoming “unavailable” after several hours of using MailMate (primarily a problem for users with unstable internet access).
-   Fixed: A smart mailbox using the “is in” operator with a right hand side smart mailbox defined after itself (in the mailbox outline) was incorrectly always empty when launching MailMate.
-   Fixed: Crash bug when quitting.
-   Fixed: Attempted to fix an old issue with crashes related to variously dynamically created menus.
-   Fixed: MailMate now terminates when detecting certain problems with threading (this is to catch a known unresolved problem a bit earlier).
-   Fixed: Date headers on printed pages are now in the local time zone.
-   Fixed: When printing a single HTML message, the headers are (usually) a bit more readable now (no missing colons).
-   Fixed: Crash bug triggered when pasting a non-email-address in an address field.
-   Fixed: For plain text messages, the trailing space of a quoted signature separator was wrongly stripped.
-   Fixed: Quoted printable encoding is no longer enabled when the only “problem” is a quoted signature separator.
-   Fixed: The `smartypants` converter now also leaves `"-- "` by itself if it's quoted.
-   Fixed: Numerous memory leaks.
-   Fixed: A CID URL is now handled by opening the (first) message to which it belongs.
-   Fixed: A password requester could be shown twice if the initially selected mailbox triggered a synchronization. Primarily a problem when not saving the password in the keychain.
-   Fixed: Signatures could appear twice -- triggered by some problems with escaping text for use with Markdown.
-   Fixed: Drag'n'drop of emails to some (but not all) other applications could fail due to a bug in MailMate.
-   Fixed: Notifications can now be used in the (undocumented) `multipleMessages`execution mode when returned as an action from scripts.
-   Fixed: Certain orders of actions could result in a message being shown in a mailbox in which it was no longer located.
-   Fixed: The composer now always starts with an empty undo stack.
-   Fixed: Typo in the LaunchBar example.
-   Fixed: Disappearing “is in” rows in mailbox conditions. This also fixes a delay when enabling/disabling/changing submailboxes.
-   Fixed: Changes in disabled rows were not detected and saved in the rules editor. Also some performance improvements in the rule editor.
-   Fixed: Problems with parsing emails and mbox files which use a single carriage return for newlines.
-   Fixed: When editing tags, switching to another message before committing no longer applies the change to the new selection.
-   Fixed: Problem with mailboxes going into a “failed” state (in particular Gmail). This should now happen more rarely and if it happens it should be easier to get them online again.

## Revision 3905 (Tuesday, December 17, 2013) — Version 1.7.2

It's been a busy month because of the successful crowd funding campaign. Thanks to all who made contributions and/or helped to spread the word. This update primarily includes various low level changes and fixes, but it also includes some new bundles for those of you with the experimental 2.0 features enabled (see the General preferences pane).

### Calendar Bundles

Experimental bundles added for Calendar (iCal), BusyCal, and Fantastical. The latter two are based on bundles provided by Torsten 'Teggy' Grust (thanks!). The Calendar bundle defaults to the use of a calendar named “Work”. For now, you can change this using the `defaults` command in the Terminal:

```
defaults write com.freron.MailMate MmDefaultCalendarName -string "MyCalendar"
```

If you select text in the displayed email then this is used for the creation of the event. Otherwise, MailMate tries to automatically find a suitable date in the message.

### Task Manager Bundles

Three new bundles have been added to match the functionality of the OmniFocus/Reminders bundles. The new bundles provide integration with Evernote, Things, and The Hit List.

### SmartyPants

Experimental SmartyPants support has been implemented. It only works for HTML and HTML is generated even if only needed for SmartyPants. Quoted text is ignored by the converter. The SmartyPants conversion skips any occurrences of `"-- "`.

Enable this feature as follows:

```
defaults write com.freron.MailMate MmSmartyPantsEnabled -bool YES
```

### Other

Most of the following is only of interest to bundle creators.

-   New: `MM_SELECTED_RANGE` to get the selected text for the canonical input of a command.
-   New: `MM_SUPPORT_PATH` in the environment variables to easily access shared commands.
-   New: Standalone binary to detect dates in text (named `detect`). It looks for free text dates in the input choosing the first one which is later than “now”. Otherwise, it simply selects the first date. The code is based on Apple's `NSTextCheckingTypeDate`.
-   New: Drag'n'drop to an IMAP mailbox (or mailbox based on a IMAP mailbox) to import messages/mbox files.
-   New: Drag'n'drop files to the messages outline to import messages/mailboxes.
-   New: The list of specifier shorthands can now be extended (very low level).
-   New: Added hidden setting to change the total number of allowed connections (default is 45): MmIMAPTotalMaximumOfConnections
-   Changed: Improved handling of custom key bindings in the Composer (with/without ⌘ works in the text view, without ⌘ works in the headers).
-   Changed: The manual page on custom key bindings now clarifies how modifiers for custom key bindings need to be ordered.
-   Changed: Deriving an identity now also takes the `Envelope-To` header into consideration.
-   Changed: Improved handling of selected text in HTML messages when replying to a message.
-   Changed: Gmail labels are not fetched/synched if none have been specified in the Tags preferences pane.
-   Changed: Manual page on Tags now makes it more clear how tags can be added in the composer window.
-   Fixed: Smart groups in Contacts/Address Book are now properly expanded in recipient fields (previously only regular groups worked).
-   Fixed: Korean text with the ks_c_5601-1987 charset did not work, because it is not supported by iconv.
-   Fixed: `selectWithFilter:` now works with values containing single quotes.
-   Fixed: `#date-last-viewed` and `#date-sent` properly handled by the conditions editor.
-   Fixed: Replying to sent messages no longer duplicates any auto-added Bcc.
-   Fixed: Now handles (erroneous) `cid:` URLs containing file path /'s.
-   Fixed: Now handling messages with (erroneous) dates where day and month have been swapped.
-   Fixed: Crash bug related to S/MIME certificates with no email address assigned.
-   Fixed: Workaround for issue with SSL on secure.runbox.com.
-   Fixed: Non-UTF8 mailboxes were not displayed correctly in undo/redo menu items.

## Revision 3836 (Sunday, November 10, 2013) — Version 1.7.1

Don't miss the 1.7 release notes if you haven't read them yet.

-   New: window sheet which asks user to go to the crowd funding site. It can easily be told to not appear again.
-   New: Added GUI option in the General preferences pane for enabling experimental 2.0 features.
-   New: Changed default behavior for new Gmail accounts. 1. “[Gmail]/All Mail” is subscribed. 2. Default archive mailbox is “[Gmail]/All Mail”. Existing accounts are not affected.
-   New: A Gmail label column is shown in Tags preferences if the user has any Gmail accounts. Any tag with a Gmail label defined is _not_ fetched as an IMAP mailbox.
-   New: Added `replyMessage` action for bundle commands (undocumented 2.0 experimental feature).
-   New: Hold down ⌃⌥ when selecting a message in the outline to select all related message. The result depends on the column selected (the selection matches what is searched for if double clicking).
-   New: The `selectWithFilter:` key binding has been changed to accept a format string. This can be used to select messages related to the current message. For example, a shortcut (⌃⌥D) to select all messages from the same sender and delete them:`"^~d" = ( "selectWithFilter:", "from.address = '${from.address}'", "moveToMailbox:", "trash" );`
-   New: Experimental Reminders bundle which works similar to the OmniFocus bundle (with the same shortcuts).
-   Changed: Low level hint in the manual for using custom mailbox graphics slightly changed to work for 10.9 (Mavericks).
-   Changed: IMAP code now detects the OVERQUOTA response code and a better error message is provided.
-   Changed: Emphasized that files in the application bundle should not be modified (manual page about custom key bindings).
-   Changed: Added `(X-)Envelope-To` to the list of headers which contain email addresses.
-   Fixed: Long time bug causing recursive creation of IMAP mailboxes and eventually repeated crashes on startup.
-   Fixed: The “Always Ignore” option when failing to fetch IMAP messages did not work correctly.
-   Fixed: When failing to fetch messages, the list of UIDs could be too long to fit on screen.
-   Fixed: The error message did not include the correct port number when MailMate failed to make a secure connection.
-   Fixed: Crash bug related to the use of the “View ▸ Columns” menu.
-   Fixed: Typo in the Alfred 2 tip in the manual page about the extended URL scheme.
-   Fixed: When only having S/MIME enabled and replying to a message which was to be signed by default then the default protocol was some times wrongly changed to OpenPGP.
-   Fixed: Now better at handling decoding errors with the `Shift_JIS` charset.
-   Fixed: Copying addresses from the headers view did not always work well when pasting them in an address field (the name part was not quoted).
-   Fixed: Transformations in format strings did not always work (for example, `${from.name:/capitalize}`).
-   Fixed: Some users experienced a crash when quitting MailMate (e.g., when updating).

## Revision 3790 (Thursday, October 17, 2013) — Version 1.7

The lists of new features, changes, and fixes are long, and you are likely to find something of interest, but you may be even more interested in the section below the list. It describes some of the future features of MailMate and how you can try some of them right now.

-   New: GUI settings to control how signing/encryption is derived when replying.
-   New: Markdown behavior for replies is now configurable (Composer preferences pane).
-   New: Universal mailboxes (Inbox, Drafts, etc.) can now be edited with the Mailbox Editor. Only a single pane for now.
-   New: Added GUI option for whether or not “Move to Mailbox” should close the window after moving message(s) (Viewer preferences pane).
-   New: Hold down ⌥ when using using the “Move to Mailbox...” panel (⌥⌘T) in order to copy instead of move.
-   New: Copy messages using ⌘C. They can be pasted (⌘V), e.g., in the Finder or in the Composer.
-   New: Use paste (⌘V) to copy a message to the current mailbox.
-   New: Going to “Root of Thread” (⌃⌘R) now automatically displays the thread if the root is not in the current mailbox.
-   New: Smart mailboxes are now more aware of which mailbox they are based on. If based on a single IMAP mailbox then drag'n'drop and more is possible.
-   New: The `emate` command now supports adding a “Reply-To” header (also works for a `mailto:` opened using AppleScript).
-   New: Use the `emate` command (or the `mailto:` URL scheme) to set tags for new messages.
-   New: Sound selection popups also make Apple Mail sounds available. By default, the Apple Mail “Mail Sent” sound is now used.
-   New: All IMAP mailboxes (and accounts) can now be edited with the Mailbox Editor.
-   New: Added AppleScript example for emailing an attachment using Alfred 2.
-   New: Added `copyToMailbox:` key binding selector which works similarly to `moveToMailbox:` (with a mailbox argument).
-   New: Added `rootOfThread:` and `lastOfThread:` to the list of available key bindings.
-   New: Added “Deselect All” (⌥⌘A) as an alternative menu item to Select All.
-   New: Added “Last of Thread” (⌃⌘L) to the message menu.
-   New: Placeholder strings for from/to/subject, for example, “(No Subject)” instead of an empty string.
-   New: Spell check for subject header.
-   New: The `nextMessage:` and `previousMessage:` key bindings now work in a single message window if the mailbox window exists and the selection has not been changed.
-   New: Added message related key binding selectors: `selectFirstMessageRow:`, `selectLastMessageRow:`, `selectPreviousMessageRow:`, `selectNextMessageRow:`.
-   New: Added mailbox related key binding selectors: `selectNextMailboxRow:`, `selectPreviousMailboxRow:`, `selectNextMailbox:`, `selectPreviousMailbox:`.
-   New: Automatically disconnect IMAP/SMTP connections after a while (using `LOGOUT/QUIT` commands). The default is 120/30 seconds.
-   New: IDLE connections are now “checked” when leaving sleep mode.
-   New: Added “File ▸ Edit IMAP Account” menu item.
-   New: Added menu item in context sensitive menu to edit IMAP accounts.
-   New: Menu bar counters now have a “Move Out of Junk” menu item instead of “Move to Junk” when appropriate.

Read more about the following in the “Hidden Preferences” manual page:

-   New: Add your own verifications before sending a draft, for example, ensure you never send an untagged draft.
-   New: Explicitly map email addresses to OpenPGP user IDs.
-   New: Make MailMate warn when trying to send to “external” recipients.
-   New: Configurable dock counter icon size, e.g., `defaults write com.freron.MailMate MmDockCounterFontSize -float 48.0`
-   New: Configure how long a connection to an IMAP/SMTP server is kept alive (`keepAliveSeconds`);
-   New: Experimental support for the IMAP CONDSTORE extension (`defaults write com.freron.MailMate MmEnableIMAPCondstore -bool YES`).

Changes and fixes:

-   Changed: Improved “Mailbox Schedule” menu: An account default can now be configured for each IMAP acount, the children of the universal mailboxes also allow setting the schedule, “Never” has been renamed to “Manually”, and the menu display how much time has passed since the latest synchronization.
-   Changed: Long link tooltips are now line wrapped.
-   Changed: Margins for printing now allow using the full paper size (use “File ▸ Page Setup” to change the margins).
-   Changed: Updated default location of `gpg2` to be `/usr/local/MacGPG2/bin/gpg2` since the installer of GPGTools has changed behavior.
-   Changed: (de)selectAll: now works when the message list is not in focus.
-   Changed: Added new shortcut to open the Address Panel (⌥⌘1).
-   Changed: Improved warning when a secure connection is not supported by the server.
-   Changed: Mailbox chooser (“Go to/Move to Mailbox”) is now much faster.
-   Changed: Messages outline columns can now (also) be changed using “View ▸ Columns”.
-   Changed: No longer terminating if getting an EBUSY error (resource busy) when trying to delete empty folders.
-   Changed: Quick Look buttons in the message view now also makes all other attachments of the same message(s) available in the Quick Look window. The Quick Look API does not really support this, but it has been implemented by rotating the attachments (only noticeable when displaying all attachments in the view).
-   Changed: Removed special handling of signature separators. Fixed bug which stripped the signature separator when generating HTML from Markdown.
-   Changed: Replying to sent messages now works more reliably. It also works with address patterns (IMAP account setting).
-   Changed: “Reply List” now falls back to standard reply if it is not a list message.
-   Changed: Now closes auto-expanded mailboxes when drag'n'drop'ing messages.
-   Changed: Workaround for servers with _persistent_ temporary errors on login. MailMate now retries with alternative login schemes.
-   Changed: Additional check to ensure that an IMAP keyword is never applied if it is not an IMAP atom (some servers allow setting such keywords, but they shouldn't).
-   Changed: Expired server certificates are now trusted if the user has explicitly set the certificate as trusted.
-   Changed: Improved error message when parsing IMAP flags fails.
-   Changed: No longer using the non-standard XLIST IMAP command (Gmail). Instead, RFC 6154 is used which is supported by both Gmail and some other IMAP servers.
-   Fixed: Tips were wrongly initialized to start at the end. Unfortunately this means that only 1 tip was automatically shown per window.
-   Fixed: Always showing a “Details” button for OpenPGP messages. It previously failed when decrypting.
-   Fixed: Detection of follow-up messages often failed. Should be more robust now.
-   Fixed: Buggy `collapseThread:` key binding.
-   Fixed: Disables the synchronization schedule menu when it cannot be used.
-   Fixed: Incorrectly showed a failed OpenPGP encryption of a message as successful.
-   Fixed: Issue with case-sensitivity for non-ASCII mailbox names in the mailbox chooser (Go/Move to Mailbox).
-   Fixed: Links using the private `mlmt-internal` URL scheme are not shown when hovering the mouse over a link.
-   Fixed: PGP decryption bug for non-inlined encrypted body parts.
-   Fixed: Slightly improved error message when `gpg2` (for OpenPGP) cannot be found.
-   Fixed: Reflow bug of quoted text in the text editor.
-   Fixed: Server-located images are now displayed in the Drafts preview (in particular in signatures). Note that blocking is still active if the draft contains an attached message.
-   Fixed: Some junk/trash mailboxes did not have the “Empty ...” menu item enabled.
-   Fixed: Tag changes are committed when a window is closed. Important when using the single message window to make tag changes.
-   Fixed: The `collapseAll:` key binding selector now forces the messages outline to redisplay.
-   Fixed: Time zone bug when generating “Date” header. Any in-between-zones were incorrect (e.g., +0530 would become +0500).
-   Fixed: Updated `sundown` (Markdown converter) to handle some issues with signature delimiters (and short header underlinings).
-   Fixed: Updating smart mailboxes with the “is not in” comparison method rarely worked correctly when adding/removing messages.
-   Fixed: Workaround for attachments wrongly QP-encoded without encoding CRLF (generated by Outlook).
-   Fixed: “Send and Archive” in the Composer now selects the next message in the mailboxes view (when possible).
-   Fixed: Crash bug related to adding a compound row to search conditions (on the last row).
-   Fixed: Crash related to sending a message as a new message after a subject change (which triggers a warning to be shown).
-   Fixed: Long-standing crash bug when decoding a message with a completely empty body part (headers AND body).
-   Fixed: Bug with IMAP IDLE which could result in MailMate not detecting a broken connection.
-   Fixed: Synchronization problem when the number of mailboxes in “Connected” state matches the maximum number of connections for an account.
-   Fixed: IMAP code read flags twice when verifying the result of storing flag changes.
-   Fixed: When adding a new account, the universal mailboxes were often not correctly updated (until MailMate was relaunched).

### A glimpse of the future: Rules, Scripts, and Gmail labels

MailMate has come a long way since its initial release, but there is still much to do. Two of the most often requested features are rules and scripts and important progress has been made in these areas. Even though these features are not complete I would like more users to use and test them. Don't expect everything to work as expected, but please report any issues you have by email or on the mailing list.

Use the following command in the Terminal to enable the features:

```
defaults write com.freron.MailMate MmTwoPointOhFeaturesEnabled -bool YES
```

**Update:** This can now be done using a checkmark in the General preferences pane.

Restart MailMate and the Mailbox Editor of all mailboxes should include a “Rules” pane. It should then be possible to filter messages and then “Move/Copy to Mailbox”, “Set/Remove Tag”, “Play Sound”, and/or “Run Script”.

Also notice a new “Command” menu in the main menu of MailMate. By default, it contains two commands for adding messages to OmniFocus and it contains a simple command for opening a Lighthouse ticket (the issue tracking service for MailMate) when viewing a notification email from Lighthouse. How to make your own commands is, for now, undocumented, but you are welcome to ask questions on the mailing list. It is more powerful than the current examples show.

Somewhat unrelated to the above, the Terminal command above also enables a new experimental feature for Gmail. Gmail supports both standard IMAP keywords and their own label system. Unfortunately, the latter does not work well with standards compliant IMAP email clients if the user applies multiple labels to a single message (it is then fetched/stored multiple times by most email clients).

MailMate now offers a solution to this problem where (some) Gmail labels are treated as if they were IMAP keywords. This plays well with the existing support for tags in MailMate. It works as follows: A new column in the Tags preferences pane allows you to assign a Gmail label to each tag. If you assign it then MailMate is automatically going to ignore that label when it's reported by the server as an IMAP mailbox. Instead MailMate pretends the message has the corresponding IMAP keyword enabled.

**Update:** This is now the default behavior for new Gmail accounts.

Important points:

-   This solution means that you can have both Gmail mailboxes and Gmail tags. In other word, only use a Gmail label when you want to use it as a tag for messages that exist in some other mailbox.
-   Moving messages between IMAP accounts should work fine. This means you can move labelled messages between Gmail accounts and move them to standard IMAP accounts in which they'll be assigned IMAP keywords instead. In other words, this feature is also a good solution for migrating from/to Gmail.

## Revision 3549 (Friday, July 5, 2013) — Version 1.6

The following lists the considerable number of new features, changes, and fixes since the most recent public release of MailMate (April 9th, r3323). Some of the important changes are listed in their own subsections below, but it's also worth looking through the “Other changes” subsection. You'll find a gem or two in there as well.

This version of MailMate is largely based on user reports/requests and I'd like to thank everyone for their positive and constructive feedback. Also thanks to all the license buyers and, in particular, thanks to the users sponsoring some extra work hours to be spent on MailMate. You are now listed in the About window of MailMate.

### Send Later

A “Send Later” feature has been implemented. It is enabled in the Headers popup in the Composer. A simple text field allows one to write time expressions such as “tomorrow at noon” or “friday at 10”. The text is red as long as the expression cannot be interpreted. The supported expressions cannot be documented since it is based on Apples API for locating date/time-related expressions in text. In addition to this, MailMate looks for simple relative time expressions such as “2 hours 10 minutes” with support for years, months, weeks, days, minutes, and seconds. Shorthand is also supported, for example, “2h 10m” or “2h10m”. If MailMate cannot parse the expression and the user tries to send the message then a sheet is shown which allows the user to correct the problem or set an exact time. The date header of the message reflects the “send later” date (which may be sooner than the message is sent if MailMate has been offline).

Two new message outline columns are available for showing when a message is scheduled to be sent (“Pending Submission”). One of them is relative to the current time and is enabled by default for the Drafts mailbox. Finally, when reviewing messages in the Drafts folder, you can now use “Send Now” or “Cancel Send and Edit” on any messages pending to be sent.

_The work hours needed for the “Send Later” feature were partly sponsored by Self-Reliant Film._

### New mailbox editor

The Mailbox Editor has been redesigned. This is work in progress. The editor now handles a set of panes. For now, this only works for smart mailboxes, but it is planned to work for any kind of mailbox with a varying set of panes (depending on the type).

A new Submailboxes pane is available. This has settings for:

-   Automatically showing submailboxes based on a header of the messages in the mailbox. A format string can be specified for the automatic naming of these mailboxes.
-   Automatically showing submailboxes for each account (like for the standard mailboxes such as the universal Inbox).

You can, for example, automatically display submailboxes dividing messages into subsets based on year, sender, mailing list, or any other (part of a) message header. The best way to see its potential is to simply play around with the feature.

### Improved `mailto:` scheme

Improved handling of `mailto` URLs. It is now possible to specify a `from` argument. It should just be an email address and MailMate will take care of finding the corresponding identity. It works with all identity settings including address patterns. If an unknown address is given then MailMate falls back to the default account.

Improvements also include:

-   Updated `emate` to also allow a `from` argument.
-   Fixed problem with `mailto:` URLs: A composer was not opened if MailMate was not already launched.
-   Fixed various bugs related to `mailto:` handling and the automatic derivation of an identity based on recipient(s).
-   The `message:` URL scheme is now automatically bound to MailMate if the `mailto:` scheme points to MailMate. The user is first asked about this, but the user can choose to let MailMate handle it automatically in the future if the binding is lost.

### Tips view

Added a new view providing quick tips about some of the less obvious features of MailMate. It is currently shown at the bottom of the mailbox viewer and the composer (it'll be extended to the mailbox editor as well). The view can easily be dismissed by clicking an “Ok” button, but you can also tell it to never appear again. The General preferences pane includes a new setting for specifying when tips should appear. By default it is “Once a Day”.

### IMAP

-   Messages scheduled to be sent are now uploaded AFTER sending. This circumvents problems with Gmail and Zimbra and makes MailMate behave more like the majority of email clients — hopefully triggering fewer IMAP server bugs.
-   Workaround for buggy IMAP servers to allow the user to always ignore messages for which MailMate fails to fetch something. This is useful for buggy IMAP servers like MS Exchange.
-   No longer uploading drafts to the server as long as a composer window is open.
-   New hidden setting for handling server passwords. You can now add `suppressPasswordRequester = 1` to an account in `Sources.plist` and the password requester is never shown for that account. This is useful for unstable IMAP servers which randomly reject user passwords.

### `Content-Transfer-Encoding: x-uuencode`

MailMate now supports the non-standard transfer encoding named `x-uuencode`. If you have had problems with “corrupt” attachments in the past then this might fix it. The encoding seems to be generated by Eudora (maybe as an option or only by some versions), but in general it seems to be quite rare. Most email clients use base64 encoding as specified in the MIME standard. Nevertheless, some users may have a lot of these messages in their email archives.

Note that MailMate does not (and cannot) generate messages with the `x-uuencode`encoding (and this is not going to change).

### TNEF (winmail.dat)

MailMate now includes out-of-the-box support for extracting files from TNEF attachments (often named `winmail.dat`). You do not need to install anything to make this work.

Note that TNEF is a proprietary non-standard format. The sender should be notified about this and encouraged to use a different attachment format.

### Experimental support for requesting DSNs

Experimental support for requesting DSNs (delivery status notifications) as specified in RFC 3461 has been implemented. MailMate supports `RET` and `NOTIFY` although I'm not sure how widespread `RET` is used in practice. Note that the Gmail SMTP server supports neither.

To try this out, quit MailMate, and then edit this file:

```
~/Library/Application Support/MailMate/Submission.plist
```

For each SMTP server for which you would like to enable this feature, you can add one or both of the following:

```
requestDSN = "SUCCESS,FAILURE,DELAY"; // Any combination of values is accepted. You can also specify NEVER instead to never receive DSNs.
reportDSN = "FULL"; // Either FULL for the full message or HDRS for receiving headers only.
```

Note: How well this works depends on the SMTP servers between sender and receiver. Feedback is welcome.

### Other changes

-   Live preview in the Composer window (no longer just updated on Save).
-   Now showing a tooltip when hovering over a link showing the URL target. It is _not_shown if the target is the same as the displayed link title.
-   Added a “Reply All” toggle to the composer toolbar. It works as both a toolbar button and as a shortcut (both ⌘R and ⇧⌘R).
-   Improved the “Display Count” to take its default from the parent mailbox as long as it has not been changed explicitly.
-   New “Display Count” menu item: “Inherit” (from the parent mailbox).
-   De-obfuscation of email addresses when pasting text in a recipient header, for example, `user at example dot com` -> `user@example.com`.
-   Improved behavior when dealing with drafts from other email clients. They are never allowed to be sent, but they are allowed to be edited (and then sent) if simple plain text. In all other cases, “Edit as New Message” can be used.
-   Holding down ⌥ disables the inlining of a dragged image in Markdown mode.
-   Improved detection of replying to sent messages. This no longer requires messages to be in “Sent Messages”.
-   Added `dir=auto` to the HTML generated from plain text messages before displaying them. This does not work well for messages with mixed text-direction, but it's a lot better than nothing.
-   Updated the Markdown converter to always add `dir="auto"` for paragraphs. This is much better for right-to-left languages, but something similar is not yet done for the plain text to HTML converter.
-   Added footnotes support to the Markdown converter.
-   Cascading of windows has been improved (fixed).
-   Added shortcut for “Save Attachments...” (⇧⌥⌘A).
-   Added shortcut to the “Format” menu for the markup popup menu (⌃⌘M).
-   Improved the experimental TNEF handling (previously it only handled simple filenames).
-   Mountain Lion workaround: The Address Book viewer in the composer now adds to “To:” on double click. Holding down ⌥ opens the entry in the Address Book/Contacts application.
-   Added junk-related key bindings (`markAsJunk:`/`markAsNotJunk:`) to the manual.
-   Updated manual to include that inline images are possible using Markdown.
-   Added more available Composer bindings to the manual: `showHeaders:`, `showSignatures:`, `showMarkupLanguage:`, `showIdentities:`
-   Added temporary hidden prefs named `MmHeadersViewMaximum`. It can be used to limit the number of recipients shown in the headers view (default is 30).
-   Using the `goToMailbox:` key binding no longer forces focus to be the message view. The existing focus is maintained instead.
-   Now printing with the font used to display messages.
-   If the toolbar is hidden then it is also hidden after entering full screen mode.
-   Deleting smart mailboxes with children has been improved. A warning is shown if more than 1 mailbox is deleted (including mailbox children).
-   When generating a reply the email addresses are no longer forced to be lowercase.
-   Renamed Address Book to Contacts (more than 80% of users are on Mountain Lion or higher).
-   Displays a bit of “Resent” information in the headers view (`Resent-From/To`). A small first step towards support for redirection.
-   Double clicking on reply/forward-arrows in the messages outline always searches for related message(s) — disregarding the setting to open a new window on double click.
-   Added separator in the headers popup (composer) to separate standard headers and virtual headers (Tags and Send Later).
-   Release notes window no longer stays on top.

### Other fixes

-   Much faster at displaying long text messages (such as automatically generated log file emails).
-   Improved behavior when cutting text in the composer: The quoting level of the end of the range is now maintained.
-   Now regenerating `Message-ID` more often when editing drafts.
-   Full screen mode now works for all windows, not just the first one. Full screen mode also works the first time running MailMate.
-   If the `MmReplyWroteString` hidden preference is blank then no blank lines are inserted at the top of the message.
-   Fixed bug in checking for sent messages after a crash which could lead to a new crash.
-   Fixed “Send and Archive” such that various checks are done (as happens for “Send”), e.g., attachments check.
-   Fixed drag'n'drop of smart mailboxes to match what is allowed by “New Smart Mailbox...” (everything is allowed).
-   Fixed byte size count when importing/rebuilding (previously it could overflow).
-   Fixed various issues related to changing layouts.
-   Fixed problem with “Edit as New Message” for messages with inlined images.
-   Fixed problem with caching the scroll position of a message.
-   Fixed problem with hidden subviews when changing layout or when launching MailMate.
-   Fixed bug in the code for removing extraneous whitespace in signatures. Changes to signatures were not saved if whitespace was removed.
-   Fixed problem with duplicate signatures (triggered by signatures containing one or more lines with nothing but spaces).
-   The “Edit Signatures...” menu item in the Composer now jumps to the Signatures pane in the preferences (instead of just opening the Preferences window).
-   The memory mapping code now crashes hard for ENOMEM errors. This is slightly better than telling the user that a database rebuild might help. (This is not the ideal fix needed for ENOMEM errors.)
-   Fixed potential crash bug in the string formatter used in numerous parts of MailMate (triggered by non-UTF8 strings).
-   Fixed whitespace issues when displaying plain text messages. Extraneous whitespace was displayed both in the beginning and the end of a message. The changes also affects the default CSS file.
-   Fixed bug related to inlining multiple images in Markdown mode. Given a special order of events MailMate would unexpectedly terminate.
-   Fixed crash bug for the “Correspondence” button triggered by an email address containing one or more single quote marks.
-   SMTP now works even if a username is given for a server with no authentication requirements. Previously MailMate would repeatedly ask for a password which was not needed.
-   Fixed problem with the Thread button when no messages were selected. This creates a general search for messages in the same thread as all messages in the current mailbox.

## Revision 3323 (Tuesday, April 9, 2013)

The following critical bugs were fixed shortly after the 1.5.4 release.

-   Fixed bug making it impossible to write some letters with certain keyboard layouts, for example, writing “ô” with the French keyboard layout.
-   Fixed bug triggered when inlining images in Markdown mode combined with signing/encrypting.
-   Fixed IMAP parser: FETCH responses were incorrectly assumed to always be uppercase.

## Revision 3316 (Thursday, April 9, 2013) — Version 1.5.4

-   Supports inline images in Markdown mode. Markup for referencing an attached image is inserted when adding an image to the textview (dragging or pasting).
-   “Open Link“ menu item now works in the composer.
-   Opens links in the composer when hitting the enter key.
-   Now derives a name from other headers if a `Reply-To` header does not include the name of the recipient.
-   Assigned shortcut to New Smart Mailbox (⌃⌘N).
-   Changed shortcut from ⌘0 to ⌥⌘0 (like Apple Mail) for opening the Activity Viewer.
-   Nicer formatting of large numbers in the title bar.
-   Added “Reply List” menu item.
-   Added hidden preference named `MmMessagesOutlineMoveStrategy`. It controls how the selection changes when moving messages out of the currently selected mailbox. The possible values are `next`, `previous`, `unreadOrNext`, `unreadOrPrevious`. Note that `next`/`previous` is interpreted in relation to the current sorting direction. The `unread` variants always prefer an unread message if only one of the next/previous messages is unread.
-   Handles `Re:`-prefixes in Chinese which use a different type of colon (full width colon) when generating the subject line for a reply. The change is also likely to improve the handling of `Re:` in other non-ASCII languages.
-   Attempt to work around a problem with input of japanese characters in mixed Japanese/Western messages.
-   Cleaned up default css file for the message view. Cleaned up HTML generation.
-   When switching mailboxes, any selected unread messages are no longer marked as read.
-   When switching mailboxes then extreme scrolling positions are maintained (top/bottom). This helps new messages to be automatically displayed when, for example, switching back to the Inbox.
-   Disabled the use of scroll-position when switching from/to raw message display modes.
-   Removed `Note:` header previously generated for some messages when printing.
-   Added boolean preference (`MmCrossMessageContentIDsAllowed`) for users wanting to disable the ability to reference parts of other messages within a message.
-   Fixed bug in handling of “None” groups (most often triggered by the arrival of new messages).
-   Fixed bug which caused most attachments to be assigned the generic `application/octet-stream` MIME type.
-   Fixed bug in the account import from Apple Mail which could lead to MailMate terminating when trying to compose, send, or delete a message.
-   Fixed bug making sticky flags (such as unread state) fail when the mailbox outline was closed.
-   Fixed problem with partitioned mailboxes when changing the partitioning value (messages were not moved between submailboxes).
-   Fixed various issues with queries which could result in an incorrect set of messages for some smart mailboxes.

## Revision 3271 (Thursday, March 14, 2013) — Version 1.5.3

This is primarily a bug fix release. The only new feature is a hidden preference to customize the “On ... John Appleseed wrote:”. This can be done as follows:

```
defaults write com.freron.MailMate MmReplyWroteString -string 'On %e %b %Y, at %k:%M, ${from.name:${from.address}} wrote:'
```

The above is the the same as the default. The placeholders for date and time are the same as described in the manual page for the `strftime` function. The following describes this function in the Terminal:

```
man strftime
```

### Bug fixes

-   Fixed decoding bug related to a japanese character set.
-   Fixed hang related to the recently added “None” operator for configuration of smart mailboxes.
-   Fixed bug related to None queries. Smart mailboxes were not always properly updated when switching to/from “None”.
-   Fixed bug causing any/all changes in the smart mailbox editor to not take immediate effect.
-   Improved parsing of From headers like this: “Foo bar <foo@bar.com> (Comment)”
-   Address completions no longer include entries like this: “foo@bar.com <foo@bar.com>”
-   Fixed problem with disabled toolbar menu items for layouts involving the thread arcs view.
-   Fixed bug triggered on 10.6 related to non-local address books.
-   Fixed `emate` to handle attachments properly.
-   Fixed the extended URL documentation to include a missing `tell application MailMate` prefix.
-   Changed shortcut for the Activity Viewer from ⌘0 to ⌥⌘0 (matching Apple Mail in 10.7/10.8).

## Revision 3255 (Monday, February 4, 2013)

-   Implemented `replyList:` selector. It can be used to reply to a mailing list disregarding any other message headers.
-   Added `replyList:` and `send:` to manual page with key binding selectors.
-   Workaround for mis-encoded japanese messages (`iso-2022-jp`): When conversion fails (using `iconv`) MailMate skips to the next line and continues the conversion.
-   Fixed replying to inlined PGP encrypted messages. The decrypted text is now used for the reply.
-   Now strips the PGP parts when replying to an inline PGP signed message.
-   Fixed stability problems with encrypting messages with attachments (both OpenPGP and S/MIME).
-   Shows a warning before opening the Address Panel in the composer if MailMate is not allowed to access Contacts on Mountain Lion.
-   Uses bold font for a collapsed message with one or more descendants (when collapsed).
-   Added `maxNumberOfRetries` as an optional key for `Sources.plist` and `Submission.plist`. This can be used to extend the number of retry attempts when connections are very slow. Each retry attempt doubles the time out value used for the connection. The default is 2.
-   Distortion improved a bit: Now distorts headers when viewing multiple messages. HTML is still not distorted.
-   Some code added to track down a bug where MailMate tries to send the same message twice (MailMate still aborts when this happens.)

## Revision 3239 (Wednesday, January 30, 2013)

### New mailbox search option

Added “None” as an alternative option for matching on mailboxes (in addition to “Any” and “All”). This enables one to easily construct searches like “All messages in mailbox A, but none of the messages in mailbox B or C.”.

### New mailbox related selectors for custom key bindings

New selectors for custom key bindings to be able to change tags on all messages of the currently displayed mailbox (or search result). Here is an example marking messages as read/unread:

```
"1" = ( "mailboxToggleTag:", "\\Seen" );
"2" = ( "mailboxSetTag:", "\\Seen" );
"3" = ( "mailboxRemoveTag:", "\\Seen" );
```

Also added a new selector to expunge (permanenly delete) any messages marked as `\Deleted` in the currently displayed mailbox (or search result). This can be used to make MailMate behave like a traditional IMAP email client. Here is an example:

```
"D" = "expungeDeletedMessages:";
```

To make that work well then you also need to display `\Deleted` messages for all mailboxes. Until a better solution has been implemented then you can do as follows:

```
defaults write com.freron.MailMate MmShowDeletedMessages -bool YES
```

Feedback is welcome.

Note that the manual pages have been updated to include a list of all available keybinding selectors (in the appendix).

### Other changes

-   Fixed critical bug in the recent addition of a “Reply to ...” menu item in the headers view. The menu item can be used to reply to a single person when a message has multiple recipients. Unfortunately, the sender (the “From” address) of the message was always added as a recipient of the new message and this was not visible until after sending the message.
-   Improved the handling of replying to messages sent by one self. MailMate should now more reliably create a follow-up message instead of a reply.
-   Now offers to force delete an account if it contains any messages not uploaded to the IMAP server (most often unsent drafts or sent messages).
-   Increased padding for thread arcs in order to make it easier to see long vertical arcs.
-   Workaround for a layout related crash bug.
-   Fixed crash bug triggered when sending a message while still editing a recipient field.
-   Fixed crash bug triggered when quitting with more than one message pending submission due to `MmSendMessageDelayEnabled` (and one chooses to send them when an alert is shown).

## Revision 3218 (Monday, January 21, 2013) — Version 1.5.2

-   Added “Reply to ...” to the context sensitive menu of addresses in the headers view.
-   Improved handling of OpenPGP and S/MIME. Now MailMate properly handles signed/encryped body parts in `multipart/mixed` MIME messages.
-   For the Japanese users of MailMate: Now respects the first/last name ordering of individual contacts in the Address Book (Contacts on Mountain Lion).
-   Inlined images are now rotated according to EXIF data in images (Mountain Lion only).
-   Shows an alert when trying to add an entry to Contacts when access to Contacts is not allowed (by user preference). Previously this silently failed (Mountain Lion only).
-   Enabled auto-linking for the Markdown converter.
-   Updated to use Growl framework version 2.0.1.
-   Added some optional toolbar buttons, a “Flag” toggle and a “Reply All” button.

Added `sendAndArchiveParent:` and `sendAndMoveParentToMailbox:`selectors which can be used for custom key bindings. Also added an optional “Send and Archive” button for the composer toolbar. It is not displayed by default. Note that when doing “Send and Archive”, the archived parent is automatically marked as read (if not read already).

Added a new submenu to the Mailbox menu named “Synchronization Schedule”. It allows the user to explictly configure how often each mailbox is synchronized, including a “Connected” item which means that the mailbox is treated like the INBOX, that is, IMAP IDLE is used. It only makes sense to have at most 3 “Connected” mailboxes since there is not yet a GUI to increase the number of simultaneous connections (it can be configured manually though).

It is now possible to add custom headers to the composer using a hidden preference. For example, the following can be used to add a priority header to outgoing messages:

```
defaults write com.freron.MailMate MmAdditionalComposerHeaders "( { headerName = 'X-Priority'; type = 'plain'; } )"
```

Give the header a value of 1 and it'll get a “high” priority.

### Experimental handling of `winmail.dat` files

TNEF (Transport Neutral Encapsulation Format) is a proprietary attachment format which is generated by some Microsoft products. The resulting files are often named `winmail.dat`. This version of MailMate can automatically extract the files within TNEF attachments using the `tnef` command line tool, but this is not (yet) distributed with MailMate and you should consider it a very experimental feature. If you have MacPorts installed then you can get `tnef` as follows:

```
sudo port install tnef
```

Then launch MailMate and try to open a message with a TNEF attachment (MIME type must be `application/ms-tnef`). It has only been tested on a few emails. Feedback is welcome, in particular if you have messages for which it fails to work correctly.

### IMAP

-   Fixed bug in the handling of Message-IDs with double-quotes when searching for a message on servers without support for UIDPLUS.
-   Workaround attempt for the Davmail Exchange->IMAP gateway server.
-   Fixed handling of IMAP LOGIN command. It did not always work if the username needed to be quoted.
-   Fixed problems with handling ``\` and``"` in the IMAP code.
-   Improved feedback when deleting an IMAP mailbox fails, for example, some servers do not allow deleting standard mailboxes. MailMate now offers to cancel the deletion.
-   Workaround for IMAP servers which (erroneously) report a negative UIDVALIDITY value (it is handled by skipping the minus sign).

### Various Fixes

-   Fixed a bug in the SMTP code which could result in partially sent messages.
-   No longer terminates when creating a new message while no identities exist.
-   Fixed problem with the configuration of reply-shortcuts in the Composer preferences pane.
-   Fixed problem with Growl notifications which were no longer “clickable”. Apparently a problem introduced by Growl 2.
-   Fixed bug in format string code, for example, `${from.name.first}` could fail in certain contexts.
-   Changed quoted printable encoding to never end with a `=` character. These were displayed on iOS. (Quoted printable is mainly used for signed messages. In general, MailMate tries to avoid the use of quoted printable.)
-   Fixed bug in the handling of the enter key (numeric key pad) in custom key bindings.
-   Workaround for messages where the `Content-Transfer-Encoding` header is the same as the charset of the message (the origin of these emails are unknown). Falls back to 7bit encoding instead in this special case.
-   Workaround for making iOS devices accept S/MIME signed messages from MailMate. There are still issues with signed+encrypted messages.
-   Fixed a couple of layout problems.

## Revision 3157 (Wednesday, December 19, 2012)

-   Fixed various issues with tags related to IMAP keywords being case insensitive. Previously, some tags did not seem to stick when applied to messages, but the real problem was that MailMate did not recognize the tags due to differences in casing.
-   Fixed a bug in `mailto:` handling when sending a message with attachments (via AppleScript).
-   Now allowing the Bcc header when using `mailto:` with trust.
-   Added manual page about the `mailto:` URL scheme.
-   Added new emate command. Its only functionality, for now, is to be a convenient wrapper for the `mailto:` URL scheme (thanks to Mathias Holm for the original script).
-   Updated manual page about emate.
-   Improved warning for “untrusted recipient key” when encrypting messages using OpenPGP.
-   Fixed the broken look of multiple attachments to be a proper table.
-   Fixed problem with dynamic submailboxes disappearing too early, for example, when marking last message read in an submailbox of unread messages.
-   Fixed an issue with the `searchAllMessages:` and `mailboxSearch:` selectors (available for custom key bindings).
-   Fixed: The new line wrapping of headers triggered a bug in the SMTP code. A message with multiple Bcc recipients could make the SMTP thread hang in a busy loop.

## Revision 3142 (Friday, December 14, 2012)

-   Fixed problem with code signing which made MailMate repeatedly ask for access to the keychain (it did not affect all users).
-   Fixed problem with any malformed HTML messages containing a `cid:` URL with no value.
-   Tweaked the “Prefere Plain Text” feature such that a HTML body part is automatically shown if the plain text body part is empty.

## Revision 3139 (Wednesday, December 12, 2012) – Version 1.5.1

### Tagging

This is the first version of MailMate with a user interface for tagging. Details can be found in the manual, but you can easily try it out by simply hitting `t` in the message viewer. Also note the new “Tags” preferences pane.

The implementation of tags in MailMate is based on IMAP keywords.

### Other changes

-   When failing to encrypt (OpenPGP) a message to an untrusted recipient then “Trust Once” is now provided as an option (when trying to send).
-   Untrusted S/MIME certificates are now editable (when viewed using “Show Details”), that is, the trust settings can be changed.
-   Holding down ⌥ can be used to expunge selected messages immediately (instead of moving them to the trash). An alert is shown which can optionally be disabled.
-   Added the ability to change the type of mailbox count when multiple mailboxes are selected.
-   Suppression checkmark added to the window shown for “Empty Mailbox” actions (available for “Deleted Messages” and “Junk”).
-   Improved handling of first responder state when adding/removing views. This is an improvement for both tagging and searching, for example, after tagging the focus returns to the view which had focus before opening the tags editor.
-   Now wraps headers very nicely at 78 using field specifiers to properly tokenize headers. Lines can be longer if unable to wrap nicely, but lines are never longer than 998 characters. These are
-   Workaround for Gmails implementation of IMAP keywords which allows the ']' character. This is non-standard, but MailMate now handles it gracefully.
-   Refactored part of the window layout system.
-   Fixed IMAP bug triggered when APPEND'ing messages with non-standard flags on a server with no support for non-standard flags.
-   Fixed crash bug when using `mailto:` with attachments (via AppleScript).
-   Fixed OpenPGP encryption-related crash bug.

This release also includes a workaround for a problem under 10.7.5 which would make MailMate and the authorization interface to the keychain hang when changing the trust settings of a server certificate. The problem is related to code signing.

## Revision 3095 (Thursday, November 8, 2012) — Version 1.5

This section covers all changes since version 1.4.3 of MailMate which was released as a public beta in July. It is followed by a section describing the changes since the latest public release which was version 1.4.2 (r2818/r2819).

Note that the certificate used for code signing has changed since version 1.4.2 and you are going to be asked about allowing MailMate to access passwords in the keychain. This should only happen once for each password.

Version 1.5 is the first version of MailMate with support for OpenPGP and S/MIME. To be able to view/verify and/or compose messages using S/MIME or OpenPGP you need to enable it in the Security preferences pane (⌘,).

### Various features/changes

-   Updated to Growl Framework 2.0. This means MailMate now supports Mac OS X Notifications on Mountain Lion
-   Added support for colored flags (compatible with Apple Mail). This also works over IMAP for any server with support for custom IMAP keywords (the majority of servers). The primary flag color is now red in order to match Apple Mail. Default key bindings for setting colored flags is capital F followed by 1-6 (no visual support for setting these flags yet).
-   “Download Linked File” (or Image) is now available in the context sensitive menu of the message view.
-   Improved performance of HTML to text conversion by replacing `html2text.py`with `libxml2`.
-   Removed all dependencies on the BWToolkit framework. The related changes include a new status bar below the mailbox outline.
-   Added a hidden preference (`MmIgnoreDeliveryAddresses`) to ignore delivery addresses when deriving the identity to be used for a reply. Removed the `MmAlwaysTrustDeliveryHeaders` hidden preference.

### IMAP

-   Fixed a problem related to case sensitive IMAP servers. It only affects installs of Mac OS X on case insensitive disks, but that is also the default. MailMate would terminate when trying to move messages between mailboxes which only differed in casing.
-   Workaround for Gmail servers replying with `* BYE \[UNAVAILABLE\]` for a login attempt.
-   Workaround for servers failing to provide an EXISTS response after APPEND (experienced with an IMAP server named SmarterMail).
-   Fixed various issues regarding saving messages in the drafts folder on an IMAP server. It now has better performance and it may, indirectly, affect problems with some non-standard servers (Gmail) with respect to the location of sent messages.

### Bug fixes

-   Workaround for a bug in OS X 10.8.2 triggered when using `AESendMessage` to send AppleScript events. This affected users of SpamSieve. Every message sent to SpamSieve would hang and then time out (after 2 minutes) making MailMate seem extremely slow.
-   Local references in HTML messages now work correctly (scrolling to the correct location within the message).
-   Fixed placement of caret when selecting “No Signature” in the composer (when using “Top” posting).
-   Updated `sundown` (Markdown converter) to no longer auto-enumerate numbered lists since that does not work well for the plain text part of emails.
-   Forwarding a message with a misplaced calendar attachment (`text/calendar`within `multipart/alternative`) now works correctly, that is, the calendar item is attached to the forwarded message. (This is a workaround for a bug in other email clients.)
-   Fixed “New Message” bug when using the dock icon menu: Window was not taken to front.
-   Fixed visual glitch in the date column of the messages outline when expanding/collapsing message threads.
-   Fixed visual glitch when opening/closing the find banner view (⌘F).

### Debug

Three new debug variables have been added to make it easier to solve various problems:

```
defaults write com.freron.MailMate MmDebugSecurity -bool YES
defaults write com.freron.MailMate MmDebugSend -bool YES
defaults write com.freron.MailMate MmDebugAddressBook -bool YES
```

The first one may be of interest for anyone trying out the new support for S/MIME and OpenPGP. The others are mainly introduced to track down problems reported by a few users.

## Revision 2980 (Thursday, July 26, 2012) — Version 1.4.3

This version of MailMate was only released as a public beta. The following covers all changes between versions 1.4.2 and 1.4.3.

### Various features/changes

-   Prepared for Gatekeeper (Mountain Lion security feature) by signing MailMate with a Developer ID certificate.
-   Experimental decryption/verification of PGP messages both with and without the use of MIME body parts. Note: Currently, decrypted data is always added to the database. See the manual pages about hidden preferences for details (and how to enable this feature).
-   Added an action named `selectWithFilter:` to be used for key bindings. It can be thought of as a generalization of `selectAll:` and `deselectAll:` since it can be used to select any set of messages matching a filter. See the manual page about custom key bindings for more information.
-   When using “Format ▸ Show Fonts” it is now possible to alter the table line height used in the mailbox outline and the messages outline. For the record, the changeable fonts are: Mailbox outline, messages outline, message view (normal and raw mode font), and composer font.
-   Dragged messages (to the Finder) are now named using their subject. Configurable using hidden setting: MmFilenameFormatString.
-   Dragging messages out of MailMate is now handled better using the UTI `public.utf-name`.
-   Added ⌥F2 shortcut to open the context sensitive menu in the editor of the composer. The primary use case of this is to easily see and select spelling suggestions. This functionality can also assigned to a different key using custom key bindings (the selector is named `showContextMenu:`).
-   No longer displays multi-page PDF documents inline (done by heuristically looking for the number of pages in PDFs).
-   Added a “Show Fonts” button to the General preferences pane in order to make it a bit more obvious that font changes are possible.
-   Added help button to the Counters preferences pane.
-   Added a cancel button (small x in the right side) to the text field used by search conditions (only for some comparison methods).
-   Inlined images (`cid:`) in HTML messages can now be dragged.
-   Now parsing HTML body parts for the database when it differs (considerably) from the plain text body part alternative (or when such alternative does not exist).
-   Parsing of `Message-ID` headers now allows spaces in the domain part since such headers are generated by some buggy software.
-   Now validating the domain part of the `Message-ID` created for new messages. Replaced by `mailmate-app.com` if it does not validate.
-   No longer logs warnings about missing subparts of MIME multiparts when only headers have been fetched.
-   Threads in search results are now auto-expanded when fewer than 500 messages are found.
-   Add key bindings file with Postbox key bindings (created by Ian Beck).
-   Now remembers scroll position for selected message(s).
-   Changed the composer layouts: They are now horizontal/vertical variants of the preview layout. By default the preview is shown when markup languages are enabled, but it can always be explicitly enabled/disabled (⌃⌥⌘P).

### Optimizations

Multiple aspects of MailMate have been optimized. This should be noticeable for most users, in particular users with a large number of messages and/or mailboxes. Optimizations include:

-   faster startup time
-   faster searches (in particular when searching addresses, subjects, or body text)
-   messages outline sorting (in particular when sorting on addresses or subjects)
-   synchronization of IMAP accounts
-   faster when moving forward/backward in search history

### Completion of recipient names/addresses

-   MailMate now supports searching LDAP servers when autocompleting names/addresses in the composer window, but there is currently no GUI for this feature. Read more about it in the manual page about “Hidden Preferences”. Feedback is welcome.
-   Added a comma to all “lastname, firstname” completion suggestions.
-   Fixed bug in the sorting of possible completions shown.

### Extended `mailto` URL scheme to be used via AppleScript

It is now possible to create new messages in MailMate with attachments using AppleScript. It is also possible to send these messages without bring MailMate to the front.

For a long time, MailMate has supported the `mailto` URL scheme. For example, the following link creates a message with recipient, subject, and default body text:

```
mailto:me@example.com?subject=Test&body=Body%20text
```

It can be used within HTML pages as a link, but it can also be called directly, for example, using the `open` command in the Terminal:

```
open "mailto:me@example.com?subject=Test&body=Body%20text"
```

Using the `open` command it is also possible to specify the application to be used when creating the message:

```
open -a MailMate "mailto:me@example.com?subject=Test&body=Body%20text"
```

Otherwise, the default email application is used (this can be configured in the General preferences pane in Apple Mail or MailMate).

MailMate now extends the `mailto` syntax to include some additional special parameters. These are `attachment-url` and `send-now`. For security reasons they are ignored except if the URL is provided via AppleScript. It can be done as follows using a single line in the Terminal:

```
osascript -e 'open location "mailto:me@example.com?subject=Test&body=Body%20text&attachment-url=file:///full/path/to/file.txt&send-now=yes" with trust'
```

Note the important `with trust` part of the AppleScript command. This is needed to make sure MailMate does not ignore the special parameters.

In practice, all of this means that MailMate can now be integrated with applications which need to send messages with attachments. Examples for iCal and BusyCal are provided, but it is currently a bit tricky to use them since integration requires the developers of the applications to add scripts for MailMate (and don't ever expect that to happen for iCal). For now, the scripts can be enabled as described below using the Terminal (assuming all applications are in `/Applications`).

iCal:

```
mv /Applications/iCal.app/Contents/Resources/Scripts/Mail.scpt /Applications/iCal.app/Contents/Resources/Scripts/MailBackup.scpt
ln -s /Applications/MailMate.app/Contents/SharedSupport/Other/iCal/Mail.scpt /Applications/iCal.app/Contents/Resources/Scripts/
```

UPDATE: The above does not work on Mountain Lion since Apple no longer uses the `Mail.scpt` file. It is unknown whether or not a workaround exists.

BusyCal:

```
mv /Applications/BusyCal.app/Contents/Resources/Scripts/MailAttachmentScript.scpt /Applications/BusyCal.app/Contents/Resources/Scripts/MailAttachmentScriptBackup.scpt
ln -s /Applications/MailMate.app/Contents/SharedSupport/Other/BusyCal/MailAttachmentScript.scpt /Applications/BusyCal.app/Contents/Resources/Scripts/
```

UPDATE: The above does not work for BusyCal 2.0. It might work if the script is placed in the following location (not tested): `/Volumes/Mountain\ Lion/Users/benny/Library/Application\ Scripts/com.busymac.busycal2/com.freron.MailMate.scpt`

Note that updating iCal/BusyCal or moving MailMate is going to break the symbolic links created above.

An example script for LaunchBar (nightlies) is also included. It should be used with the “Preferences ▸ Actions ▸ Options ▸ Create Emails with” preferences item. The script is located here: `MailMate.app/Contents/SharedSupport/Other/Launchbar/SentHandlers.scpt`. LaunchBar should then allow you to create an email with any selected files attached (selected in the Finder).

### IMAP

It is now possible to manipulate the use of namespaces for each IMAP account. This is important for some users, especially those needing to specify what is known as an IMAP prefix in most email clients (most often this is not necessary). The feature is described in the chapter about “Hidden Preferences” in the manual.

Gmails IMAP server does not report changes to IMAP keywords/flags including its read state (when watching for changes in the INBOX). As an experimental workaround, MailMate can now be told to regularly check for keyword changes. You can try it by running the following command in the terminal:

```
defaults write com.freron.MailMate MmEnableKeywordsCheckInIDLEForGmail -bool YES
```

Other IMAP related changes are:

-   Improved heuristic for guessing standard IMAP mailboxes when they have not been explicitly set.
-   Moved “Edit Subscriptions...” to the IMAP account editor.
-   Fixed issue with “Edit Subscriptions”. It did not work correctly if the IMAP username/hostname of the account had been changed.
-   Fixed behavior for IMAP servers advertising UIDPLUS without support for UIDs in APPEND/COPY responses.
-   Workarounds for Courier 2004 server (GoDaddy). One workaround for flags which the server does not report correctly immediately after changing them and another workaround for UIDs not being properly detected after an APPEND/COPY due to failed SEARCHes for `Message-ID`s. Also fixed a more general potential message duplication problem when appending.
-   Improved behavior for servers (Gmail) with sudden NO rejections on fetch queries combined with termination of the connection (BYE).
-   Fixed the subscriptions editor to also use the namespaceResponse hidden preference.
-   Reduced maximum IMAP command line length to work better with servers with a relatively small limit on command line length.
-   Fixed an issue with uploading messages (APPEND) triggered when one of them (and not the first one) had no or non-standard IMAP keywords.

### Experimental dual mode

Introduced a new layout class to handle multiple modes in a window. This is used to provide a dual-mode layout in which one can switch between list mode and message mode. To control it, a key binding is needed for `nextMode:`. To enable this layout, you need to do the following:

```
mkdir -p ~/Library/Application\ Support/MailMate/Resources/Layouts/Mailboxes/
cp /Applications/MailMate.app/Contents/Resources/Layouts/Mailboxes/dualMode.plist ~/Library/Application\ Support/MailMate/Resources/Layouts/Mailboxes/
```

And then edit `dualMode.plist` by removing the `enabled = 0` line.

### Bug fixes

-   Fixed problem with messages erroneously being shown as part of the currently displayed mailbox (messages for which IMAP keywords had changed).
-   Fixed: For convenience dock/menu-counts are shown when editing counters even if they are 0. Unfortunately the 0-counters were not removed when closing the preferences window.
-   Now properly updates the search result when selecting something in the popup for an 'is/is not' comparison.
-   Better detection of URLs when <> and punctuation is involved (when converting from canonical text to HTML).
-   Fixed sorting of the Spam Score column in the messages outline.
-   Fixed some minor memory leaks related to internal conversion of property lists.
-   Fixed problem with repeated autosave requester after rebuilding database.
-   Changed wording in the headline of the password requester to avoid confusion about the username used for the account.
-   Fixed various issues/bugs related to the history of searches.
-   Fixed termination of MailMate triggered when forwarding certain types of messages.
-   Fixed termination of MailMate related to clicking on items in the headers view.
-   Changed how `cid:` references are handled. It should now work better with non-unique or malformed `Content-ID` headers. In practice, certain HTML messages with embedded images are now shown correctly even though they contain bad `Content-ID` headers.
-   Fixed termination of MailMate when using the “File ▸ Open Message” menu item. It was not correctly enabled/disabled.
-   Fixed termination of MailMate related to “Show Fonts”.

## Revision 2818 (Tuesday, March 27, 2012) — Version 1.4.2

Version 1.4.1 of MailMate unfortunately introduced a performance bug which under certain circumstances can make MailMate practically unusable (high CPU and disk usage). The problem is particularly bad with large mail stores. Thanks to the users helping identify and solve this issue. It is strongly recommended to update to version 1.4.2. (Note that version 1.4.2 works on Mac OS X Leopard as well.)

### From address derivation for email aliases

Derivation of the `From` address for replies has been changed. Until now it has been based on a heuristic using the `X-Original-To` header and other similar headers, but examples from users have shown that this approach does not work well in general. As a replacement for the heuristic, an optional account setting named “Address Pattern” has been introduced. It is disabled by default. The value for this option must be a regular expression which describes the format of any aliases for the account. Read more about this in the account settings chapter in the Help Book (a help button has also been added to the account settings window).

### Change focus using key bindings

Introduced `makeFirstResponder:` for key bindings. This can be used to bind a key to directly activate a view. The identifiers for the views can be found in the layout files, but here are the most likely use cases:

```
"o" = ( "makeFirstResponder:", "mainOutline" );
"m" = ( "makeFirstResponder:", "messageView" );
"M" = ( "makeFirstResponder:", "mailboxesOutline" );
```

### Other changes

-   Improved headers editor for recipient addresses in the composer. Previously, multiple tokens were created if pasting text in the middle of an existing token or if tab'ing when the cursor was in the middle of an existing token.
-   IMAP mailbox states are now cached. This makes scrolling in the mailboxes outline smoother.
-   Bounces “Download” folder instead of opening it when saving an attachment.
-   Fixed “Edit ▸ Find ▸ Mailbox Search” menu item. It now works correctly when selected using the mouse (previously it switched to “All Messages”).

## Revision 2802 (Wednesday, March 21, 2012)

**IMPORTANT:** This is the last release of MailMate which supports Mac OS X Leopard (10.5). This affects roughly 2% of the current user base (even less if including Mac App Store users) which is about the same as the number of Mac OS X Mountain Lion users (10.8). This revision of MailMate disables the automatic software update when running MailMate on Leopard.

## Revision 2801 (Thursday, March 15, 2012) — Version 1.4.1

### Customizable swipe gestures

Trackpad gestures are now supported by MailMate. It has been implemented with customization in mind as described in the following. The 4 standard swipe directions, left, right, up, and down, are transformed into key down events with the unicode characters `\U2193`, `\U2190`, `\U2192`, and `\U2191` (→ ← ↑ ↓). It is a bit of a hack, but it allows great flexibility with respect to what can now be done with gestures. By default, standard key bindings have been extended as follows:

```
"→"      = "nextMessage:";
"←"      = "previousMessage:";
"↑"      = "previousThread:";
"↓"      = "nextThread:";
"^→"      = "nextUnreadMessage:";
"^←"      = "previousUnreadMessage:";
"^↑"      = "previousUnreadThread:";
"^↓"      = "nextUnreadThread:";
```

The defaults may be changed (feedback is welcome), but in any case you can change it yourself using a custom set of key bindings. Swipe to archive, switch mailbox, delete messages, or whatever you like. As indicated by the defaults, it is possible to combine swipes with the use of modifier keys.

### Other new keybindings

Based on a user request, the following actions are now available for binding keys to expand/collapse messages or threads in the messages outline (when organizing by thread):

```
expand:
collapse:
expandThread:
collapseThread:
```

In addition to `toggleTag:`, it is now also possible to explicitly set or remove tags:

```
setTag:
removeTag:
```

### Improvements

Most importantly, a number of optimizations should result in faster startup time, smoother scrolling in the messages outline, and faster display of messages, in particular, for large message stores.

-   Added preferences for when to automatically mark messages unread (see the “Composer” preferences pane).
-   Added support for named alternative email addresses (details in the chapter about account settings in the manual).
-   Updated Markdown converter (`sundown`). It is now better at handling changes in quote-level although this is non-standard Markdown behavior. Also fixed handling of quoted code blocks which would often fail when indented code blocks were in use.
-   Better detection of whether Markdown can be used for replies. Markdown is now enabled whenever the text replied to is known to be Markdown or does not contain Markdown markup.
-   Added the use of an external script to convert HTML to plain text (Markdown) when needed for replies or forwarded messages.
-   Now warns when trying to send a message from an account with no SMTP server configured (instead of silently not sending).
-   Improved handling of links in the composer. No longer opened on single click. Hold down command to open a link or use the menu item.
-   Drag'n'drop of email addresses between fields behaves as one would expect. The GUI feedback is still wrong (inverted). Hold down option or command to copy.
-   Added “Reset Usage History” button in the Signatures preferences pane. MailMate now also automatically uses the first configured signature (if any exists) when a signature cannot be derived otherwise.
-   IMAP server name and username settings can now be changed when editing account settings.
-   Improved IMAP code for handling non-UIDPLUS servers.
-   Changed how deleted messages are handled internally. Some actions should be (feel) faster now.
-   Added columns for “Date Sent”. (Currently only works properly for new messages or if rebuilding the database.)
-   Indentation in the messages outline column has been improved (the one with triangles). In particular, there is no indentation when not organizing by thread.
-   Improved default columns shown for standard mailboxes under SOURCES (such as showing “To” instead of “From”).
-   Improved mailbox outline display performance.
-   Improved performance of resetting messages (“Message ▸ Reset...”).
-   Better handling of address-only messages when completing addresses.
-   Improved parsing of spam status related headers.
-   No longer necessary to close the Quick Look panel before clicking a new Quick Look button.
-   Improved behavior when moving signature to top after adding text to the top of the message. It is now placed under any text entered and before the “On ... wrote:” line.
-   Specialized handling of a `text/calendar` body part when it is part of `multipart/alternative` (created by buggy software). It is now shown as an attachment when viewing the `text/plain` or `text/html` body part.
-   Import Messages: Option to import into the destination mailbox even if messages are found within some hierarchy of folders.
-   Improved importing of mailbox folders created by Lion Apple Mail.
-   Added enclose-related words to the default attachments check.
-   No longer trusts `X-Original-To`-like headers when creating new messages if they come before any `Received` headers (this matches how replies work).
-   Improved From address derivation. Now any `X-Original-To` and `X-Delivered-To` headers are ignored if they come _after_ any `Received`headers.
-   Improved derivation of From address for mailing lists where the `X-Original-To`header was not useful. Now it works if the real address is only found in the `for`part of a `Received` header. These parts of `Received` headers are now scanned for known addresses.
-   Attachment links are now draggable (and not just the attachment icons).
-   Introduced hidden preference for setting the default type for mailbox counters: `MmMailboxDefaultCountKey`. Set it to `none` to disable counting by default.
-   Improved drag'n'drop of messages. Now inserts titled URL in RTF documents and a plain link in plain text documents. Also uses so-called promised files instead of real files.

### New hidden preferences

The following three boolean hidden preferences values are now available:

```
MmMoveSentRepliesToMailboxOfRepliedMessage
MmAddressCompletionMailbox
MmNonPrivateNamespacesEnabled
```

The first one is self-explanatory, the second one can be used to control which messages are used for completion of email addresses in the composer, and the last one can be used to enable experimental support for non-private IMAP namespaces. Feedback is welcome, but none of these features should be considered complete.

### Fixes

-   Fixed bug which resulted in forwarded messages being marked as answered.
-   When opening a message using a menu bar counter menu item or by clicking on a notification then the message is opened in the main window. Previously it often failed, because of an active search (which is now cleared instead).
-   Fixed various problems related to circular message references including self-referencing messages. This includes crashes involving the `maximum_value_for_header` function. It has been solved by always breaking cycles when threading messages.
-   Various issues fixed with regard to mailbox dragging/reordering.
-   Fixed issue triggered by receiving `text/enriched` attachments which are really msword documents (generated by a buggy email client).
-   Fixed bug related to messages with `message/rfc822` as content type in the root body part.
-   Fixed sorting of Read state column (blue dot).
-   Fixed parsing of (yet another) non-standard From address variant: `address (name <address>)`.
-   Fixed issue with the hidden preference to prepopulate the Bcc header.
-   Fixed handling of `mailto:` URL scheme when used to launch MailMate.
-   Fixed crash bug when exiting MailMate with one or more open mailbox editors.
-   Fixed crash bug which could be triggered by recipient addresses containing “single quote” marks.
-   Fixed crash bug which (under special circumstances) could be triggered when using “Edit as New Message” followed by removing an attachment.
-   Workaround for problem with 'Gordano Messaging Suite IMAP4 server v15.02.3689'.
-   Workaround for server which did not return a hierarchy delimiter when requested to do so (Surgemail).
-   Fixed pasting URLs copied from a Webview. Previously the name was pasted instead of the URL.
-   Added boolean defaults value MmEncodeFullSubjectLines. This can be used as a workaround for problems with buggy websites (like https://www.followup.cc/).
-   Now uses the correct SMTP settings when sending a message with a derived email address.
-   Now properly handling draft messages which were never saved, but which were still part of the database because of a crash. This fixed bug has the side-effect that when rebuilding a database empty messages are likely to appear in the Drafts mailboxes.
-   Fixed an IMAP namespace problem. Triggered when multiple namespaces of a given type are reported by a server.
-   More robust handling of IMAP servers unable to return the bodies of existing messages (workaround for MS Exchange bug).
-   Now able to handle 0-sized IMAP messages (a problem which is rare and difficult to reproduce).
-   Fixed behavior when detecting changed UIDVALIDITY value for an IMAP mailbox. Previously it could fail if the mailbox contained messages with no UIDs.
-   Changed handling of IMAP messages with empty headers and body.
-   Fixed default state for ignoring server subscription states (it was supposed to be on by default, but this was not the case).
-   Updated default IMAP server used for iCloud IMAP accounts (`imap.mail.me.com`) when importing accounts from Apple Mail.
-   Workaround for mailbox creation problem with buggy Yahoo IMAP server.
-   Fixed SMTP settings in the IMAP account settings window to properly show an empty string.
-   Improved date parsing such that some problematic `Received` headers are skipped (essentially a workaround for headers generated by a Gmail migration).

## Revision 2651 (Saturday, December 17, 2011) — Version 1.4

Until this version of MailMate, during startup the user has been notified of any previous crashes and then offered the opportunity to submit them to Freron Software. This has been a very useful feature and crashes are now quite rare in general due to the fixes which have followed the crash reports sent. The feature still exists, but it has been simplified. The Preferences (⌘,) has a new setting where MailMate can be told to automatically send crash reports quietly. This is disabled by default, but you are automatically asked (once) to enable it if a crash report is found.

### Reorganized and extended preferences

The Preferences (⌘,) window has been reworked and now contains 7 panes. Previously hidden preferences have been given a GUI and other preferences have been improved. “Software Update” has moved from the MailMate menu to its own pane and it has more detailed settings. In particular, you can configure it to automatically download beta versions of MailMate.

### Markdown support

Markdown support is now available and you can enable it in “Preferences ▸ Composer”. The composer window is then going to include a Markdown-related menu in the status bar. You can read more about it in the Help Book, but essentially it means that you can write your messages in Markdown style and then MailMate is going to generate an HTML body part as an alternative to the plain text (Markdown) body part. Note that the composer has an alternative layout which makes it easier to experiment with this feature (see “View ▸ Layouts” when using the composer).

### IMAP/SMTP

For new users, IMAP server subscriptions states are now ignored by default. This can be changed in the “Edit Subscriptions...” interface. For existing users (that is, existing databases) the default is still to respect server subscriptions.

The quest continues to support as many IMAP servers as possible. Some servers are more challenging (euphemism for buggy) than others, and some times servers reveal bugs in MailMate. The following are all of the IMAP related changes:

-   IMAP/SMTP data parsing: Line endings should be so-called CRLF according to the standards, but MailMate now handles CR's without LF's as gracefully as possible (this fixes an iCloud IMAP server problem).
-   Workaround for bug in MS Exchange IMAP server (wrong result for UID SEARCH commands).
-   Server reachability is now handled a bit differently in an attempt to fix some issues with both IMAP and SMTP.
-   Fix for problem with an MS Exchange IMAP server where the server provided information which was not requested for the destination mailbox of a move command (this is legal behavior, but it was not expected by MailMate in this special case).
-   Introduced a “failed” stated for IMAP accounts which makes it easier for MailMate to avoid taking mailboxes offline unless explicitly requested by the user.
-   Now accepts differing mailbox hierarchy delimiters returned from LIST and LSUB if one of them is NIL.
-   Automatically ignoring “[Gmail]/Important” for new accounts. Also better at detecting “All Mail” and “Starred” when they are localized.
-   Fixed various issues in the subscriptions editor, including broken filtering. You can now use ⌥ to select/deselect all (filtered) items.

When sending a message fails then a “Try Later” option is now available. It'll retry after 15 minutes and then present the requester again (if it fails again). Each time the retry delay is doubled. When quitting, MailMate notifies the user if any messages are on hold.

If sending while offline then messages are automatically queued for sending when going online again. The state of individual messages can be seen in the Drafts mailbox. Using hidden options it is also possible to delay sending any messages (the delay is measured in seconds):

```
defaults write com.freron.MailMate MmSendMessageDelayEnabled -bool YES
defaults write com.freron.MailMate MmSendMessageDelay -integer 60
```

-   SMTP: Increased end of DATA timeout to 10 minutes to be compliant with RFC5321.

### Database rebuilding

MailMate now automatically offers to rebuild the database if an inconsistency is detected. The user is asked to choose between basing the rebuild on already downloaded messages or basing the rebuild on redownloading all messages. When based on downloaded messages, MailMate tries to maintain the usage history of signatures.

This is a major new feature even though you may never see it. The previous solution was to output an error to the system log and then simply terminate MailMate. It was not very user-friendly and it was difficult to recover manually.

Part of the implementation of this feature means that the UIDs of IMAP messages are now stored in file attributes. Also, moving messages between mailboxes is now done much more efficiently than it was before (on the local disk).

### Other new features

Navigation keys have been for thread navigation (in the Messages menu for now). The corresponding selectors are `next/previousThread:` and `next/PreviousUnreadThread:` and they can be used for custom keybindings if needed. The default keys mirrors the keys for `next/previous(Unread)Message:`with the addition of the control key (⌃).

The From address of a message is now customizable. A “Customize...” menu item has been added to the From-menu. This opens a simple sheet with a text field. The text field features automatic completion based on previously sent messages. Note that the From menu is not shown if only 1 identity is known (configured in accounts), but this is likely not an issue for users wanting to customize the From header.

Another new selector is `scrollPageDownOrNextUnreadMessage:` which can currently only be used by assigning a key using custom key bindings. The idea is to assign it to the space key to make it behave a bit differently with respect to finding the next message (standard key binding simply looks for the next message and not the next unread message).

Two algorithms now exist for the dynamic signatures system. It can be configured using the Terminal as follows:

```
defaults write com.freron.MailMateSimple MmDynamicSignatureMethod -string standard
```

The three possible values are `none` (to disable it), `standard` (the default), and `messageType`. The last one bases its signature guess on whether the message is new or is a reply. This is for users who typically write an initial message with a large signature and then subsequently use a small signature.

-   SpamSieve is not launched before it is really needed, that is, when a message arrives in a mailbox covered by the SpamSieve settings.
-   Dragging of so-called promised files now works with the composer. This means dragging events from iCal to the composer should work.
-   “Edit ▸ Select Duplicates” feature (⌃⌥⌘A). If duplicate messages exist then this command selects anything but the original messages (those known for the longest time). This is a useful feature, but it is likely to be replaced with something more flexible in the future.
-   Added new menu item for resetting messages, that is, remove them locally and then refetch them from the IMAP server (“Messages ▸ Reset...”).
-   Added dock menu item for composing a new message.
-   The default mailbox search terms are now automatically altered if viewing a mailbox with sent or draft messages such that any occurrence of `from` is replaced by `recipient`.
-   Moved Return/Enter to open messages to the standard key bindings (from Gmail bindings). Fixed the Enter key binding to actually work.
-   As an experimental feature, `insertFormatString:` has been added as an alternative to `insertText:` for key bindings. Mainly to allow one to do something like `"x" = ( "reply:", "insertFormatString:", "Hi ${from.name.first},\n\n");`.
-   Updated documentation.

### Fixes

-   Fixed bug related to creating a new message with an attachment, saving it, and then removing the attachment. In some cases the attachment was never really removed (the problem was related to autosaving).
-   Fixed bug in reply code when replying to multiple senders. Most of the time only 1 sender was included in the To-header.
-   Fixed messages outline to keep the selected row displayed when changing sorting column.
-   Blind fix to an issue which only occurs for a single user with a very large number of configured accounts.
-   Fixed problem with Growl 1.3.x on Lion. Also updated the Growl framework included with MailMate to version 1.2.3. Cannot just upgrade to the 1.3 framework since it does not work for 10.5.
-   The state of the headers view (disclosure triangle) is now also saved in single message viewer windows.
-   Fixed headers view menu item such that “New Message to...” works when only an email address is available. Also added “Reply to...” which is useful for emails with a reply-to field which would otherwise be used by default.
-   Improved debug output for signature derivation.
-   Fixed potential crash bug when new messages are deleted immediately (server side).
-   Fixed bug in parsing of Thunderbird account preferences.
-   Improved default identity for a new message when messages outline sorting has the newest message at top.
-   Fixed crash bug when parsing a malformed `message:` URL.
-   Improved navigation and sorting of threads when having newest message at top.
-   Now showing registration window when trial time has ended (30 days of active use), but it is still possible to skip it and continue under the restriction of only being able to send 2 messages per launch.
-   “Edit as New Message...” now maintains the original From header even if the email address is not explicitly configured in account settings.
-   Replaced the Markdown converter, `upskirt`, with the latest revision from github. Note that its name has now changed to `sundown`.
-   Fixed bug in the From -> Recipient replacement for mailbox searching in a drafts mailbox.
-   The preview layout (⌘1) of the Composer has been improved, in particular, the choice of layout is persistent and the window is now always closed when sending.
-   Fixed autosave-related termination bug when editing drafts with attachments (often seen when forwarding).
-   Swapped j/k related bindings in the Gmail keybindings file.

## Revision 2491 (Sunday, September 25, 2011)

In addition to a range of fixes/improvements, this release also includes some important steps towards improving integration with other applications. Some of it is still in an experimental state, but you can read more about it further below. It might even be fun to play with.

### Various fixes/improvements

-   Fixed saving of splitview divider positions. It failed in some cases when restarting MailMate (the width of the mailboxes outline was not preserved).
-   Fixed problem with a message being displayed even when a mailbox search has no matches (the previously selected message was still shown).
-   Fixed various problems where MailMate would try to synchronize a non-existing or non-selectable IMAP mailbox.
-   Improved forwarding behavior for messages with a `text/html` body part.
-   Fixed counting of attachments (implicitly the display of the paper clip in the messages outline) to work when attachments are hidden within one of the body parts of a `multipart/alternative` MIME body part (most often produced by buggy email clients).
-   Fixed some printing issues with message headers. Also, Quick Look buttons are no longer printed.
-   Temporary solution for hiding Bcc headers when forwarding/printing is to use boolean defaults values MmNeverForwardBcc/MmNeverPrintBcc.
-   Fixed program termination when copying messages to universal mailboxes.
-   Fixed problems related to the responder chain when closing windows. This could terminate MailMate, e.g., when closing a composer window by sending a message.
-   Fixed problem with synchronization of mailboxes when launching MailMate. In some cases this could lead to termination of MailMate.
-   Changed behavior of MailMate if a (buggy) IMAP server returns out of range sequence numbers. MailMate now reports the problem to the user instead of terminating.
-   Increased timeout value used after uploading a message to an SMTP server. Some servers are very slow to respond.
-   Improved sorting of subjects in the messages outline.

Also added debug code to more easily get a log from a failing server connection. When an error window is shown with the options of “Take Account/Mailbox Offline” or “Retry” then you can hold down ⇧ to produce a log of a retry attempt. The file is saved to the Desktop with a name with the following pattern: "MailMate_server_mailbox.txt".

### Integration with other applications

Safari has menu items which can be used to easily mail pages or links. These menu items now also work for MailMate with the caveat that MailMate attaches page content (since the composer supports plain text only).

Also new is that MailMate supports the following in the Services menu: “New Email With Attachment” and “New Email With Selection”.

It is also possible to obtain a special MailMate menu item in the PDF menu of the printing dialog (this works in any application). This can be done by making an alias to MailMate in the following folder:

```
~/Library/PDF Services/
```

After making the alias, the name of the alias can be changed to, e.g., “Mail PDF with MailMate.app”.

Finally, MailMate now also handle the following URL schemes: `mid`, `cid`, and `message`. Note that they can be “assigned” to MailMate by using the email application chooser in the (General) Preferences. Whether you need to do this depends on which email applications you have used in the past, e.g., “Apple Mail” only supports (and introduced) the `message` URL scheme.

Also added a menu item for “Copy as Link” using the `message` URL format. This URL scheme is an undocumented Apple feature, but this is going to work better if switching between Apple Mail and MailMate. An alternative could be the `mid` URL format which is standardized. This might be optional in the future.

### A RESTful interface

In order to try out the following very experimental feature, you need to enable it before launching MailMate:

```
defaults write com.freron.MailMate MmHTTPServerEnabled -bool YES
```

Now you can test it by entering the following URL in your favorite web browser:

```
http://localhost:54321
```

The only thing displayed is a link to the following:

```
http://localhost:54321/messages
```

This should show you a list of all messages in MailMate. You can click on any message, but don't click on junk messages since external references (images mostly) are most likely not blocked in the browser. The link to message number 1 (if it exists) would then be:

```
http://localhost:54321/messages/1
```

You can also see the message number of any message in MailMate by enabling the “Msg ID” column in the messages outline. In the special mailbox “All Body Parts” you can also see the message number of any body part.

The default `Content-Type` depends on the HTTP Accept header. In a browser, `text/html` is likely returned for any messages or body parts of type `text/*`, `message/rfc822`, or `multipart/*`. Other body parts are returned as they are defined in the MIME body part headers, for example, a body part of type `image/png`is returned as `image/png` (decoded to its binary form). When using `curl` from the command line then the default output is `text/plain` for body parts where this return type is supported. This is nicely decoded canonical (utf-8 encoded) text.

The returned data can be changed by explicitly stating the accepted type(s). For example, using `curl` from the command line, you can retrieve a raw message as follows:

```
curl -H'Accept: message/rfc822' http://localhost:54321/messages/1
```

Or you can retrieve the HTML formatted message used in the browser:

```
curl -H'Accept: text/html' http://localhost:54321/messages/1
```

You can also reference header values as follows:

```
http://localhost:54321/messages/1/headers/x-mailer
```

In this case the result would be a json array like `["MailMate r2460"]` if the message had been written in the latest (registered) revision of MailMate. The following is an example of how to use a specifier to only get the `MailMate` part of the header:

```
http://localhost:54321/messages/1/headers/x-mailer/name
```

You can also try the above in a browser where the following URL can be used to see a list of all headers in a message:

```
http://localhost:54321/messages/1/headers
```

Note that `message/rfc822` is also supported for the URL above.

All of this is work in progress and should be considered a “proof of concept”. The main goal is to use this as an interface for retrieving information about messages in MailMate from scripts in any language.

For now, MailMate still lacks a way to run commands on selected messages and therefore the above is not yet very useful in practice, but you are encouraged to play with it and maybe even provide some feedback.

## Revision 2419 (Wednesday, August 24, 2011) — Version 1.3.1

### Custom key bindings

The custom key bindings feature is now exposed in the GUI. It can be enabled in “Preferences ▸ General” and a comma-separated list of custom key bindings files can be entered. For now, only a Gmail key bindings file is distributed with MailMate. A help button in the preferences leads to a help book chapter which describes how you can create your own shortcuts, for example, to go to specific mailboxes, move messages, or to toggle IMAP keywords/tags.

Note: If you have used this feature while it was not exposed in the GUI then you still need to go to the preferences and enable it.

### Hidden preferences

Over time, numerous hidden preferences have been described in the release notes. A new [chapter](help:anchor=hidden_preferences%20bookID=com.freron.MailMate.help) in the help book lists all of them. Some of them are eventually going to have GUI counter parts, some will stay hidden, and some will be removed again. Look through the list to see if it contains one or more useful features for you. Feedback is welcome.

### “Guessing” standard mailboxes

Introduced strategy for guessing standard mailbox names, for example, MailMate automatically figures out to use a mailbox named “Trash” for deleted messages instead of creating a new mailbox named “Deleted Messages”. This is a heuristic approach since there is no standard for getting this information from IMAP servers except for the non-standard XLIST extension used by Google (and maybe others have adopted it). This extension is also supported by MailMate.

### Other changes

-   Now updates the choice of From-address (identity) when changing the main recipient in new messages (not for replies).
-   Now stops updating From-address/signature when an explicit choice has been made (for example, after choosing “No Signature”).
-   Fixed completion of names when inserting adress book groups in the composer (previously only the first name was included)..
-   Fixed selection-problem in the Correspondence outline (nested messages were not always selected).
-   Fixed problem with duplicates in the Drafts folder after quitting MailMate while writing an unsaved new message.
-   Removed unnecessary refresh when using Quick Look. In some cases this could also terminate MailMate.
-   The Quick Look buttons no longer require javascript and are thus displayed for all messages (previously not shown for HTML messages).
-   Automatically expands the SOURCES section in mailbox outline when adding new accounts. Important for the new non-obvious show/hide style used in Lion.
-   Fixed issue on Lion with respect to restoring window frames on startup.
-   When selecting a mailbox MailMate makes a quick check for new messages. For smart mailboxes MailMate identifies any explicit mailboxes on which the mailbox is based (recursively) and makes quick checks for new messages in these.
-   Added “View ▸ Clear Scrollback” (⌘K) menu item for clearing the log view in the Activity Viewer. It clears all logs if no connections are selected.
-   Fixed sorting problem for messages with address fields with only an email address.
-   Fixed selection problem in the correspondence outline. Some times MailMate would not select the correct message after, e.g., archiving.

### Link crashes (Default Folder X)

Some users have reported crashes when clicking on links in emails on Lion. If you experience this problem then it is very likely that you need to update the Default Folder X application. This problem also seems to not be limited to MailMate, but may occur for other applications as well.

## Revision 2359 (Saturday, August 6, 2011)

-   Fixed problem with the IMAP server at gmx.net (MailMate never finished synchronizing mailboxes). The problem may also have affected other IMAP servers.
-   Fixed an issue with viewer windows not opening on restart.
-   Fixed problem related to actions immediately after changed message selection (like double-clicking or when archiving multiple messages quickly one by one).
-   Now properly remembering whether or not automatic spelling correction is enabled in the composer.

Added temporary solution for adding a bcc header by default to all outgoing messages. Write the following in the Terminal if you need this:

```
defaults write com.freron.MailMate MmDefaultBccHeader -string me@example.com
```

Added experimental prefs value MmAllMessagesFilter to make searches faster. It can be used to reduce the number of messages included in the “All Messages” mailbox. All messages are still available via the IMAP sources/mailboxes:

```
defaults write com.freron.MailMate MmAllMessagesFilter -string "#date > 1 years ago"
```

## Revision 2341 (Wednesday, August 3, 2011) — Version 1.3

With this release MailMate now officially supports Mac OS X 10.7 (Lion). Lion related changes are described in the following subsection. The release notes for this release are extensive, but you should note the subsections further below describing some new experimental features, in particular, a new flexible system for custom key bindings (providing Gmail-like keyboard shortcuts) and the first small steps toward support for OpenPGP.

### Lion related features and fixes

-   Added full screen mode in Lion (⌃⌘F).
-   Fixed account importer to work for Apple Mail on Lion.
-   Added menu item in “View ▸ Spelling” for toggling the use of automatic spelling corrections.
-   Fixed problem on Lion with storing/restoring view frame sizes. Most often seen by a wrongly sized mailbox outline.
-   No longer using a private API for non-local address books when running on Lion (Apple fixed this issue).
-   Fixed occasional beeps and other problems triggered when quitting MailMate.

### New features and improvements

-   Undo/redo supported for moving messages.
-   Changed the look of attachments using tables and an updated stylesheet. This includes a button for “Quick Look” and drag'n'drop of the file icon.
-   Improved replying to messages in the Sent mailbox (which are handled as follow-ups instead of replies): Cc and Bcc are handled, the “Reply or Reply All” requester is never shown, and the default signature is derived correctly.
-   Mailbox Search/Editor: Fixed several date related issues including sticky values when changing comparison method or duplicating rows.
-   Mailbox Search/Editor: Date comparisons can now be done on the received date as well.
-   When cancelling/closing a mailbox search MailMate now returns to the originally selected mailbox.
-   Changed derivation of default From address to prioritize known recipient addresses higher than delivery addresses.

Two new options have been added to Preferences/General (based on frequent requests):

1.  An option to change the default behavior of double-clicking a message. It can now be set to open the message instead of searching for related messages.
2.  An option to use a bold font style for unread messages.

There is also a new hidden boolean option. When enabled, any message viewer or composer window is taken to the front when the dock icon is clicked. Normal behavior is to always open a mailbox viewer if none exists:

```
defaults write com.freron.MailMate MmShowAnyViewerOnDockIconClick -bool yes
```

### Custom keybindings

A new system is in place to provide custom key bindings for common tasks. As an example MailMate includes many of the key bindings used by Gmail. There is no GUI option yet, but this feature should be stable. To enable it, run the following from the Terminal:

```
defaults write com.freron.MailMate MmCustomKeyBindingsName -string "Gmail"
```

The key bindings are defined in the files located in:

```
MailMate.app/Contents/Resources/KeyBindings/
```

It is possible to create a new key bindings file and place it in:

```
~/Library/Application Support/MailMate/Resources/KeyBindings/
```

The Gmail key bindings file can be used as a starting point for new files. It includes most of what is possible to do. Each key-combination (or series of key-combinations) can be bound to one or more actions. Each action is defined by a so-called selector.

Some selectors accept an additional argument. These are `insertText:`, `goToMailbox:`, `moveToMailbox:`, and `toggleTag:`. The `goToMailbox:` and `moveToMailbox:` selectors work both with and without an argument. Alternatively, `goToMailbox:` can take the unique id of any mailbox as an argument (see Mailboxes.plist) and `moveToMailbox:` can take one of the following as an argument:

1.  A standard mailbox name such as inbox, archive, drafts, sent, junk, and trash.
2.  A mailbox path without an account such as `/Special`.
3.  A full path for a mailbox within an account such as `imap://you@imap.example.com/Special`

The following example would bind the key `g` to move a message to a mailbox named `Special` within the account the message is currently located:

```
g = ( "moveToMailbox:", "/Special");
```

Here is an example of using key bindings to tag messages. It also illustrates the use of nested key bindings:

```
"t" = {
	"s" = ( "toggleTag:", "Special" );
};
```

In this example, entering `ts` toggles a tag named `Special`. It should be possible to define a column showing the state of such a tag and it is possible to match on it when searching or creating smart mailboxes. Other than that the tag is “invisible” for now. Note that the tag is given directly to the IMAP server and thus you should use ASCII and no special characters including no use of space.

### Basic experimental OpenPGP support

The first step has been taken towards support for OpenGPG. So far, there is only support for decrypting and verifying ASCII armored text parts (inlined signatures/encrypted text). It should not be considered stable, but you can help by trying it out anyways.

MailMate is currently hardcoded to use `/usr/local/bin/gpg2` which you need to install if you do not already have it. The GPGTools installer is recommended (or just MacGPG2 and optionally GPG Keychain Access).

To enable this feature in MailMate you need to paste the following in the Terminal:

```
defaults write com.freron.MailMate MmEnableOpenPGP -bool yes
```

### Experimental “IMAP window”

Since MailMate is an offline email client it requires a lot of disk space if you have a large collection of emails. As an experimental feature MailMate now offers to only fetch a subset of messages based on their age. It is currently controlled with an application wide preferences value:

```
defaults write com.freron.MailMate MmIMAPWindowInDays -int 365
```

This should limit MailMate to only fetch messages with a date within the latest year (technically, it is based on the so-called INTERNALDATE of the message on the server).

MailMate does not dynamically adapt to changes to these settings yet. It only has an effect when initially synchronizing an account. (Internally, MailMate supports controlling this window at both account and mailbox level, but this currently requires manual editing of state files.)

Any feedback on this feature is welcome, but use it with care. It _is_ experimental.

### Other changes and fixes

The following is a detailed list of all other changes since the latest public release:

-   Improved the behavior of MailMate with regard to the INTERNALDATE provided for a message uploaded to an IMAP server.
-   Fixed termination problems triggered when deleting an account or some times just quitting MailMate.
-   Coalesced identically named “Open Message” menu items in the “File” menu.
-   Fixed problem with lacking quotes around names in email addresses. Now only allows `-_` and alphanumeric characters without quoting.
-   Fixed problem with flags not being set for new messages (resulting in an unread state for sent messages).
-   Fixed selection of next/previous message in some circumstances when, for example, archiving messages.
-   Temporary solution to a visual problem with showing a large number of recipients in the headers view.
-   Fixed problem which could cause MailMate to be stuck in a mailbox, i.e., it was impossible to get into a different mailbox.
-   Fixed visual glitch when deleting text. It was fixed by not removing attributes unless they exist (seems to be an NSTextView bug). Also tried to fix a performance problem, but this was not possible.
-   Fixed rare crash related to unescaped quotes (triggered under certain circumstances when inserting a quote character in a recipient field in the composer).
-   Fixed crash related to the use of ' when searching for a string in an email.
-   Added “attaching” to the default set of words triggering a potential warning about missing attachments.
-   Improved threading of messages with a References header but no In-Reply-To header.
-   Better/correct splitting of quoted paragraphs when doing it at the end of a line.
-   Now properly showing From-popup when basing reply on a delivery header with a different address than the address of a single-account-single-address configuration.
-   Generated HTML is now much more readable (“Show HTML Source”).
-   Removed explicit stylesheet used for “Show Raw Source”. Replaced by styling pre-elements which have been assigned a special class name (`raw`).
-   MailMate is now compiled using `clang` instead of `gcc`. May or may not improve performance (no benchmarks done), but it certainly improves development speed.
-   Fixed bug which would some times cause the importer window to never appear.
-   Detection/display of links surrounded by <...> in plain text now works better.
-   Improved (less strict) parsing of Message-ID header.
-   Fixed various issues with key bindings. In particular, space did not always work as expected. This was related to how/when Cocoa issues the performClick: action.
-   Swapped the priority of Content-Description filename and Content-Type name when determining a filename.

When using the following debug variable, a log file is dumped to `/tmp/mailmate_imap_subscriptions.log` if an error occurs while fetching mailboxes to be displayed for “Edit Subscriptions”.

```
defaults write com.freron.MailMate LoggingEnabled -bool YES
```

(It also enables logging for the Activity Viewer even when the Activity Viewer is closed.)

## Revision 2204 (Monday, June 13, 2011)

-   Fixed multiple issues with authentication in both IMAP and SMTP. This is a good time to retry with any problematic accounts.
-   SMTP: When trying port 465 (which is non-standard and undocumented) both STARTTLS and portwrapped SSL is attempted. If you have had problems enabling SSL on port 465 then it might work now.
-   Fixed various issues displaying HTML messages.
-   Attachments are now (more often) displayed when viewing the plain text body part of a message with an HTML alternative.
-   Workaround for problem with displaying rare subject lines with multiple blobs a la: “[blob1] Re: [blob2] Re: Re: Subject...”.
-   Close any active mailbox search when closing the messages viewer window. This makes the counter menus more reliable when selecting messages.

## Revision 2191 (Wednesday, June 8, 2011)

### Improved Markdown support (still experimental)

MailMate now ships with a Markdown converter. It is named `upskirt` and it was originally created for GitHub. A blog post will soon be posted which describes the Markdown experiment in more detail.

An alternative composer window has also been included by default. It contains a message view to make it easy to preview the current draft by simply saving it. See the “View ▸ Layouts” menu or just hit ⌘2 in the composer.

The default CSS has been improved to work better with the output from `upskirt`. This includes a simple look for tables.

### Other changes

-   Changed default tooltip for thread arcs. It now simply states from name and a relative date, for example, “John Appleseed, 2 days ago”.
-   Fixed minor problem with displaying attachments with an explicit inline content disposition.
-   Fixed some SMTP authentication problems.
-   Fixed problem with occasionally unsaved text field values in the preferences windows.

## Revision 2175 (Thursday, June 2, 2011)

Fixed issues with IMAP authentication methods (AUTH=PLAIN and AUTH=CRAM-MD5).

## Revision 2169 (Thursday, June 2, 2011) — Version 1.2

_Special note:_ Goggle has changed the default set of mailboxes provided via IMAP. It is strongly recommended to go into the Labels part of the Gmail web settings and make sure the following mailboxes are marked as “Show in IMAP”: Sent Mail, Drafts, Spam, and Trash.

### New look for attachments

A transition has started to provide a more table-like display of non-inlined attachments with 1 row for each attachment. Note that:

-   Dragging attachments (including inlined images) now works as expected.
-   The context sensitive menu is shown when right-clicking anywhere in a row.
-   There is a new menu item to “Open With”.

Inlined PDFs are shown using the img HTML tag (thus avoiding PDF plugins). Note that you can always Quick Look attachments (⌘Y). If you never want to inline PDFs then you can do the following in the Terminal (temporary solution until a general system is in place):

```
defaults write com.freron.MailMate MmNeverInlinePDF -bool YES
```

### Updated stylesheet for the messages view

As part of the attachment changes, the HTML generated has been simplified and the default CSS file has been updated/extended. If you have created a local stylesheet variant you may need to update it. If you have experience with CSS then you are encouraged to take a look at the default stylesheet:

```
/Applications/MailMate.app/Contents/Resources/MmMessagesWebView/stylesheet.css
```

You can extend the stylesheet by creating a file in the following location:

```
~/Library/Application Support/MailMate/Resources/MmMessagesWebView/stylesheet.css
```

You can see the HTML generated for a message by using “View ▸ Show HTML Source” (⌃⌘U) within MailMate.

### Experimental: Markdown for writing emails

The following enables an extra option in the composer which allows you to tell MailMate that you are writing your message using Markdown:

```
defaults write com.freron.MailMate MmAllowMarkupLanguages -bool YES
```

The motivation for this idea is going to be described in a blog post, but in short, if Markdown is chosen then `markup=markdown` is appended to the Content-Type of the text body part of the message. This can be ignored by the receiving email application or it can be used to convert the Markdown text to HTML before displaying it. Currently, the only email client to do so is of course MailMate and currently it only works if MailMate finds `markdown` or `upskirt` in the default path (a Markdown to HTML command is currently not distributed with MailMate).

### Various new features

-   Added submenu items for counter menus in the status bar: Archive, Move to Junk, Delete, Reply, Forward, and “Mark as Flagged/Read”.
-   Added “Empty Mailbox” menu item for Deleted Messages and Junk.
-   Added shortcut to synchronize the currently selected mailbox (⇧⌘N).
-   It is now possible to synchronize smart mailboxes which are based on IMAP mailboxes (also ⇧⌘N).
-   Escape can now be used for both cancelling text search in webview and for cancelling mailbox search.

If available the IMAP XLIST command is now used (supported by Gmail) to get the standard mailboxes. This should make MailMate work better (by default) when used with localized variants of Gmail. It may also affect your current setup if mailbox types had not been explicitly assigned.

### Delivery headers

Changed the detection of delivery headers (such as `X-Original-To`) such that it no longer requires the existence of an identity with the same domain in an email address as found in the delivery header. If this is a problem for some users then please report it (more real life examples would be useful since this is basically a heuristic). The new behavior can currently be disabled using:

```
defaults write com.freron.MailMate MmAlwaysTrustDeliveryHeaders -bool NO
```

MailMate is now also better at guessing an appropriate from address for, e.g., mailing list messages (essentially doing the same as when replying to messages).

### New debug variables

Debug variable for scripts:

```
defaults write com.freron.MailMate MmDebugScripts -bool YES
```

Debug variable for logging communication between SpamSieve and MailMate:

```
defaults write com.freron.MailMate DebugSpamDetection -bool YES
```

If you have had problems with accounts getting stuck in a “disconnected” state then you can help debug the problem doing as follows:

```
defaults write com.freron.MailMate MmDebugReachability -bool YES
```

This is going to log data which can be found in Console.app when the problem occurs.

### Details, detail, details

This is an example of how you can change the font of the headers view (intermediate solution since the headers are planned to be moved to the messages view):

```
defaults write com.freron.MailMate MmHeadersViewFontName -string "LucidaGrande"
defaults write com.freron.MailMate MmHeadersViewFontSize -float 16
```

Other details:

-   Changed the parsing of the List-ID header identifiers to include those not following the format in RFC2919 (for example, the IMAP protocol mailing list).
-   “Move to/Go to Mailbox” now use the full mailbox path in the mailbox chooser. This should make it easier to match submailboxes.
-   If available the IMAP ID command is used to tell the server about MailMate.
-   Fixed problem with updating universal mailboxes when changing assigned mailbox types in IMAP accounts.
-   Fixed problem with unnecessary resizing of views in the Widescreen layout (triggered when doing a mailbox search).
-   Fixed problem with matching some mailbox names in “Move to/Go to”, (mailbox names with non-ASCII not created in MailMate).
-   Fixed: The mailbox search did not work correctly for 'exists/not exists' queries (they were simply ignored).
-   Fixed problem with the From-field not being shown when a single account was configured with multiple addresses.
-   Fixed problem with an email with a date which was 410 years ago (and any similar date-handling problems).
-   Fixed problem with Synchronize All Sources.
-   Fixed problem with MailMate terminating after entering a recipient in the composer. It was triggered when restarting MailMate with a composer window open with a non-existing message.
-   Fixed problem with moving messages into the INBOX on an account with an INBOX namespace. An INBOX/INBOX was created, but the messages were still correctly moved to INBOX.
-   Fixed problem with percentages shown in the statistics view (only a problem on Leopard).
-   Improved detection of local IP for use in the EHLO of SMTP (important to avoid rejection by some SMTP servers).
-   Fixed crash when deleting an account (triggered by trying to get the state of a non-existing mailbox).

## Revision 2089 (Wednesday, May 4, 2011) — Version 1.1.2

### Improved mailbox search

It is now possible to save the default mailbox search conditions. Setup the search you would like by default (likely with empty text fields) and then select “Edit ▸ Find ▸ Use as Default Search”. Note that (as always) empty text field values are ignored when doing a mailbox search (as opposed to the smart mailbox editor). This is not new, but it is useful to know if setting up multiple conditions in the default search.

Also, when adding rows in the rule editor the new row is based on the row for which + was clicked (or the closest following simple row if a compound row is clicked).

### Improved completion of addresses in the composer

-   Stays in edit mode when pasting if the pasted string does not appear to contain an email address.
-   When a single token is selected, the space key can be used to go into edit mode.
-   When completing addresses and no matches are found, the casing is now returned to how it was entered. This is especially useful when manually entering an email address which is unknown to MailMate.
-   Fixed various issues with duplicate entries in the suggested completions.
-   Fixed an issue with reordering of first/last name when completion was based on previous recipients.
-   Fixed an issue with tabbing out of an address header when a group name is entered.

### Other changes

Fixed a bug related to the junk state of messages. When deleting a message in Junk it was wrongly marked as not junk. A bad side-effect of this is that SpamSieve was also notified that it was not junk. If you have been affected by this bug then you should consider resetting the corpus in SpamSieve. Thanks to Erik for reporting this problem (ticket #124).

Empty email address groups are now ignored when sending via SMTP. This can be used to, for example, send to “Undislosed Recipients:;” without getting an error. For convenience you can create an empty Address Book group with “Undisclosed recipients:;” as a name (or some other name, but remember to include “:;”).

Added support for the SMTP authorization method named LOGIN. This is an alternative to PLAIN which is already supported by MailMate, but some SMTP servers only support LOGIN. These methods are almost identical, but LOGIN requires more round trips to the server than PLAIN. If you have had problems with MailMate continually asking for a password for some SMTP servers then this might be a solution.

-   Open Messages (⌘O) now opens multiple messages in one window. Separate windows can still be obtained using ⇧⌘O.
-   The behavior of smart mailboxes with filters such as “date is within last x days” has been improved.
-   The Bcc header is stripped by MailMate itself instead of leaving it to mail transfer agents.
-   Fixed memory-issue with importing large IMAP accounts/mailboxes.
-   Fixed minor issue with replies based on selected text (ticket #121).

## Revision 2038 (Friday, April 8, 2011) — Version 1.1.1

### Autosave

When composing a message, a copy is autosaved every 30 seconds (but only if changes exist). When launching MailMate, any autosaved messages are detected and the user is asked to either discard or import. This should never result in more than 2 versions of a draft: The autosaved version and the most recently explicitly saved version.

### Other changes

-   Reordering of standard mailboxes is now allowed.
-   “Save Attachment...” now shows and allows changes to the default filename.
-   More information provided when importing messages.
-   The Flag column in the messages outline is now used to display an exclamation mark for high priority messages (only when message is not flagged).
-   Improved replying to messages in “Sent Messages”. It previously failed when the message was not sent from the first identity of an account.
-   Removed maximum width for a couple of integer columns in the messages outline in order to better handle custom font sizes.
-   Only applying SpamSieve to messages without the $NotJunk flag. This is needed, for example, if running SpamSieve on two machines when trying to move a message from the Junk mailbox back into the Inbox.
-   Now using “MIME-Version” instead of “Mime-Version” in new messages. Details matter.
-   Workaround for Gmail for a problem resulting in sent messages ending up in the trash. How to reproduce the problem is unresolved but it is likely related to Googles alternative interpretation of the IMAP standard.
-   Workaround for servers wrongly providing EXISTS responses before EXPUNGE (Yahoo, MS Exchange 2007, and probably others).
-   Fixed various other IMAP issues.

## Revision 2003 (Friday, March 25, 2011) — Version 1.1

### MailMate for everybody

Several improvements allow MailMate to work with most (if not all) IMAP servers. Send some feedback if you have an IMAP account which does not work with MailMate.

The most important improvements are:

-   No longer requiring the UIDPLUS extension. Servers with the UIDPLUS extension are still recommended since it is both more robust and more efficient when utilized by an offline IMAP client such as MailMate.
-   Better handling of IMAP servers with limited support for IMAP keywords (such as MS Exchange IMAP).
-   Handles when the INBOX on the server is not in uppercase (such as Yahoo IMAP).

### Image blocking improved

The default in MailMate is now to always block external references, but the user has detailed control of the behavior using some new preferences (currently under General). The most important setting is “Block external references for messages in …” which allows the user to define a mailbox containing the messages for which blocking should be enabled. The default is “All Messages”, but it could be any smart mailbox, for example, a smart mailbox excluding messages which have been identified as being safe. This could be based on headers inserted by server-side spam detection software (like “X-Spam-Score” or “X-Spam-Flag”).

For convenience, the preferences also include a checkbox for “Load external references for messages marked Not Junk” (this could also be done using a smart mailbox as described above). This is especially useful when combined with a new SpamSieve option which allows you to automatically mark messages as Not Junk if they have a low spam score.

Go to the General preferences and play with these new settings and send some feedback if it somehow cannot handle your preferred use of image blocking.

Note that blocking is always enabled for messages in “Junk” or “Deleted Messages”. It is also always enabled for attached messages (occurs when using something like “Forward as Attachment...” has been used to construct an email). This allows one to safely receive forwarded spam.

### Composer related changes

When completing addresses, MailMate now looks in all Address Book sources. Technical note: This is done using a private API and therefore this feature may be removed again in future versions of MailMate. Feedback on both success and failure of this feature is welcome.

When pasting in the composer, text is preferred to images (pasting an image makes it an attachment). This was necessary since otherwise pasting text from some applications would instead result in the attachment of an image.

Also note:

-   Email address completion now works for Address Book groups including distribution list identifiers.
-   Improved splitting/merging of quoted paragraphs.

### Other changes

MailMate now enforces a 30-day trial period. It is measured as days of active use measured by the number of days on which messages have been sent. When the trial period has expired, you can still use MailMate, but you can only send 2 messages per launch.

Interesting minor changes:

-   Separate search shortcuts: Search All Messages (⌥⌘F) and Mailbox Search (⌃⌥⌘F).
-   The Search button in the toolbar now keeps MailMate in the current mailbox if holding down ⌥.
-   Allows renaming of standard mailboxes.

Various (less interesting) fixes:

-   Fixed bug in saving attachments using “Message ▸ Save Attachments...” triggered when focus was in the message view (nothing was saved).
-   Fixed rare crash bug related to a message being deleted while in the process of being displayed in the message view.
-   Fixed problem triggered when an IMAP connection was reused to select a second mailbox just after a message was expunged from the first mailbox (server-side).
-   Fixed crash bug which was triggered when a new IMAP mailbox was registered and a popup button with mailboxes was in use at the same time.
-   “Move Out of Junk” is no longer greyed out in the messages menu when messages are selected in the Junk.
-   Fixed bug in the filter editor (Mailbox Search) which would make it ignore parts of the query if an any/all expression existed with a single child.
-   Removed toolbar button in the Preferences window.

## Revision 1951 (Saturday, March 5, 2011) — Version 1.0.2

The SpamSieve support can now be enabled in the preferences. This includes the choice of a mailbox in which SpamSieve should be used to check new messages. By default, this mailbox is the unified Inbox, but it could be any smart or real mailbox.

The handling of messages outline columns has been improved. Submailboxes automatically inherit the settings of parent mailboxes unless explicit changes are made and it is now possible to select the outline column (the column with a triangle) which is useful if the order of columns is changed.

Composer related changes:

-   Improved the default choice of identity (from-address) for new messages.
-   Fixed handling of signatures such that “No Signature” is remembered for future messages.
-   Fixed quoting level color when removing the last quote level character.
-   The various settings in the Substitutions menu (in the context sensitive menu) are now saved. In particular, Text Replacements can be enabled (see Language and Text in the System Preferences).

IMAP related changes:

-   Fixed issue where subscribed mailboxes under a private namespace were not found (due to a missing delimiter in the namespace prefix).
-   When creating a mailbox with the same name as an unsubscribed mailbox, the mailbox is automatically subscribed (instead of failing).
-   Added alternating row colors in subscriptions sheet.

Other changes:

-   Added “Common Headers or Body” to make it easier to search addresses, subject, or unquoted body text.
-   Fixed encoding of long header lines with non-ASCII and no spaces (for example, a subject line in Japanese).
-   Now allows whitespace around “=” in Content-Type parameters (in order to handle a bug in at least some versions of PHPMailer).

## Revision 1928 (February 23, 2011) — Version 1.0.1

### Reply All vs. Reply

Until now MailMate only had a single “Reply” button (and menu item). It worked as “Reply All” and the only way to make a private reply was by clearing the Cc header. This has now been improved, but even though a “Reply All” (⇧⌘R) menu item has been added, the intention is that it is not needed, because of the new behavior of “Reply”.

The feature is quite simple. When replying to a message with multiple recipients, MailMate displays a sheet to ask if one wants to reply to all or to reply to the author only. There are easy shortcuts for both alternatives (Return and Space).

Rationale: It is bad to reply to all if one really wanted to reply to a single person. But it is also bad (although not as critical) to forget to reply to all when that would have been appropriate. The solution here is to always ask when a message has multiple recipients. If you dislike this behavior, you can go to Preferences/General to make Reply work as in, for example, Apple Mail.

### SpamSieve (experimental)

As you may have noticed, MailMate has no built-in junk-filtering. This is unlikely to change soon (if ever), but now there is support for SpamSieve, a shareware utility for identifying spam. It was, more or less, implemented today, so for now it is an experimental feature and can only be enabled via a hidden preference.

To enable it, copy/paste the following to the Terminal:

```
defaults write com.freron.MailMate SpamSieveEnabled -bool YES
```

Note that the preference above may be cleared by MailMate if it fails to find and launch SpamSieve.

The SpamSieve support works as follows.

-   Any new message in any Inbox is given to SpamSieve. If it is identified as spam then it is automatically moved to Junk (within the same account).
-   If a message is explicitly marked as “Junk” by the user then SpamSieve is told that the message is good.
-   If a message is explicitly marked as “Not Junk” by the user then SpamSieve is told that the message is spam.

You can use the “Junk/Not Junk” keywords to train SpamSieve. The SpamSieve score can be seen in a dedicated messages outline column. A planned feature is to allow the user to specify the mailbox for which SpamSieve should be used to check for spam. The default is the unified Inbox.

### Memory leak in Activity Viewer

An important memory leak was found in the Activity Viewer. It was especially bad if the Activity Viewer was open during the initial synchronization of account(s).

### Other

There is now a hidden option to enable alternating row colors in the messages outline:

```
defaults write com.freron.MailMate MmMessagesOutlineUsesAlternatingRowColors -bool YES
```

Minor changes and bug fixes:

-   Fixed the row height in the outlines for custom fonts (some fonts were previously clipped).
-   Fixed date issue caused by UNIX calls and CFTimeZone disagreeing on the current time zone (in relation to UTC).
-   Added “Save Attachment...” to the context sensitive menu in the message view.
-   Enabled “New Folder” in save panels for attachments.
-   Improved handling of opening .eml files (but still not showing .eml messages which are not known by MailMate).
-   Now encoding all application/* MIME types as base64.
-   Fixed crash/efficiency bug related to adding the bodies of retrieved messages to the database.
-   Fixed crash bug triggered, e.g., when double-clicking on a message in the To-column when the message had multiple recipients.
-   Improved parsing of quoted strings in headers, e.g., filenames containing double quotes.
-   Fixed crash bug which could be triggered by “Edit as New Message…”.
-   Fixed “Use as Default Headers” in the Composer which was broken in recent updates.
-   Fixed crash related to renaming IMAP accounts.
-   Added messages with the \Deleted flag to the set of messages which should not be trusted to fetch external resources.
-   Removed “Delivered-To” from the set of headers checked when trying to deduce an alias for a from-address. Should probably never have been added in the first place.
-   Looking for Thunderbird settings in ~/Library/Thunderbird/profiles.ini instead of Profiles.ini.