# Helmut4 Changelog
All notable changes for the private product [Helmut4](https://helmut.tools) will be documented in this file.

## [Unreleased]
### Added
- Job status CANCELED
- New Panel-Dashboard to be equal to Helmut Web

### Fixed

### Changed

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
