# Helmut4 Changelog

All notable changes for the private product [Helmut4](https://www.helmut.de) will be documented in this file.

## [development release]
### Added
- Added an automatic Node Tree sorting function. Win: CTRL + L, Mac: CMD/Control + L. 
  - Nothing selected: Entire Node Tree will be adjusted
  - One Node selected: Node acts as anchor, only the downstream Nodes will be adjusted
  - Multiple Nodes selected: Only the selected Nodes will be adjusted
- Basic Auth support with username:password and clientId:clientSecret (oAuth tokens) instead of Bearer token.
  - Bearer Auth still supported
- We added an extra level of security to the way Helmut components connect to the message bus:
  - You will need to install the new client 4.0.5.x
  - Client 4.0.5.x is compatible with Helmut versions < 4.0.5.x but not the otherway around.
- RevApp integration to Upload Assets, Share Assets (public and private) and Delete Assets (streams: 4.0.5.24, hw:4.0.5.11)
  - Add your RevApp credentials under Preferences -> Modules -> RevApp
- Will Now show the name of the stream in the delete confirm message (translateable)
- Web backup now supports cronjobs and store variables
- Added Variable Store. Stores user Key / Value pairs + protected flag.
  - Nodes:
    - Get Variable by key
    - Set (update) Variable value or create a new one
    - Delete Variable
  - Store Gui:
    - Overview of all Variables
    - Manually create, delete or update Variables
    - Protected flag can only be changed here
    - Protected Nodes can only be changed by Admins. Can't be changed by Nodes
- Added Snapshots Modal (streams:4.0.5.17)
  - Add Snapshot of current node tree
  - Load a saved Snapshot, and repalce your current node tree with it
  - Independent of 'save' functionality, unsaved progress will be lost
  - Delete Snapshots
- Block switching active project whenever a sync process is active (hp:4.0.5.5)
- Add option "Don't change breadcrumb" and renamed the corresponding asset name feature of the Add Asset to Project Action (hp:4.0.5.5; streams:4.0.5.26; co:4.0.5.4; hk:4.0.5.2)
- Added EditShare EFS Media Storage Nodes (streams: 4.0.5.17)
  - Media Space
    - Create Media Space
    - Delete Media Space
    - Get free space of Media Space
    - Update Media Space
    - Add group to Media Space
    - Add users to Media Space
    - Remove group from Media Space
    - Remove users from Media Space
  - Users and Groups
    - Add users to group
    - Create groups
    - Create user
    - Delete groups
    - Delete users
    - Remove users from group
- Add select all option to multiselect field (for example to select all groups in add user dialog) (hw:4.0.5.13)
- Panel related logging that can be seen on debug port via chrome is now exposed to a log file next to the project file (hp:4.0.5.8)
- Fix all store variable nodes in case of the "Connection refused" issue (streams:4.0.5.27)
- Fix regex condition node for regex syntax inputs like \d (streams 4.0.5.27)
- Added RClone nodes. The RClone installation as well as the set up of remotes has to be done manually
  Nodes:
  - Copy
  - Mkdir (Make directory)
  - Move
  - Purge
  - Rmdir (Remove directory)
### Fixed
- Requests to Premiere like render project, render AAF etc. would timeout (and loop sometimes) after 2 minutes (also patched in 4.0.4-release-0)
- Removed default 1970 date for datetime metadata (hp:4.0.5.2, hw:4.0.5.6)
- Fixed webinterface asset update for synced callback loop
- Project filters can now be saved if the language has changed
- Fixed Scrollbar in the Streamdesigner's 'edit panel' to be full size again (streams:4.0.5.14)
- Duplicate profile when group is selected is not working without throwing JSON parse error (hw:4.0.5.10)
- Fix umlauts and "-" char of metadata keys comming from premiere sync (co:4.0.5.3)
- Fix preload profile at export page loading of panel (hp:4.0.5.6)
- Fix stream renaming issue where a renamed stream appears to be empty and finishes without running any node (hw:4.0.5.12)
- Proxy path will now change if an asset is indexed that had already a proxy set (co:4.0.5.3)
- {job.proxy} is not null anymore for autoimport streams (co:4.0.5.3)
- Reset footer selection count and action button if an individual action button of a table entry is used (hp:4.0.5.8)
- Store variable can now not be duplicated by renaming an existing one (streams 4.0.5.27)
- Fix action menu in housekeeper multiselect (hw:4.0.5.13)
- Fix "Medialoopster Update Asset Delete Date Action" for IMAGE and AUDIO assets (hw:4.0.5.13; users:4.0.5.4; streams: 4.0.5.27)
- Editshare nodes used to show 'successful' when no work was done (Because of missing user input). Now it shows that it fails (streams: 4.0.5.28)
- Editshare nodes used to work, even if the module is disabled. Now they will fail (streams: 4.0.5.28)
- File Copy Action Node will cancel the job at first try rather than resetting the job status back to RUNNING (streams:4.0.5.29)
- Fix bug where a streams import was impossible when trying to import streams from an older version that has a higher patch version (hw:4.0.5.15 ;streams:4.0.5.30)
  - Example: importing 4.0.4.125 streams export into a 4.0.5.5 streams version
- Fix Stratus Asset Create Action node -> Description field behaviour that no longer transfers project related metadata (streams:4.0.5.28)
- Fix all Store variable nodes to work in production environment -> They do not throw bad requests (streams:4.0.5.28)
- Add Snapshots dialog is now showing "Name:" instead of "Key:" (streams: 4.0.5.31)
- Add job or project over message bus removes an entry at bottom of the list to avoid exceeding the limit (25/50/75/101). When limit is not reached
  Jobs/Project have been removed from the list by mistake (hw:4.0.5.14)
### Changed
- Adding new jobs/projects via the the message-bus will now remove the last entry of a list to never exceed the selected size of shown elements (25/50/75/101)
  - We received reports of huge performance issues when being on the dashboard and a lot of new jobs showed up
- Search for projects or jobs in the Webinterface now adds a delay of 500ms while typing before the search will be executed to avoid spamming the server
- Changed Variable Store shortcut from v to k (streams:4.0.5.14)
- Changed loading indicator for autosync process by mooving it to the footer (hp:4.0.5.4)
- Changed multiselect and mooved it to footer (hp:4.0.5.4)
- Changed type of several input fields to autocomplete to allow search and select functionality (hw:4.0.5.10, hp:4.0.5.3)
- Increased total number of unsynced assets in badge to 999+ (hp:4.0.5.3)
- Variable Store: The key of an existing key/variable pair can be updated (streams:4.0.5.17)
- Improved RevApp nodes (streams:4.0.5.23)
  - Connection to new Worker container for file upload
  - Option to overwrite the creator on upload job request
  - Fix typos and improved placeholders and descriptions
- Unselect selected item in table whenever the very same item is clicked again (hw:4.0.5.11)
  - In this case the right bar will disappear
- Append -nostdin to FFMPEG render node to avoid requesting user input when overwriting an output file is needed (streams:4.0.5.24)
- Change users page search to be backend side and add an "unassigned" entry that searches for users that are not part of any group (hw:4.0.5.11, users:4.0.5.3)
- Add option to remove a stream from a profile in the add/edit profile dialog (hw:4.0.5.12)
- "Medialoopster Add Asset To Project Action" is now also adding existing assets to project (streams 4.0.5.27)
- Change behaviour to text input fields to select everything only for first click, every other click will navigate the cursor between the text (hw:4.0.5.13, hp:4.0.5.8)

### Removed

## [4.0.4-release-4] (stable release)
### Fixed
- Add RevApp connector nodes (streams:4.0.4.105, fx:4.0.4.20)

## [4.0.4-release-3] (stable release)
### Fixed
- Fixed housekeeper search query for all search combinations of unique and usedInTimeline flag for the node "Cosmo Get Project Assets Action" (co:4.0.4.26)

## [4.0.4-release-2] (stable release)
### Fixed
- Add fix where the invisble panel would not import assets into premiere after selecting them in the file/folder choose dialog
  - Requires a new client rollout (v4.0.4.28)

## [4.0.4-release-1] (stable release)
### Changed
- Adding new jobs/projects via the the message-bus will now remove the last entry of a list to never exceed the selected size of shown elements (25/50/75/101)
  - We received reports of huge performance issues when being on the dashboard and a lot of new jobs showed up
- Search for projects or jobs in the Webinterface now adds a delay of 500ms while typing before the search will be executed to avoid spamming the server

## [4.0.4-release-0] (stable release)
### Added
- Support for HTML tags in Wildcard Resolver (Streamdesigner) (streams:4.0.4.2)
- Highlight projects that are locked by you (hw:4.0.4.2)
- Pagination to Metadata page (hw:4.0.4.3)
- Switching to dashboard after executing a task within Housekeeper (hw:4.0.4.2)
- Add Premiere Generate New UUID Action node. Will give a Premiere Project a new global UUID to avoid duplicates. (streams:4.0.4.4)
- Premiere OS Path Mapper now also maps <ActualMediaFilepath> (streams:4.0.4.4)
- FFMpeg Render Node now outputs to node.result and {job.destination} (streams:4.0.4.4)
- Added all sequence informations to sequence exports via JSON side car file (streams:4.0.4.4)
- The Panel now logs out if a user disconnects from the local Helmut client or quits the client (hw:4.0.4.3)
- Nodes to add/remove Asset's to/from Medialooopster (streams:4.0.4.27)
- {user.client} wildcard which resolves to the clients version number (available in server streams too) (streams:4.0.4.27)
- Links between {node.result.?} wildcards and the actual linked Node in Streamdesigner (streams:4.0.4.27)
- Denied deletion within the Streamdesigner of linked Nodes using {node.result.?} (streams:4.0.4.27)
- Functionallity to expand/reduce single/all (all = shift+click) Nodes individually next to the global 'Show settings' function within the Streamdesigner (streams:4.0.4.27)
- Feature to enlarge the inline Stream debugger withing the Streamdesigner (chevron on the right site when Debugger is open) (streams:4.0.4.27)
- Manual refresh button to the IO/CO/HK-Dashboard if filters are set (new events will no more be pushed on top of the list regardless of the filter) (hw:4.0.4.8)
- Feature to live debug log files of connected clients via the the Action menu in the FX-Dashboard (license:4.0.4.1 hw:4.0.4.8 users:4.0.4.2)
- DISCONNECTED event (delays client logout until all Streams are executed) (license:4.0.4.1 hw:4.0.4.8 users:4.0.4.2)
- Relative date filters for custom metadata from type date (fx:4.0.4.1, hw:4.0.4.4, hp:4.0.4.3)
- Stream trigger point for unindexed assets (co:4.0.4.3)
- HTTP Request Node (experimental; streams:4.0.4.32)
- Natural, alphabetical Metadata sorting in Project, Asset and Dashboard overlay (hw: 4.0.4.12)
- Helmut Confirm Dialog Action to ask a user confirm a question within the Webbrowser (streams:4.0.4.32 hw:4.0.4.12)
- Helmut Input Dialog Confirm Action to ask a user answer a question within the Webbrowser (streams:4.0.4.32 hw:4.0.4.12)
- Add User To Group Node to add user(s) to a Group (for exmaple during group/user creation) (streams:4.0.4.32)
- Added more nullpointer checks to index project logic (co:4.0.4.5)
- <s> Version to name of downloaded clients (hw:4.0.3.14) </s>
- Added Multilanguage support to Webinterface and Panel. Streamdesigner and error messages will NOT be translated.
  - Add Languages under "Language" Menu entry and set them as default Language under Preference > General
  - This Language will also be applied to the Panel
  - Languages marked with a red color are not yet translated - same goes for new entrys after updates.
- Added indicator for missing translations
  - Missing translations always fall back to English (unchangeable/undeleteable language)
- Added multiselect to most of the table views of the web interface (hw:4.0.4.21)
- Add Medialoopster Update Asset Delete Date Node
- Some Nodes did not create the destination folder if it didn't exist, this has been changed in various nodes
- "Import Project To External Helmut Action" to import a Project into an external Helmut using OAuth
  - The Projectfile will be uploaded
  - Metadata will be merged by names if enabled in Node
- Stratus Asset Add Folder Membership Action to Streams (streams:4.0.4.54)
- Added delete job and delete multiple jobs functionality and the corresponding access preset (hw:4.0.4.23, fx:4.0.4.7)
- Multinode copy to StreamDesigner (cross tab requires SSL) (streams:4.0.4.67)
- Freetext search does now also cover IO job statusMessage field in dashboard view (io:4.0.4.11)
- Added Multiselect in panel and web and reworked the selection to avoid sort order variation during selection (hp:4.0.4.12, hw:4.0.4.24)
- Added a boolean field "filterable" to metadata to enable/disable the possiblity for filtering for it. Not filterable metadata which are already set as filter will be 
  kept until they will be removed. After Removal they cannot be filtered until filterable is enabled again (hw:4.0.4.24, hp:4.0.4.11, metadat:4.0.4.4.2)
- Added wildcard to count words in a string (streams:4.0.4.68)
- Added "hidden" field to profiles to hide them from the user interface (io:4.0.4.12, hp:4.0.4.14, hw:4.0.4.27)
- Added scrollbars to metadata section of export tab of panel (hp:4.0.4.18)
- Transfer Stream variables from PreStream's to actual Stream
- Added custom datetime filter (hw:4.0.4.30, hp:4.0.4.16)
- {job.unique} wildcard usable in INDEXED_ASSET, UNINDEXED_ASSET and ADDED_ASSET streams and after "Cosmo Get Project Assets Action (streams:4.0.4.84, co:4.0.4.27, io:4.0.4.13)
- Added a CMD Execute and BASH Execute Action next to the existing Commandline action which causes problems from time to time depending on the command to execute
  - Commandline Action is spawning an internal shell which is limited, CMD (windows) and BASH (MacOS/Linux) use the desired shell
- Added Cronjobs (HK -> Cron) to Helmut:
  - Cronjobs support schduled execution of TASKS and ActiveDirectory Syncs
  - For existing installations, patch your Docker Stackfile with:
    - curl -s https://repo.moovit24.de:443/install/patch-cronjob.sh | bash
    - If you plan to use ActiveDirectory Sync via Cronjobs, you need to modify existing AD Groups in Order for them to work. Just click and unfocus first ActiveDirectory Groups field.
- {user.ip} wildcard to resolve a users real IP
- Stratus Transfer Asset Action to trigger transfer in Grass Valley's legacy Stratus system (and monitor those)
- New icons for the Adobe applications
- Added scrollbars to multiselect overlays (hw:4.0.4.49, hp: 4.0.4.24)
- Added "job set project id action" (streams:4.0.4.97)
  
### Fixed
- Leaving Edit Profile Dialog via ESC and reopen another profile -> the correct profile settings will be loaded instead of the previous opened ones (hw:4.0.4.1)
- Improved special character support in wildcards (streams:4.0.4.1)
- Problem with control characters in Mediainfo JSON output on Windows
- Importing clips by importing a bin via cosmo tab in helmut panel does not longer overwrite existing clips in project (hp:4.0.3.29)
- User was not added to group when preselected using Add User Dialog (hw:4.0.4.2)
- Cancel All did not cancel all upload jobs (hw:4.0.4.2)
- Could not add the same node twice to the dashboard within streamdesigner (streams:4.0.4.4)
- File chooser results in input fields have not been saved when not clicked into the field (added focus) (streams:4.0.4.4)
- Fixed bug where navigating from tag field inside add project dialog causes the word Tab to appear in tag field (hw:4.0.4.2)
- Changing between products and navigating to preferences tab -> product related preferences will not disappear anymore (hw:4.0.4.2)
- Preferences would not load automatically after login in (hw:4.0.4.8)
- XML/HTML Tags are now shown in Nodes (streams:4.0.4.28)
- Added URL Encoding doe SwatIO node - uploads could've failed depending of the file(name) to upload
- Missleading message when only reserved license slots were available
- No overwriting of user specifications for active directory sync whenever new users are imported to helmut (users:4.0.4.3)
- All other objects than user objects will now be skipped during active directory sync process (users:4.0.4.3)
- Client would drop connection to server when trying to execute (large) Streams > 10MB (license:4.0.4.5, linux: hc:4.0.4.6)
  - Requires client rollout!
- Wildcards would not resolve backslashes and other regex characters (streams:4.0.4.41)
- Reworked canceling of jobs (streams:4.0.4.41 io:4.0.4.8 license:4.0.4.7)
- Added skip for native AE elements for project index (co:4.0.4.13)
- Autosync asset into project in windows environment -> pathmapping added to message bus response (hp:4.0.4.11)
- FX Metadata page would show "Add Metadata Set" instead of "Add Metadata"
- IO Metadata page would show "Action" instead of "Delete"
- PreStreams are now hidden from Cosmo Profile view as Cosmo has no PreStreams
- Commandline parser does no more add quotes when not needed to a command
- Removed > sign from export modal (hw:4.0.4.22)
- \E is no more causing problems in wildcards (stremas:4.0.4.61)
- Saved Streams content would sometimes be "Success Action" only instead of the actual stream
- Cosmo Get Assets For Project node is working properly again
  - This node looped over one asset only instead of all found assets
- FX Dashboard now shows correct IP for clients using autoconnect
- Fixed path issue within Command Line executor node (streams:4.0.4.69)
- Fixed fps condition to work with floating point numbers (streams:4.0.4.70)
- Fixed metadata sorting for fx and io metadata table views (hw:4.0.4.25)
- Changed payload cleanup for Json extract node to avoid creating functional chars by having backslash following by a numerical char like '\1.mxf' (streams:4.0.4.75)
- LowerCased node names have been uppercased
- Fixed bug where hitting 'Enter' in the EnterTextDialog would refresh (redirect) the page
- Re-added sorting to filter values
- Relative TODAY filter to not act like TODAY_GREATER
- Pasting nodes to the streamdesigner does no more paste nodes outside of canvas
- {file.content.?} now supports {path.to.win/mac.?} nesting
- Tag typeahead field is working again in addProject dialog and filter field (hw:4.0.4.30 hp:4.0.4.16)
- Removed filechooser icon from numerical input fields in streamsdesigner (streams:4.0.4.85)
- Covered duplicate bin creation by adapting synchronization process of "normal" assets for bins as well (co:4.0.4.18, hw:4.0.4.34)
- Add proxy to an asset and index project before synchronization -> proxy path will remain instead of beeing deleted (co:4.0.4.19)
- Project Metadata Changer Action did not trigger valueObject caluclation for DATE and DATETIME Metadata to search in those relativly
- Choosen filter value will no be translated (hw:4.0.4.41, hp:4.0.4.18)
- Change variable value in prefenece tab will now be updated in web ui (hw:4.0.4.42)
- Saved dashboard filter in cosmo product are now listed inside the filter menu (hw:4.0.4.43)
- Set initial sort order of assets in project detail page to name ascending and fixed multiselect (hw:4.0.4.48)
- Fixed scrollbar overlapping footer and not reachable metadata fields in export tab (hp:4.0.4.22)
- Edit project -> delete the tag will now really delete the tag entry(hw:4.0.4.48)
- Removed unused buttons cancel, save, confirm that belongs to filter dialog from save filter dialog (hp:4.0.4.22)
- Further optimized the synchronization process to enable correct behaviour when it comes to intermediate manual sync trigger (co:4.0.4.23, hp:4.0.4.23)
- Horizontal aligned different input fields in filter dialog in panel (hp:4.0.4.23)
- Setting a datetime metadata for an asset that should be uploaded to a project is now possible (hw:4.0.4.49)
- Fixed "personal" filter for projects page (hw:4.0.4.49, hp:4.0.4.24)
- Fixed Jobs count pagination for solo and multiple delete jobs (hw:4.0.4.49, hp: 4.0.4.24)
- Calls to Premiere (Render, AAF etc) timed out after 2 minutes.

### Changed
- Removed ' and " from allowed characters for projects (hw:4.0.4.2)
- Cancel All button now also clears the list in the Upload dialog (hw:4.0.4.2)
- All Node names to camel case (streams:4.0.4.4)
- Moved EVS Node's to THIRD_PARTY category
- Changed the way Streams are build and saved and reduced the size by ~85%.
  - This should make execution of large Streams faster as well
  - Requires to re-save existing streams
- Added custom.id support for Projects and Assets
- Medialoopster Nodes are now synchronizing using custom.id's instead of project/assets names (streams:4.0.4.27)
- Allowed category and template filters without group filters (hw:4.0.4.8, hp:4.0.4.4)
- Reworked the PreStream logic.
  - PreStreams are working as a client stream only now
  - PreStreams are now being executed in the same logic as normal streams. They are only shown to admin users until they either turn in a "real" job (just be successful) or are dismissed
  - You can add separate render nodes for PreStreams so they are executed quickly - dedicated PreStream rendernodes should NEVER do long living / heavy tasks - thats why asynchronous actions are not "supported". (streams:4.0.4.32 io:4.0.4.3 hw:4.0.4.13)
  - PreStreams always have priority over "real" jobs when a rendernode is asking for a new job - no matter in which order they have been added
- Changed scrolling of panel to whole view instead of table view only (hp:4.0.4.5)
- Replaced cross in filter dialog at top right with "Delete", "Cancel" and "Confirm" buttons (hw:4.0.4.13 hp:4.0.4.6)
- Completely refactored synchronization process of assets to projects (hp:4.0.4.7 co:4.0.4.7)
- Folder Delete Action has now conditions if folder is not empty "DELETE_ANYWAY", "SKIP", "FAIL"
- Active Directory perform action api endpoint is now expecting a uuid of the groups entry for which the action should be performed (web:4.0.4.23, users:4.0.4.6)
- Added "Keep original name" checkbox to "Cosmo Add Asset To Project Action" to avoid changing the asset name during synchronization process (streams: 4.0.4.68 co:4.0.4.15 hp:4.0.4.13)
- Added autocomplete behaviour to tag filter in fx (hp:4.0.4.13 hw:4.0.4.25)
- Added query parameter to AD sync endpoints to avoid sync result message -> Preparation for cron job (users:4.0.4.11)
- Add proxy will now trigger an autosync of this proxy if the corresponding project is open otherwise it will have the sync behaviour of its highres whenever the project will be opened (co:4.0.4.20)
- Updated the adobe product icons (hw:4.0.4.48, hp:4.0.4.22)
- Disabled the possiblity to save empty filters (hw:4.0.4.48, hp:4.0.4.22)
- Landing page for HK product is now projects page instead of dashboard (hw:4.0.4.49)

### Removed
- Removed hardcoded Job Status Update from Execute Extendscript Action
- Temporary removed toggle recursive synced by triggering set (un)sync on folder (streams:4.0.4.84, co:4.0.4.27, io:4.0.4.13)
- Removed the posibility to rename an access preset since it will not be updated in the user objects (hw:4.0.4.49)

## [4.0.3-release-1] (stable release)

### Fixed
- Client would drop connection to server when trying to execute (large) Streams > 10MB (license:4.0.3.7)
  - Requires client rollout!

### Change 
- Removed parent bin selection for autoimported clips (hp:4.0.3.30)

## [4.0.3-release-0] (stable release)

### Added
- OAuth authentication
- Open Logs (folder) from client menu
- MD5 checksum to streamEngine download
- Advanced error output when a client failed to execute a stream
- Uninstaller (windows only)
- Endpoint check by product in webinterface
  - It was possible to reach the project page within IO for example even tho it doesn't exist for IO
- Added relative date filters to panel
- Added a logging entry for the case that a rendernode is not part of the group, which is assined to the io profile in cosmo
- Support for Premiere 14.3.1 (requires hp:4.0.3.6 to work)
- Drag wires in Streamdesigner everywhere onto a Node instead of the connector only
- Nodes are now at 95% opacity to make wires visible underneath
- File Increment Name Action and Folder Increment Name Action
- Enabled Add Project Button in restricted mode (experimental)
- Custom confirm dialog when switching to another Stream with unsaved changes
- Placeholders to input fields in Streamdesigner (used for example input data)
- Searchbar to Metadata
- Extended descriptions to every input for all Nodes
- The active project has been added to the project select dropdown in the Helmut Panel
- FFMPEG Render Node Action to render with ffmpeg
- FFMPEG to Helmut Linux Client (v4.0.3.7) to /usr/local/bin/ffmpeg
- Audio Streams Condition to check how many audio streams exist in a file
- Wildcard {project.locked.status} that returns the status of a lock (LOCKED, HOUSEKEEPER, ARCHIVED, RESTORED)
- COPY and MOVE Profiles to Housekeeper
- Delete All Button to Upload File Dialog to clear the list of selected files
- Wildcard {job.mimeType.?} where ? must be replaced by an extension. Will be replaced with the mime type for the given extension on the fly (defaults to DATA)
- Server sided FileChooser to Streamdesigner
- System wide Backup and Restore to Preference Tab
- JSON Payload Extract Action
- Optional Group to Watchfolders to enable new jobs to be attached to a group a user can be part of (visibility in dashboard)
- Regex Apply Action to sanitize strings (eg. projectnames)
- Mediainfo Json Action (will return the complete Mediainfo of a File as JSON, so you can extract values)
- FFProbe Json Action (will return the complete FFProbe info of a File as JSON, so you can extract values)
- The table sort order will be reset to default and the free text search string will be deleted if "Clear current filter" has been triggered (hp:4.0.3.13 hw:4.0.3.22)
- <s> If an asset is imported into the opened premiere project via cosmo tab in panel the same asset will now immediately be added to the database to keep the web frontend synced with the project content (hp:4.0.3.13 hw:4.0.3.22) </s> removed, will be implemented in next version
- XML Generator Action to export XML's in a desired format out of Helmut informations (project, job and user)
- File/Folder Appearing Condition - monitor if one or multiple files/folders appear or disappear
- Illegal Character Filter to 'Add Metadata' dialog
- Added ID search filter to search projects by its id (hw:4.0.3.28 only by filter; hw:4.0.3.31 also as freetext search)

### Fixed

- Only 5 Watchfolders would be shown in Webinterface
- Autologin would fail on Windows and Mac
- Non admin users can now save the amount of items listed
- Relative date filters can now be saved and restored
- Creator value typeahead is now working in all products
- Cosmo can now execute Streams again without problems
- Gobal variables (preferences) are updated correctly in the webinterface
- Notification after AD-Syncs will be sent back to request user only
- Profiles in Cosmo can be filtered by group
- Node outputs cannot connect to same Node's input
- Client does no more break when a stream times out
  - We changed the logic how stream requests are being recveived and executed to avoid the client to crash if a GENERIC or IO stream times out (client v3.0.3.8, linux client mcp_hc:4.0.3.8)
- All Jobs would be populated to a users dashboard by the message bus - they are now filtered correctly.
- Ctrl key can now be used to select multiple entries on windows (currently admin only; will be reworked)
- Regex Apply Action will now find the regex provided
- Added alphabetically sorting of fx filter keys (hp:4.0.3.13 hw:4.0.3.23)
- Fixed the creation of multiple autoimport jobs for same asset if it has been imported via parent folder or as fcp xml (hp:4.0.3.13 hw:4.0.3.22)
- Fixed asset import from panel into root level of current project (import without any bin selected) (hp:4.0.3.14)
- Index project with clipProjectItems without nodeId is now working without throwing null pointer exception (co:4.0.3.6)
- Saving a task with a relative date filter set is now possible (hw:4.0.3.26)
- Filtered out sequences from autoimport job adding if a sequence is imported as a child project item of a folder (hp:4.0.3.15)
- Sequence Export would write the extracted sequence project used for rendering to C:\HelmutIO on Windows with premiere >= 14.3.1
- Cosmo projects detail page: Navigate into bin which was preveously searched by freetext search is now working (hw:4.0.3.28 hp:4.0.3.17)
- Active directory synchronization message should now always appear (hw:4.0.3.30)
- Reenabled metadata relative filter search for objects (projects and assets) that have more than one metadata entry set (fx:4.0.3.8 co:4.0.3.8)
- Fixed Domain Controller bug for Active Directory module for newer active directory version -> tested with Windows Server 2019 (hw:4.0.3.32)
- Reenabled metadata relative filter search for objects (projects and assets) that have more than one metadata entry set in frontend (hw:4.0.3.33, hp:4.0.3.26)
- Edit project dialog is not removing existing tag information (hw:4.0.3.33)
- Reenabled default profile selection for panel export, and web import/export (hw:4.0.3.33, hp:4.0.3.26)
- Node outputs of "Cosmo Get Project Assets Node" (streams:4.0.3.65)

### Changed

- Import assets from project and push assets to project using the panel will now ignore the bin structure
  - Folder will still be read out recursively but the assets will be placed in flat hierarchical manner into the destination,
    which is the current selected folder for import (or root if nothing is selected) or the target folder for push assets workflow
- It's now possible to have mutliple filters with same key
- A project sync will now set all assets to synced even though an error occurred while import or sync is performed
- Remove metadata copy to parent bins, which were created from asset breadcrumb
- Recursiv Folder uploads are now being uploaded to the relative path - use {job.source} to get the path to the file relative to the upload folder
- The Panel Dashboard will now only show jobs of the currently open project, no more all in a users groups
- Text typed values of filters will now be selected if the text field is clicked -> directly overwriting previous value now possible (hp:4.0.3.13 hw:4.0.3.22)
- Changed default comparator to CONTAINS for all text based filter values (hp:4.0.3.13 hw:4.0.3.22)
- Add 'replacer' to Regex Apply Node (replace found matches with a string or nothing)
- Project Create Action and Project Import Action Template descriptions and added Type field
- <s> Assets that will be synced into a premiere project will be automatically set to be synced as soon as they are requested from database to avoid stucking syncronization queue (hp:4.0.3.20 co:4.0.3.7) </s> -> removed, will be implemented in next version

## [4.0.2-release-3] (stable release)

### Fixed

- Housekeeper could not save relative date filters
  - Known issue: Saving the filter as a preset will not work in 4.0.2
- Sequence Export would write the extracted sequence project used for rendering to C:\HelmutIO on Windows with premiere >= 14.3.1

## [4.0.2-release-2] (stable release)

### Added

- Support for Premiere >= 14.3.1

## [4.0.2-release-1] (stable release)

### Fixed

- Only 5 Watchfolders would be shown in Webinterface
- Autologin would fail on Windows and Mac
- Non admin users can now save the amount of items listed

## [4.0.2-release-0] (stable release)

### Added

- Rendernode(s) to job overlay if there are any and less then 10
- Title and saved/unsaved status to title for Streamdesigner
- Group filter for CUSTOM_FX and CUSTOM_IO events
- Markers are now being synced back to CatDV
- Switch for changing proxies of all highres assets or only for the ones inside one project
- Support for a comma separated list in the Email Output Node
- Version check to Stream Export/Import
- Warning dialog if stream could not be saved
- 'Delete all existing streams' to stream importer
- ConflictRule to FolderCreateCondition and FileCreateCondition
- {job.breadcrumb} for Cosmo Get Assets Node
- Updating a project's name, tag, group, category, template and metadata in realtime from within a stream
- Updating a jobs' metadata in realtime from within a stream
- New {project.locked} wildcard (results in true/false)
- PRESTREAM's to filter IO jobs in advance, like Autoimport or Watchfolders (extensions for eg)
  - New feature called PreStreams.
    Whenever you setup an IO Profile, you can optionally choose a PreStream (new Stream Event in IO) that will be executed before the Job is published.
    This can be either a client or a server Stream. It’s an generic stream so it should NOT be used for heavy tasks (since multiple might run simultaneously).
    If the Stream fails, a job will NOT be created and an error message will be thrown in the panel. You can use the Job Status Action to set the job to FAILED or SUCCESSFUL (or QUEUED) right away.
    You can also use the Job Delete Action which will delete the Job silently, no errors, no Job in the Dashboard etc. Perfect for unwanted extensions / paths during Autoimport or Watchfolders. Keep in mind that it's hard to debug for a user why a job does not show up (only debuggable in stream debugger)
- Stream name and Rendernodes to Watchfolder profile chooser
- Sort users per default by username and allow sorting by username and displayname
- Added housekeeper actions to type filter of dashboard tab
- <s>Search assets over Projects in new 'Assets' tab and jump between this page and the project details page</s>
- Added current filter engine from web to panel
- Set maximum results to 25, 50, 75 or 101 for Projects, <s>Assets</s>, Users and Dashboard
- Wildcards in upload path and temp upload path in CO preferences
- {job.breadcrumb} for Exports and Autoimports
- HouseKeeper endpoint (new microservice)
- Tasks to HouseKeeper for automated mass housekeeping (experimental)
- New Traefik version 2.2
- Automatic project save after a manual project sync has completely been finished
- wildcard {job.mimeType} after Cosmo Get Assets Action
- Job Priority Action (useful for preStreams)
- INCREMENT_NAME to File Move Action, File Copy Action, Folder Move Action, Folder Copy Action
- Possibility to trigger index project inside a duplicate project stream
- Toggle all switch for assigning metadata to all groups (fx) or metadatasets (io) at ones
- {job.last.proxy} wildcard after Get Assets From Cosmo Node holding the last used proxy path when setting a new one
- {node.result.?} wildcard to use results of previous nodes (including error messages; requires to re-save all streams)
- Jump from StreamDebugger to Stream and highlight according Node by clicking on the thumb (requires to re-save all streams)
- Scrollbar to overlays
- Add .srt file support
- {user.os} wildcard (will be replaced by the client's OS, win or mac, requires client client >= 4.0.2.13)
- Project Metadata Changer and Job Metadata Changer nodes can now set metadata values, that didn't exist in the project/job object
- Relative date filters for projects modify date in FX and for jobs start date in IO
- node.result to File Move Action
- Automatic reconnect if autologin client looses connection
- Toggle All Button to Streams and Profiles
- Overlay-Scrollbar to Streams, Assets and Profiles
- Wildcards to Node pallet in Streamdesigner
- Descriptions to node inputs to Streamdesigner
- Better support for automatic reconnect after server restart for autologin clients
- After a project deletion all project asset references will be removed for project assets
  - Removing projectId and group entries
- Debugger to Streamdesigner (debugs only open stream)
  - Support for asynchronous streams
  - Added highlighting
- Metadata preresolve functionality to metadata filter
- Preference for the temporary project import path (required for scales installations)
- Project Metadata Remove Action to unset a metadata value
- Job Metadata Remove Action to unset a metadata value
- 'Suppress DELETE_PROJECT event' to Project Delete Action node.
- Append ?product=co (or io, fx, hk) to the url to point shortcuts directly to the right product. Works for login too.
- Helmut automated test suite
- Project File Download and Upload Action

### Fixed

- Installer is now using sudo to install Panels
- Usernames / Passwords with several special characters will no longer cause problems during login
- Panel where tabs would not load sometimes
- Error in Projectfile Copy action in duplicate streams
- Upload would not work if last used profile does no more exist or is not available
- Added creator and lastModified value to free text search
- Reworked UNC based path mapping for index project workflow
- Added missing filter keys for all products
- Apostrophs in filepaths are supported for asset sync in panel now
- Restore last used profile in upload asset modal is now working properly
- InOutPoints will now be set correctly also for assets with timecode offset
- Stream engine could run out of memory when using big streams (memory leak)
- Save and delete filter templates in housekeeper now possible
- Import Sequence from cosmo panel is now working again
- Fixed one issue with UNC path mapping and added pathmapping for proxy path for index project workflow
- Completely reworked metadata validation
- Boolean typed metadata filters are now working properly
- Added modified by and creator to freetext search of projects view
- Value of tag field in add project dialog will now be save even if it has been the last field modified before add button was clicked
- If key of filter bubble change the comparator field will now be prefilled with the first allowed entry if previous entry is not available for new filter key
- Check for duplicate non AD usernames to avoid duplicate entries in database
- New (never saved) tasks would not be saved if tested before saving them
- Added metadata field validation for web export asset dialog and profile filed of add watchfolder dialog
- Changed comparators of createDate filter to date related ones instead of string related
- A sequence that has been pushed to another project via drag and drop in cosmo panel will now be synced into the destination project
- Fixed bug where export of streams would drop it's stream-design
- Folder Move Action's conflict rule DELETE_EXISTING is now deleting properly
- Added LOGIN access preset to all products
- SRT files will now be relinked during project sync
- Added load dialog for addUser modal to avoid multiple button clicks
- Importing stream(s) no preserves UTF-8 characters
- {user.os} is now available in all events
- Add support for empty folders to JobFolderCopy Node
- Removed unwanted overlay appearance for buttons that change the stream order in IO, CO and HK streams tab
- Editing an existing filter bubble from type multiselect is now possible
- Select and Multiselect metadata fields in export tab of panel are now beeing highligted if validation fails
- Blocked multiple click add button in add user modal and changed backend logic to avoid the creation of duplicate users
- Assets from type CAPTIONS are now beeing relinked during project sync
- Fixed non responsive chip filter view in dashboard tab on initial panel load
- Profiles would not be filtered in HK projects menu
- Deleting a prestream from a profile will not cause an exception inside the panel telling that the prestream cannot be found

### Changed

- Write File Output Node supports [NEWLINE] now
- Sequence multiselect inside export tab of panel has now two icons for set selection either to active sequence or selected sequences in project view
- Composition multiselect inside export tab of panel has now two icons for set selection either to active composition or selected compositions in project view
- Clean current filter in projects view of helmut will now also reset group, category and template filter to default
- Changed default sort order of assets from descending modify date to ascending name
- Replaced "Import Project" preference with an accesspreset entry
- Watchfolder is now writing a lock file instead of touching it, to support curlftps (ftp) workflows
- It's now enabled to let groups, products and accessPreset for users empty when using new Active Directory module
- Active directory user import -> helmut user displayname can be binded to one of the ad fields username, displayname or email
- Changed active directory response message and added logging for evaluation
- Enabled blank fields for active directory sync
- In add project dialog if a project is selected for import the name of the project will be filled into the project name field if it is empty
- Changed the way to match cosmo database content with the premiere project content in terms of making nodeId information available for project index
- Limit the request for unsynced assets in panel for project sync workflow to 500 at a time and limit the unsynced assets counter to 500 as well
- Reworked Streamdesigner
  - Documentation with release Q2 end of june
- Active Directory sync will now push the result to the webinterface via message bus instead of direct response
- Value field of creator filter for fx (projects) and io (jobs) is now a typeahead field
  - Suggestions will be provided after two chars have been typed
- Sort order of Manage Groups dialog
- Added dynamic max with setting of chipContent inline modal to proper display filters
- Cosmo Change (Project) Asset node has now a checkbox for autoimport triggering
- Panel minimize-mode to be < 75px (was 400px)
- Wildcard dialog in Streamdesigner will now open by hitting ctrl+space instead of {
- Splitted Active Directory sync action into add, update, remove
  - Add will only add users to helmut and add them to groups
  - Update will only update products, access presets, role and display name binding
  - Remove will only remove users from groups and will NOT delete users from helmut
- Active Directory Add option now supports also Update if a user has been imported initially
- Removed IS_SMALLER and IS_GREATER comparators from string typed filters
- Added autosync checkbox for "Cosmo change (project) asset" nodes
- Disabled CO projects menu in restricted mode
- Added CREATE_PROJECT user access preset to co products

## [4.0.1-release-1] (stable release; fixed)

### Fix

- Bug where panel tabs would not load sometimes
- Bug where Stream engine could run out of memory when using big streams (memory leak)
- Bug where Cosmo would have problems with unc paths
- Bug where panel failed to import sequences on windows in some circumstances
- Various small fixes

## [4.0.1-release-0] (stable release)

### Added

- User can now change their password from the user custom menu
- Add push assets functionality
  - push assets (BINS, COMPS, SEQUENCES, FOOTAGE) between AfterEffects or Premiere Projects or cross plattform
  - simply drag and drop selection from projects window into project details page of the cosmo tab
  - bins will be read out recursively skipping unsupported items
- Add timestamp to social media downloads to force unique filenames (enables re-download)
- Add pathmapping to watchfolder
- Add new access presets (user and group)
- Add new filters
- Add user email to webinterface, including change email (action menu)
- Add wildcard:
  - %user.email%
  - %job.user.email%
- Add curl to all images for Docker Healthchecks
- Add typeahead for tag field of add project dialog
- Add 3000ms delay to connected stream
- Add use result as current project to Create Project Node
- Add install as service to Helmut client windows installer
- Add Single Sign On (windows only; experimental) - requires ActiveDirectoryAuto Module - [Show Preview](https://sev.moovit24.de/uploads/TW9vdklUIEdtYkg/XOiszDzFt6nLjcBlOFKnFdZUj691UBkVVGEnC2J2TpW6A56rnhpMCxxDLo29iRNGpnnmkwYA83aJwR7Hts1RWQr5gt9VipPoSiC3/#5bcd21ab9e93d089d98115888b7db5931321789799a8bcfb026bf8f77cb2ef6d)
- Add pre resolve metadata [Show preview](https://sev.moovit24.de/uploads/TW9vdklUIEdtYkg/TRp2uJ8BCaveU3DweDACEjvUw4guPaaFxJa85RemIurVivX7P7wiGSuiU4xUsJaHkekmz4hUeXTcr9wtOHzfjIiJCj6y7VtvhPF6/)
- Add license usage to FX dashboard
- Add (selected) Streams export/import
- Add exclusion tags for wildcards, eg. "{project.name} [<] do not map {project.name} here [>] {project.name}" -> "my-project-name [<] do not map {project.name} here [>] my-project-name" ([<] ... [>] will be removed)
- Add new Active directory Module
  - Use multiple AD Hosts (Controllers) with fallback functionallity
  - Syncronize users of different AD groups with individual helmut groups
  - Use browse dialog to browse through AD content
  - Old AD still working
- Add {path.map.to.win.?} and {path.map.to.unix.?} functional wildcards. Using these wildcards will disable automapping the complete string!
- Add confirmation dialog to logout if there are active uploads running
- Add password to helmut-updater, please contact support@moovit.de for further informations
- Add {generate.uuid node}
- Add INDEXED_ASSET trigger to Cosmo Project Index Node
- Add advanced indexing to Cosmo Index Node
- Add newline \n support to Write To File Ouput node
- Add role chooser for Auto Active Directory Module (default USER)
- Add new inOutPoint attribute for asset which enables setting in and out points on clips after syncing into project
- Add new filter logic to dashboard and cosmo and removed several issues:
  - user.displayname is now creator
  - filter dropdown entries are now sorted
- Extended mime type detection for incomming assets
- Add extension check for template when calling createProject endpoint (from node for exmaple)
- Add FCPXML render support via HelmutIO
- Add info if projects are opened without helmut (no panel available)

### Fixed

- Resolution condition node works properly
- Typeahead typed metadata works properly
- Mandatory metadata fields are now also checked within the panel
- Mandatory metadata fields are now also checked within Cosmo weupload
- Profiles to group assignment and order at profiles tap of webinterface works porperly now
- !Single jobs could be handed out to multiple rendernodes simultaneously
- WildcardCondition now matches in the correct order
- Access preset to group assignment now woking properly
- Rendernode assignment to profile is now working properly (third and following entries won't have double whitespaces between ',' delimiter anymore)
- Properly handling imported assets that has been moved inside Premiere or After Effects project view before project scan -> no duplicate asset entries, one online one offline
- Display of filter lines in create search filter dialog is now working properly
  - There was an update issue leeds to wrong filter names when lines got deleted
- {user.name} in profiles is now working same as %user.name%
- Added asset stream will now have correct job information set
- 0 B size and default 1970 date are now replaced with '-' character
- Index project where effects have been used can now be indexed without any issues
- Moved delete saved filter icon (recycling bin) in front of the filter name to enable deleting filters with long names
- UNC path mapping within index project logic is now working properly
- Project items of synced cosmo assets will be renamed after cosmo asset names
- Cought case where synced asset path is not reachable -> loading dialog will be closed now
- Multiselect metadata fields in jobs etc. will no more cause problems after adding pre-resolve feature
- Housekeeper assets search is now working properly
- Event trigger node in Streamdesigner would always show an old title then renaming a node or importing a stream
- Event triggers in Streamdesigner will now always show the latest, sorted list of events
- Mimetype detection for M4A and OMF files is now working properly
- Validate user against Auto Active Directory Module now working properly
- Certificate trust for Auto Active Directory Module now working properly
- Saving dashboard filter from HK is now possible
- Sequence and Composition which names includes ":" will now be displayed correctly inside the select dropdown
- Autoimport as well as asset sync is now working properly for premiere versions 2018, 2019, 2020
  - For 2020 new World is supported
- Added database index for date sort function to avoid mongodb buffer overflow bug
- Added path mapping for proxy import
- Autoimport groups would not be checked when choosing an autoimport profile for an open project
- ActiveDirectory Auto sync will now trigger CREATE_USER for each new user
- Single quotation mark within a filename does not cause errors inside the panel
- Add priority and source to filterlist for dashboard filters
- Rendernode could get a job it isn't responsible for
- FX and CO Server Streams could not send emails (via Node)
- Sequence and/or profiles could not be choosen in the export panel
- Metadata did not behave properly in AddProject Dialog

### Changed

- Improved filesize filter for projects and assets -> B,KB,MB,GB,TB are now suported as value suffix
- Project sync process is now working in packages of 25 assets
- Improved upload counter and progress which will be resetted if no upload is currently active
- Switch between opened projects in panel can be made by new added dropdown list, previous switch icon can be used for panel refresh
- Typeahead metadata field now allows arbitrary inputs
- Message dialog can now show large text
- SwatIO channel id is now type string to support wildcards
- Reworked Access Presets and added APs for all products
- All media files of an imported folder in AE or PPRO will now be added to autoimport list
- Wildcard replacer to support all kinds/levels of nesting now
- Enlarged input fields in Streamdesigner are now better readable
- Reworked project related filters
  - Group, category and template filters are now fixed filters and their values are dependent to each other
  - Removed edit filter dialog and replaced it with quick pick inline dialog
  - Moved filter saving and restoring functionality to main project page -> it will be find inside the quick restore menu
- Metadata 'Values' and 'Default value' are now being edited using an overlay to have more space horizontally & vertically
- A renoderNode (pool) can now be set when adding a new job to IO instead of using the pool of the profile
- Create Job Action can now set renderNode(s) within the node (empty = read from profile) to designate a new job to a node (pool)
- Multiselect of projects and jobs is now only allowed for admin users
- Private project togle is now only available for admins or the creator of a project
- Renewed IO and CO filters and removed all/any switch
- Copying nodes via browser tabs is only possible when using SSL (or localhost) - this is a browser restriction we can not work around
- Add asset to project will now update project size value
- Extended mime type list
- Updated node's using AME or Premire default value to v2020
- Add path to premiere lock file to Premrie Native Lock Action
- Project size will now be live updated with every asset which has been added to cosmo
- Removed all/any switch for all searchfilter
- The way we detect the logged in domain and user for Single Sign On

### Removed

- Hardcoded (double) project name check from duplicate project endpoint

## [4.0.1-2020-02-04-155216] (unstable)

### Added

- Warning to Streams containing deprecated Nodes to Streamoverview
- SwatIO as module and node
- Implemented multiselect for jobs in dashboard view (only cancel jobs is supported right now)
- Implemented "Import Folder" functionality for premiere and after effects panels
- Added Minimized panel view where only sync icon is visible - activates automatically with shrinking panel width
- Added environment HELMUT_LICENSE=<License token> which has a higher priority then the Database
- Added license count -1 for an inifite amount of concurrent users
- Added Node:
  - Cosmo Move Asset (global)
  - Cosmo Move Project Asset (for a single project only)
  - Premiere alert with timeout (client version >= 4.0.1.92 req)
  - Premiere prompt with timeout (client version >= 4.0.1.92 req)
  - Premiere confirm with timeout (client version >= 4.0.1.92 req)
  - Social Media Download (req social media downloader; third party by moovit.de)
  - Create new project
  - Import existing project
  - Create new Job (create jobs from withing streams)
- Copy node between Streams (Chrome only)
  - As a workaround for Firefox and Safari, you can paste into the "Search" field to create the node
- Added uprocessed asset property to enable triggering autoimport streams for assets synced from cosmo
- Added Helmut autologin download to users action menu
- Released helmut linux client (docker; experimental)
- Added path-mapping / variable insert at desired location (splice)
- Added MD5 checksum wildcard - %file.md5.?% (CPU intensiv!)
- Added recursive toggling synced if parent bin has been set to synced / unsynced
- Added restricted mode (non client mode) to Webinterface (use project tab without helmut client, eg from phone)
- Added 'reserve license' to users tab
- Add direct jump to metadata set from profiles tab
- Add typeahead (autocomplete) metadata
- Add duplicate stream
- Add duplicate profile
- Add link upload via Cosmo
- Add wildcards:
  - %date.month.textual% - January, February..
  - %date.month.textual.short% - Jan, Feb...
  - %date.month.textual.?% - January, February.. of input date
  - %date.month.textual.short.?% - Jan, Feb.. of input date
- Add WEB_EXPORT and WEB_IMPORT Events and Streams (you can still use IMPORT for webingest)
- Add WEB_EXPORT support for mediafiles to webinterface

### Fixed

- Export sequences from Cosmo Webinterface
- Import composition to premiere project
- Simulaniosly add different project types (aepx,ppro,sesx) leaded to empty names for at least two created projects
- Parentheses are now working as expected in wildcards
- Assets without mediatype (data assets) create an infinite loop when add to something else then root (/)
- Modified date for bins inside assets tabel in webinterface and panel does not show "invalid date" anymore
- Metadata sorting works properly
- Asset export is now sending the asset instead of the project path

### Changed

- Reworked project sync icon (number and icon will now trigger the sync event; added animation to icon to call attention to new unsynced assets)
- License tab in Webinterface is now showing the major version
- Removed modules from license tab
- Hiding JWT token in License tab
- Wildcard %local.profile.?% to accept numbers and decimals (eg. 12 or 12.0)
- Width of 'Type' column for Metadata
- Web sequence export is now using WEB_EXPORT profiles instead of EXPORT)

### Removed

- Removed action entry Open for force-locked projects
- Regex from metadata

## [4.0.1-2019-12-18-122818] (unstable)

### Added

- Job status CANCELED
- New Panel-Dashboard equal to Helmut Web
- Log entries to each Job (open via Overlay)
- Support for assets with same source and project id
- Unique assets per project filter for housekeeper
- Move asset endpoint which changes all asset filepaths matching sourcePatch and sets asset to unsynced
- CHOOSE_FOLDER Metadata type (IO only)
- Updated API documentations to [Helmut4 API Docs](http://repo.moovit24.de:8080/)

### Fixed

- Post Kill AME is now working properly
- Adding assets to Flow projects that contain assets on the root level is now working
- Preference Tab in Helmut Webinterface is now working
- Profile select in Cosmo uploader stuck in certian situations
- Metadata sorting broken when adding/removing metadata entries from other groups
- Metadata CHOOSE_FOLDER in Premiere on Windows would return paths with forward slashes (Adobe special)

### Changed

- Cosmo Database structure (requires reindexing of existing projects to work properly)

### Removed

## [4.0.1-2019-12-06-180706] (unstable)

### Added

- AEFT composition export
- AEFT - autoimport, manual import and import from cosmo tab for assets, sequences, compositions, bins, folders
- PPRO - autoimport, manual import and import from cosmo tab for assets, sequences, compositions, bins, folders
- AEFT & PPRO - autoimport, manual import and import from cosmo tab for compositions into PPRO and sequences into AEFT
- Watchfolder to IO
- client version to FX dashboard for connected clients
- Streams for Cosmo
- ADDED_ASSET (called after asset has been - externally)
- INDEXED_PROJECT (called after project has been indexed)
- flat hierarchically folder view for Cosmo Projects details view for WI and Panel
- webupload into Cosmo project detail view (requires HelmutIO)
- „create folder“ into Cosmo Project detail view (Autosync: false)
- local database Logging (removed Elasticsearch and Kibana)
- client version to FX Dashboard
- autologin feature for HelmutClient (dedicated rendernode-feature)
- „POST_CREATE_PROJECT“ Event to FX
- MediaInfo Condition Node FPS
- MediaInfo Condition Node Codec
- MediaInfo Condition Node Resolution
- MediaInfo Condition NodeBitrate
- MediaInfo Condition Node Audio Tracks
- MediaInfo Condition Node Color Space
- Searchfilters to IO dashboard
- CatDV Integration
- Create Catalog in Group (recursive)
- Delete Catalog in Group (recursive)
- Add Asset to Catalog in Group with Metadata
- Hostname to HelmutFX Dashboard
- advanced project scan (detailed sequence scan)
- sequence reference visualisation in web frontend
- Premiere WS Panel in Helmut Client installer (hidden)
- IO Server Streams (restricted)
- IO Custom Streams (via Panel)
- Node Export AAF via Premiere
- Node Export Sequence via Premiere
- Node Open File/Folder Choose Dialog in Premiere
- Node Delete Projectby ID
- Node Set Project Group
- Node Set Project Category
- Node Set Project Template
- Node Set Project Status
- Node Set temporary variable (inherits via streams)
- Export FCP XML
- Node Get project assets from Cosmo (special outputs)
- Node Job Folder Copy Action
- Wildcard %date.year.?% - Parse date by input yyyy-MM-dd
- Wildcard %date.shortyear.?% - Parse date by input yyyy-MM-dd
- Wildcard %date.month.?% - Parse date by input yyyy-MM-dd
- Wildcard %date.day.?% - Parse date by input yyyy-MM-dd
- Wildcard %string.split.#-#.?% - Split string by blank
- Wildcard %job.user.id% - User id of job creator
- Wildcard %job.user.name% - Username of job creator
- Wildcard %job.user.displayname% - User displayname of job creator
- Wildcard %job.user.role% - User role of job creator
- Wildcard %stream.variable.?% - Get a temporary custom stream variable
- Proxy Workflow
- "show in source monitor" action for premiere panel
- Icon-Product switch for Mini-Navigation mode
- Export-Sequence to Cosmo Webinterface
- support to nest wildcards
- search filter quickselect
- projects multiselect
- toggle sync / unsync asset in webinterface
- Multiproject support for premiere
- Multiproject select in fx projects view of the webinterface
- Multi-Export Sequence in panel
- Consolidated media typed asset import in panel to avoid multiple prwildcardemiere import dialogs
- priorities to IO Profiles > Jobs
- SentToTop Action Button to IO Dashboard
- cancel Job Action Button to IO Dashboard (for queued jobs only)
- restart Job Action Button to IO Dashboard (incl. running jobs = experimental)
- Metadata sorting per set to FX and IO
- client version info to Download section
- "SHOW_PROJECT_PATH" User access to show/hide the user path in the project overlay
- additional infos to upload job overlay
- red border for deprecated nodes in Streamdesigner
- deprecated warning toStream debugger for deprecated nodes
- separated nodes for project and job metadata changer
- click on Stream to Profiles to edit Streams quickly
- ALL/ONE (and/or) to Wildcard Condition
- Streams to HouseKeeper
- Profiles to HouseKeeper

### Fixed

- Profiles without render node assignment would not be processed
- „Saves“ folder could not be found if the Projects Path is Windows
- Asset will not be indexed correctly if it has been renamed inside Premiere
- License (Date) did never expire
- Users might have executed Streams that did not belong to them if two requests reached the server at the same time
- default value for BOOLEAN metadata fields (true/false) would not apply in HelmutPanel
- metadata entries in HelmutPanel could not be scrolled
- log entries „> maxEntries“ would not be deleted and no log would’ve been added
- aepx folders have been created multiple times when imported via panel
- Stream nodes „Job Update Status Action“ would fail
- Non working multiselect metadata field
- hidden metadata fields are not persistent within edit or duplicate project
- path mapping would be applied twice and lever itself
- (force) locked projects could be opened for detail view in Cosmo
- non-admin users would not see any job's in the io/co/hk Dashboard
- empty path-mappings would map url slashes
- projects could not be shift-multiselected bottom-up
- Job-cancel would require a client restart in various situations
- Preferences would be invisible when switching applications
- PathMapper would not map to requested OS
- Premiere Rendering requires EPR Preset Paths with forward slashes on Windows

### Changed

- Changed „Helmut Client is in use“ with „No free License slot available“ when no License slot is available
- Export Profiles are now being filtered by the Projects Group
- AutoImport Profiles are now being filtered by the Projects Group (first comes, first serves)
- Navigation Tabs that require administration rights in HelmutIO are now filtered properly
- The default state of „Remember me“ for Logins has been set to true
- Added thumbs (up/down) to Cosmo ProjectDetail view instead of true/false
- Removed Elasticsearch and Kibana
- The FX Dashboard now shows ‚Displayname (Username)‘ instead of ‚Username‘
- Upload paths (target + temp) are now set in the HelmutCO Preferences instead via docker compose
- Implemented folder creation by breadcrumb if asset has been added
- %path.split.#:?% Node has been changed to %path.split.#-#.?% to support ranges (including negativ)
- Icon-Product switch has been renewed to preserve icon positions
- Load last used Profile and active Sequence in export tab of helmut panel
- Changed IO, CO & HK Dashboard view
- Reimport exported timelines: markers will be added to source sequence and rendered clip will be skipped for import
- Update Stomp client and modified AMQP client in HelmutWeb and HelmutPanel for more stable live-updates
- Profiles are now sorted naturally alphabetical (HelmutWeb + Panel)
- Sequences are now sorted naturally alphabetical (Panel)
- Renamed table header IP to Client in FX Dashboard
- Renamed CUSTOM Stream Event to CUSTOM_FX
- Changed THIRD_PARTY Icon in IO Dashboard to white
- Added AME Support for 2020 to invisible AME Panel

[development release]: https://www.helmut.de
[4.0.1-2019-12-06-180706]: https://www.helmut.de
[4.0.1-2019-12-18-122818]: https://www.helmut.de
[4.0.1-2020-02-04-155216]: https://www.helmut.de
[4.0.1-release-0]: https://www.helmut.de
[4.0.1-release-1]: https://www.helmut.de
[4.0.2-release-0]: https://www.helmut.de
[4.0.2-release-1]: https://www.helmut.de
[4.0.2-release-2]: https://www.helmut.de
[4.0.2-release-3]: https://www.helmut.de
[4.0.3-release-0]: https://www.helmut.de
[4.0.3-release-1]: https://www.helmut.de
[4.0.4-release-0]: https://www.helmut.de
[4.0.4-release-1]: https://www.helmut.de
[4.0.4-release-2]: https://www.helmut.de
[4.0.4-release-3]: https://www.helmut.de
