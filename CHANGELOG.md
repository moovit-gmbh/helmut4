# Helmut4 Changelog
All notable changes for the private product [Helmut4](https://helmut.tools) will be documented in this file.

##   [development release]
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

### Fixed
- Only 5 Watchfolders would be shown in Webinterface
- Autologin would fail on Windows and Mac
- Non admin users can now save the amount of items listed
- Relative date filters can now be saved and restored
- Creator value typeahead is now working in all products
- Cosmo can now execute Streams again without problems
- Gobal variables (preferences) are updated correctly in the webinterface
- Notification after AD-Syncs will be sent back to request user only

### Changed
- Import assets from project and push assets to project using the panel will now ignore the bin structure
  - Folder will still be read out recursively but the assets will be placed in flat hierarchical manner into the destination,
    which is the current selected folder for import (or root if nothing is selected) or the target folder for push assets workflow
- It's now possible to have mutliple filters with same key 
- A project sync will now set all assets to synced even though an error occurred while import or sync is performed
- Remove metadata copy to parent bins, which were created from asset breadcrumb

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
- ~~Search assets over Projects in new 'Assets' tab and jump between this page and the project details page~~
- Added current filter engine from web to panel
- Set maximum results to 25, 50, 75 or 101 for Projects, ~~Assets~~, Users and Dashboard
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

[development release]: https://helmut.tools
[4.0.1-2019-12-06-180706]: https://helmut.tools
[4.0.1-2019-12-18-122818]: https://helmut.tools
[4.0.1-2020-02-04-155216]: https://helmut.tools
[4.0.1-release-0]: https://helmut.tools
[4.0.1-release-1]: https://helmut.tools
[4.0.2-release-0]: https://helmut.tools
[4.0.2-release-1]: https://helmut.tools
[4.0.2-release-2]: https://helmut.tools
