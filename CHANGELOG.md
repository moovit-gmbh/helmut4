# Helmut4 Changelog
All notable changes for the private product [Helmut4](https://helmut.tools) will be documented in this file.

## [Unreleased]
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

[unreleased]: https://helmut.tools
[4.0.1-2019-12-06-180706]: https://helmut.tools
[4.0.1-2019-12-18-122818]: https://helmut.tools
[4.0.1-2020-02-04-155216]: https://helmut.tools
