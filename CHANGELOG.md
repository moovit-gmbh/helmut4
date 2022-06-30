# Helmut4 Changelog

All notable changes for the private product [Helmut4](https://www.helmut.de) will be documented in this file.

### Before updating Helmut please consider our [update guideline](./INSTALLATION_GUIDE.md)

## [development release]
### Added
- Add PATCH to HTTP Request Action node (streams:4.1.2.24)
- Add Elements integration (streams:4.1.2.28)
- Add Helmut Core (streams:4.1.2.31; license:4.2.0.4; preferences:4.1.0.5; hw:4.1.3.30; metadata:4.1.0.6; users:4.1.0.10; cron:4.1.0.8; fx:4.1.0.8; hk:4.1.0.6; io:4.1.0.9)
### Fixed
- Adjustments to the Helmut extension to make it loadable in conjunction with Adobe Media Encoder 22.3.x (Compatible with Adobe Media Encoder CC 21 & 22) (license:4.2.0.0 hc:4.2.0.8)
- Add Project dialog is validating category dropdown (hw:4.1.3.14)
- Preferences will no longer disappear on blur of input field (hw:4.1.3.14)
- Web Upload profile is now assignable to a group (hw:4.1.3.14)
- Cancel ffmpeg render job will cancel the ffmpeg execution (streams:4.1.2.25)
- Fix Send Email Output node (license:4.2.0.1; hc:4.2.0.9; users:4.1.0.8; co:4.1.3.3; fx:4.1.0.6; hk:4.1.0.5; io:4.1.0.8)
- A combination of a "Job as Json" node with a "Job from Json" node is working now (streams:4.1.2.26)
- Kicking a user does no longer produce a server error message (users:4.1.0.9)
- Fix multi exclusive search filter combination in FX (fx:4.1.0.7)
- Fix functionality of IO button for normal user (hw:4.1.3.18)
- Fix HK multi select action button (hw:4.1.3.18)
- Fix broken custom user streams for the case that helmut stays in idle and message bus connection gets terminated by chromium based browsers (hw:4.1.3.18)
- Fix UI of upload progress for web upload (hw:4.1.3.18)
- Fix unsynced assets count in Panel (hp:4.1.3.8)
- Fix "jump to node" feature in streamdesigner for wildcard condition nodes that now present false/true instead of failed/successful (streams 4.1.2.28)
- Fix authentication of "Stratus add Asset to Folder Action" node (streams:4.1.2.29)
### Changed
- API call adjusted to prevent duplicate calls and query time increased to 5 seconds
- Windows Server was resolved as Windows NT (unknown), which has now been changed to Windows NT to allow use in Store Variables due to the parenthesis (streams:4.1.2.24)
- All conditions successful outputs will be marked with true and failed outputs with false in debug log (streams:4.1.2.25)
- Allow carriage return in all Adobe prompt nodes plus Helmut Confirm and Helmut Input Dialog (license:4.2.0.1; hc:4.2.0.9; hw:4.1.3.17; streams:4.1.2.25)
- Change logic of "Regex Match Condition" node to properly match regex (streams:4.1.2.26)
- HTTP Reuqest Action node is automatically encoding URLsend now (streams:4.1.2.26)
- Add Project.Name to IO filters (hw:4.1.3.18)
- Expose AME panel logs into file that is written into the helmut logs directory (hc:4.2.0.12; license:4.2.0.4; amePanel:2.1.1)
### Removed
## [4.2.0] (stable release)
### Added
- Add product version number (snapshot version) into the web (license:4.1.0.3; hw:4.1.3.0)
- Add metadata tab to Cosmo and Housekeeper (hw:4.1.3.3)
- Add a "Cosmo Get Asset Metadata Action" node (streams:4.1.2.4)
- Add new "Job SwatIO Upload Action" node featuring publication date including custom date and time (streams:4.1.2.13)
- Add the two missing options "Render audio effects", "Include clip copies" and add custom "Delete video clips before render" option to the "Job Render AAF in Premiere Action" node (streams:4.1.2.16; hc:4.1.0.7)
- Add new cron feature for cleanup of the jobs database (hw:4.1.3.9; cronjob:4.1.0.5; fx:4.1.0.5; io:4.1.0.7)
  - Cleanup can be made either by defining a max jobs count to keep or by relative date filter and can be setup as a cronjob that runs on a daily basis
### Fixed
- Fix $HueLampState warning which is populated on streams container startup (streams:4.1.2.0)
- All Flow nodes check for module enabled state (streams:4.1.2.0)
- Optimize node result for every render node by adding descriptions and set proper node results (streams:4.1.2.0)
- Avoid having hidden nodes in the streamdesigner node panel menu (streams:4.1.2.0)
- Fix json parse error for CosmoProxyAddActionV6 node (streams:4.1.2.2)
- Rename a stream that contains the "Stream Delete Store Variable Action" node will not force streams container to crash anymore (streams:4.1.2.1)
- Single select asset will now show same options in action menu button as it shows in the corresponding table row entry (hw:4.1.3.5)
- Heavily improved Dashboard view by (hw:4.1.3.5; hp:4.1.3.2; license:4.1.0.6; hc:4.1.0.5)
  - Reducing object size that will be published via the message bus
  - Add a queue for jobs update event in IO endpoint and remove this logic from the frontend
  - Add exclusive tag and time to live flag for rabbitmq queues
  - This could be possibly fixed
    - Out of sync dashboards of web and panel
    - Performance improvement of dashboard view
- Fix multi select for all table views (correct row selection for all sort options) (hw:4.1.3.6)
- Normalized interval for appear/growing nodes to 1 second (streams:4.1.2.6)
- AME render job will now be canceled if helmut job gets canceled (streams:4.1.2.6)
- Fix file upload issues of Job SwatIO Upload Action and limit file size to 1 GiB (streams:4.1.2.4)
- Fix failing flow nodes that use query string parameters to communicate (streams:4.1.2.11)
- Enable/disable flag will not longer be overwritten on stream save event of streamdesigner (streams:4.1.2.13)
- Improved description of Job AME render node (streams:4.1.2.11)
- Fix test suite failing when threads of old testings stay open (streams:4.1.2.13)
- Enable live view update of cosmo project panel view after adding an asset via drag & drop (hp:4.1.3.3)
- Refactored the detection of deprecated nodes of a stream and make attention icon more reliable (streams:4.1.2.13)
- Fix custom user and custom x stream ordering in fx (hw:4.1.3.8)
- Panel view does not shrink with additional sequences selected in export tab of panel (hp:4.1.3.3)
- Refactored metadata pre resolve in export tab of panel (hp:4.1.3.3)
- Enforce to have the last job update not being overwritten by previous update in new backend jobs update queue logic (io:4.1.0.6)
- Fix missing action button for some assets in cosmo project detail view (hw:4.1.3.9)
- JobFromJSON node is now able to read job that has been written from the JobAsJSON node (streams:4.1.2.16)
- Import asset via cosmo panel in helmut panel will now import the asset and change the assets name according to the name in the source project (hp:4.1.3.4)
  - If bin is imported the breadcrumb of the assets are being adapted correctly now.
- Add loop breakup logic for nested wildcards to avoid endless loops that results in 100% cpu usage per stream execution thread (streams:4.1.2.16)
- Full support of the asset import file chooser dialog for empty DVD drive (hw:4.1.3.9)
- Fix job dashboard ordering in chromium based browsers (io:4.1.0.7)
- Remove quotation marks from assetId last result inside the next path of the Cosmo Get Project Assets node (streams:4.1.2.16)
- Fix misleading table sorting of dates in several views (hw:4.1.3.11)
- Fix drag and drop feature when choosing assets from inside a bin (hp:4.1.3.6)
- Set default value "Use cron" of watch folder dialog to false (hw:4.1.3.12)
### Changed
- Do not show cron option in watch folder dialog when HK is not licensed (hw:4.1.3.1)
- Update rabbitmq message bus to version 3.9.11 (rabbitmq:4.1.0.0)
- Improve & beautify error message display in StreamDesigner (streams:4.1.2.2)
- Refactor CosmoAddInfoToSequenceAction Node to avoid failing behavior for missing values (streams:4.1.2.11)
- Add HTTP return code to the node result of the HTTP request action V3 (streams:4.1.2.13)
- Project as JSON (Legacy) node is now deprecated (streams:4.1.2.16)
- Remove fixed .gves filter for auto imports in panel (hp:4.1.3.7)
### Removed

### Known issues
- CO: problem when assigning a web upload profile to new groups, as this is not displayed in the frontend
- FX/IO: metadata reordering does not work within metadata sets
- using the "send email output" node will result in an error - delete the node from any running stream (regardless of whether it is connected or not)
- the panel does not work with AME 22.3.x (see development version / supported Adobe version list)
- when a user is kicked via the FX dashboard, this can sometimes result in an error 500 message
- messages and notifications are not displayed after a certain time due to a timeout. Temporary solution: reload the web page
- problem with the upload file paths in the Cosmo settings, as they "disappear" regularly

## [4.1.1] (patch release)
### Added
- Re-added possibility to decide if a proxy should be auto synced or manual synced by re-introducing a switch into the Add Proxy to Asset node (hp:4.1.1.0; co:4.1.1.0; streams:4.1.1.0)
### Fixed
- Metadata with the flag pre-resolve will be added to job created by web export trigger correctly (hw:4.1.1.2)
- job.source value is now set correctly (project path) in the job object of a web export triggered on a sequence object (hw:4.1.1.2)

## [4.1.0] (stable release)
### Added
- Add adobe project id (nodeId or dynamicLinkGUID or sequenceID) wildcard (streams:4.1.0.1)
- Add the possibility to use custom self signed certificates (license:4.1.0.1 ,hc:4.1.0.1) -> **Client update required**
  - https://moovit.jitbit.com/helpdesk/KB/View/42877232-use-custom-self-signed-certificates-for-the-client
- Add nodes for adding/changing and deleting asset metadata of existing assets in database (co:4.1.0.1; streams:4.1.0.1)
- Add multicam sequence support (co:4.1.0.1, hp:4.1.0.1)
- Premiere and After Effects 2022 support (license:4.1.0.1; client:4.1.0.1; streams:4.1.0.1) -> **Client update required**
- Add a GetFilesFromFolder and GetFoldersFromFolder action node that iterates over all found files or folders either on top level or recursive from a given folder path (streams:4.1.0.1)
- Add option to drop all helmut connections of one single computer (4.1.0 snapshot release) -> **Client update required**
  - Can be used to free the client connection if a user locks his windows account without logging out from helmut. 
### Fixed
- Aurora Submit Job Action (streams: 4.1.0.1)
- Cosmo Web import and Web upload are considering metadata (hw:4.1.0.1)
- Move last login timestamp update right after the trigger of the CONNECTED stream in order to really have the last login time in the connected stream (users:4.1.0.1)
- Exchange functionality in streamdesigner now works with special chars in stream design (streams:4.1.0.1)
- Delete job will also cancel the job in order to avoid invalid status updates in dashboard (io:4.1.0.1)
- Cosmo Web import file chooser dialog has now pagination and does not show folder sizes anymore (hc:4.1.0.1, license:4.1.0.1, hw:4.1.0.1)
- Colon in Metadata fields is now a supported character for select, multi select and autocomplete fields (hp:4.1.0.1, hw:4.1.0.1)
- High quote in metadata does not lead to an evalscript error anymore (hp:4.1.0.1)
- Search for windows paths via filters is now possible using the IS comparator, all others do not work (yet) (co:4.1.0.1)
- Fixed wrong content showing of edit cronjob dialog when using esc key to close this dialog (hw:4.1.0.1)
- {project.id} wildcard is now default value of Project ID list input of Cosmo Add Asset To Project node (streams:4.1.0.1)
- Hide enabled switch in watch folder edit dialog when trigger point is a cronjob (hw:4.1.0.1)
- Refactored all metadata nodes and fixed job create job metadata set assignment when add metadata switch is false (streams:4.1.0.1; hw:4.1.0.1)
  - Either current metadata can be attached to new created job or the metadata defined by the set that is attached to the triggered profile. The fix covers the last mentioned feature.
- {job.mimeType} wildcard will resolve to SEQUENCE when the job source is a sequence item (io:4.1.0.1; hw:4.1.0.1)
- Ensure job.assetId field being filled with information for web export and panel import in order to be able to use the new asset metadata manipulation nodes (hw:4.1.0.1; hp:4.1.0.1)
- Fix inconsistent Languages page visibility (hw:4.1.0.1)
- Removed duplicate Recipient-ID field in Telegram node (streams:4.1.0.1)
- Fix broken version select field for Flow and CatDV preference module (fx:4.1.0.1)
  - You need to remove all Flow / CatDV preferences and restart the fx container in order to get the fix
- Fix java heap space error when uploading large files > 1,5 GB (streams:4.1.0.1)
- Add an add and remove entry button to each groups entries of the active directory auto module (streams:4.1.0.1)
### Changed
- Improved stream designer error descriptions (streams:4.1.0.1)
- When navigating into bin in cosmo project detail view the current filters except of the breadcrumb filter will be deleted to enable unfiltered view of folder content (hw:4.1.0.1, hp:4.1.0.1)
- Improve memory usage of Panel and Webserver (hp:4.1.0.1, hw4.0.8.9)
- Force all Log4J dependencies to patched version 2.17 even though the dependencies are not vulnerable, but some wrong working dependency scanner point them out to be affected (4.1.0 snapshot release)
### Removed
## [4.0.7-release-2] (stable release)
### Fixed
- Fix empty destination path for Job Render in Premiere Node (streams:4.0.7.48)
## [4.0.7-release-1] (stable release)
### Fixed
- Adding metadata when uploading assets to cosmo works
## [4.0.7-release-0] (stable release)
### Added
- Add Project Duplicate Action node (streams:4.0.7.14)
- Add wildcard for user last login and change timestamp update behavior (streams:4.0.7.14; users:4.0.7.1)
- Add a streams node compatibility check on streams container startup (streams:4.0.7.5)
  - Streams container will try to request all existing streams in the database. If an error occurs it's now visible in the streams container logs which stream has incompatible nodes.
- Add asset/sequence report generation nodes that exports all database information about an asset or sequence to a json file (streams:4.0.7.19; co:4.0.7.2)
- Add {job.source.type} wildcard that reads out job.type value during stream (streams:4.0.7.19; co:4.0.7.2; hk:4.0.7.1; io:4.0.7.1)
  - example workflow: ADDED_ASSET could be skipped now whenever job.source.type is equals PANEL_IMPORT
- Add option to import asset instead of upload asset in cosmo (streams:4.0.7.27; co:4.0.7.4; hk:4.0.7.2;  io:4.0.7.2;hw:4.0.7.8)
  - If user is logged in and client is connected to the web interface we provide a file chooser in the web that is capable of browsing the local directory of the logged in user
  - It's possible to select multiple files or folders whereby the latter will be read out recursively
  - After Selection it's possible to trigger a WEB_IMPORT stream per file
  - **Client update required and all existing WEB_IMPORT streams have to be migrated into new WEB_UPLOAD trigger point**
- Add action button to single select overlay (hw:4.0.7.8)
- Add "Helmut Remove Users From Group Action" node (streams:4.0.7.31)
- Add assetId to job object and add {job.assetId} wildcard (streams:4.0.7.31; co:4.0.7.5; hk:4.0.7.4; io:4.0.7.3)
- Add sequence typed asset to ADDED_ASSET stream trigger and fix non triggered ADDED_ASSET stream (co:4.0.7.5)
- Add Hiscale Jobs Start Process Action Node that allows to trigger a job in JOBS Video Worklfow Platform (streams: 4.0.7.34)
- Downloaded client installer will now have current version number in their file name (hw:4.0.7.11; license:4.0.7.2; hc:4.0.7.6)
  - **It is important to do a combined update of license and web in order to have this feature active**
- Add {date.increment.days.?} and {date.decrement.days.?} wildcards (streams:4.0.7.37)
- Add project lock filter (hw:4.0.7.13)
- Add 7-Zip nodes (streams:4.0.7.39)
- MediaFPS condition now accepts stream variable as input (streams:4.0.7.39)
- Add translation for panel debugging texts (hw:4.0.7.13)
- Pre resolved date time field that is not changed in panel will now be passed correctly into export job (hp:4.0.7.9)
- Add search by job id into free text search of job dashboard (io:4.0.7.5)
- Add Watch folder to cron options (hw:4.0.7.10)
- Add a filter option for locked projects (hw:4.0.7.10)
- Add an action menu to the single project details view (hw:4.0.7.10)
- Add an "Open Helmut Panel" node that opens the visible helmut panel using the invisible one (streams:4.0.7.39; license:4.0.7.3; client:4.0.7.8)
### Fixed
- Limit mongodb (database) default maximum cache size (mongodb:4.0.7.7)
  - per default mongodb was able to allocate up to 10 GB of ram leading to memory issues
- Windows client removes the panels first before reinstalling the new ones to allow a successful panel installation on Windows(client:4.0.7.1; license: 4.0.7.1)
- Improve the asset finding in panel sync process to decrease synchronization time for large projects (hp:4.0.7.1)
  - Searching by nodeId took long due to the fact, that all assets in a project where scanned. Found a way to pre filter the potential target asset results
- Refactored PANEL_IMPORT trigger (hp:4.0.7.1; co:4.0.7.1; streams:4.0.7.1)
  - It will now be triggered ones the whole initial autosync process is finished to avoid multiple database accesses to the same assets
- Add UNC path support on path.map.to.unix wildcard (streams:4.0.7.1)
- Job Render AAF action does not force premiere to hang when the temp project has been manipulated and close project flag is true (client:4.0.7.3; license:4.0.7.2; streams:4.0.7.2)
  - If ones removes the video track in order to avoid error messages in aaf creation we had an save event right at the end of the process before closing the temp project. This led to a freeze of premiere. We now just skip the save and simply close the project without saving.
  - **client update required!**
- Job destination is not filled with previous export of AME when using the Job Render in AME Action node and export finishing process takes longer (client:4.0.7.3; license:4.0.7.2)
- Kill premiere is not working on Windows and does not throw an error message on mac (client:4.0.7.3; license:4.0.7.2)
- Stream exchange of stream that contains Job Render AAF in Premiere Action node is now possible (node replace necessary) (streams:4.0.7.4)
- Fix last occurrence of the bug where changing the streams sort order removes the connection between the start node and the first helmut node (hw:4.0.7.5)
- Create profile dialog does no longer show hk streams DELETE trigger events in cosmo (hw:4.0.7.5)
- Fix MOVE and COPY tasks in housekeeper (hk:4.0.7.3)
  - Both types where missing as a job.type which led to an error in the hk container. User saw only one hk job created in the dashboard even though multiple projects where covered by the task filter
- Refactored Tag field in add project dialog to avoid the blur effect to remove the previous value (hw:4.0.7.8)
- Auto import now adds all jobs to AME without throwing busy status (streams:4.0.7.31)
- Delete Job now also performs a cancel event beforehand (io:4.0.7.3)
- All file create/copy/move action nodes now create destination folder by default if not existing (streams:4.0.7.31)
- Fix error of new "Project Metadata Changer Action" node when it's getting used in a customIO stream (streams:4.0.7.31)
- Fix panel disconnection whenever assets are being copied between multiple opened premiere projects (hp:4.0.7.7)
- Empty AME path in corresponding node will now fails with error message in the jobs dashboard as expected (streams:4.0.7.31)
- Stream snapshot and stream variables free text search now searches global over pagination (streams:4.0.7.38)
- Delete category stream is not moved to Housekeeper after stream save event (streams:4.0.7.33)
- Reactivate asset metadata display on sidebar for single item selection (hw:4.0.7.10)
- Adjust Date formatting between different displayed fields e.g. filter modal, filter chip, date value in table view (hw:4.0.7.10)
- Client installer are now supporting all CC2020 and CC2021 versions (license:4.0.7.2; hc:4.0.7.6)
  - For Premiere Tested up to Version 15.4.0 Build 47; for After Effects 18.4.1
- Save button in add profile modal will be reactivated after failed add event e.g. due to already existing profile name (hw:4.0.7.12)
- Make action menus close automatically (hw:4.0.7.10)
- Align several buttons and menus properly (hw:4.0.7.10)
- Fix unnatural app navigation (i. e. redirect to login for logged in users) (hw:4.0.7.10)
- Fix occasional display and loading problems (i. e. Template view) (hw:4.0.7.10)
- Several containers are not throwing Authorization Interceptor Errors anymore when running (preferences:4.0.7.1; metadata:4.0.7.1; logging:4.0.7.4; fx:4.0.7.2; hk:4.0.7.5; io:4.0.7.6;  language:4.0.7.1)
- Failed Hiscale Jobs Start Process Action Node will not longer stops the stream workflow but triggers failed output of node (streams: 4.0.7.47)
### Changed
- Deprecate % sign for functional wildcards in order to allow usage of this sign as a modulo operator in Execute Javascript Action node (streams:4.0.7.2)
- Add username as separate table entry in FX Dashboard and make it searchable and sortable (hw:4.0.7.4)
- Medialoopster nodes -> change all put requests to patch (streams:4.0.7.10)
- Helmut snapshot and update script is now using regex to determine correct stack file in order to allow prefix and suffix to "Helmut4" stack file name
- Refactor the user feedback of background processes of the helmut panel and add improved support for After Effects (hp:4.0.7.5)
- Change Add Proxy node to allow asset id as input parameter that will be prioritized over highres path (streams:4.0.7.20; co:4.0.7.3)
- Add glowing highlight effect to active fixed fx filters (group, category and template) (hw:4.0.7.8)
- Reduced multi select to a action button and a indicator of the total amount of selected items in panel (hp:4.0.7.6)
- Add LINUX as selectable OS in Operating System Condition node (streams:4.0.7.28)
- Like the Job Metadata Changer Action Node the corresponding Project Node does allow empty metadata values as inputs (streams:4.0.7.38)
- Add node version numbers to node headers in streamdesigner (streams:4.0.7.39)
- Change circular progress color of canceled jobs in dashboard from red to white (hp:4.0.7.9;hw:4.0.7.13)
- Change layout and button theme in Preferences (hw:4.0.7.10)
- Improve behavior of the search toolbar (hw:4.0.7.10)
- Unify several button and menu names (hw:4.0.7.10)
- Rewritten the After Effects and Premiere invisible panels and added missing nodes for After Effects to align feature set of both products (streams:4.0.7.39; license:4.0.7.3; client:4.0.7.8)
### Removed
- Hide the unused show all switch in the variables modal of streamdesigner that came from the snapshots modal (streams:4.0.7.2)
- Remove the open logs function whenever Helmut is running on https:// (hw:4.0.7.2)
- Remove switches from boolean filters (hw:4.0.7.10)
- Remove several outdated and unused app components (hw:4.0.7.10)

## [4.0.6-release-0] (stable release)
### Added
- Added option to search for a stream by its ID (hw:4.0.5.20)
- Added option to copy a stream's ID to clipboard in the streamdesigner with the top right speech bubble (streams:4.0.5.40)
- Added new wildcard {path.map.to.json.?} to change '\' to '\\' (streams:4.0.5.39)
- Added AddJobToAurora Node(streams:4.0.6.15)
- Added VpmsCheckIn Node(streams:4.0.6.15)
- Added VpmsMetadataUpdate Node(streams:4.0.6.15)
- Added Split & Stitch workflow Beta - only for 25fps (streams:4.0.6.15; io: 4.0.6.1; hps: io: 4.0.6.5; AME_WS_1_3_6) 
  - Added Job Create Split Jobs Action Node 
  - Added Job Stitch Splits Action Node
  - Workflow: Create a new job for every single stitch, render them independently and then stitch the splits back together
- Added XPath Node to extract values from XML files by expression (streams: 4.0.6.15)
- Added HUE Bridge Support (streams: 4.0.6.15; fx: 4.0.6.1; preferences: 4.0.6.1; hw: 4.0.6.4)
  - First delete the old HUE preferences from the db
  - Upgrade versions
  - Restart fx (Preferences are only created during startup)
- Added a wildcard to retrieve a folder's contents' size (streams: 4.0.6.17)
- Added Tooltips to Streamdesigner for: (streams:4.0.6.17)
  - Snapshot names (list view)
  - Variable store (list view) keys
  - Variable store (list view) values
  - Node Descriptions (left panel)
- Added domain name into browser tab and add - DEBUG string whenever the debugger modal is opened on the page (hw:4.0.6.7)
- Introduced a new Metadata field called AUTOCOMPLETE (hw:4.0.6.7; streams:4.0.6.17; metadata:4.0.6.1; co:4.0.6.4; fx:4.0.6.3; hk:4.0.6.3; io:4.0.6.2)
  - Same like TYPEAHEAD but with restrictions on the possible user input
- Added wildcards for requesting all users and all groups by now limited to 500 results (streams:4.0.6.22)
- Added Send Message To Teams Channel node (streams:4.0.6.24)
### Fixed
- New client 4.0.6.1
  - Premiere/AME version 15+ support
  - Improved AME panel with more logging and better AME error handling
  - To much license claiming in Chrome will now report correct message
- New linux client 4.0.6.2
  - Improve client initialization when starting multiple clients at the same time
- Handle null values in search filter to avoid complete page load error (hw:4.0.6.1; hp:4.0.6.1)
- Changing event trigger of Start node will no longer visually duplicate the node (streams:4.0.6.7)
- Add missing translation "Choose Composition" (hw:4.0.6.3;hp:4.0.6.2)
- Fix behavior of switch input field in streamdesigner (streams:4.0.6.12)
- Fix Project metadata changer action to only change the target project (streams:4.0.6.13)
- Fix Project metadata remove action to only change the target project (streams:4.0.6.13)
- File and Copy Folder nodes don't show 'FAIL' anymore, when successful (streams:4.0.6.13)
- Fix issue that leads to the job status to stay in "Starting AME" forever, if an invalid / non-existent path was used (streams:4.0.6.0)
- Fix Cancellation of Job AME Render Action when canceling the stream (streams:4.0.6.14)
- Catch negative interval input in File ... and Folder Growing/Appearing condition (streams:4.0.6.14)
- Refactored the update job list logic in the dashboard page to preserve usability of that page (hw:4.0.6.5)
- Fix opening another stream from within the Streamdesigner with the right click menu + colon (streams:4.0.6.17)
- "Helmut Add User To Group Action" allows comma separated inputs (streams:4.0.6.17)
- Fix long node descriptions adding line breaks (streams:4.0.6.17)
- Job File Copy Action has a {node.result} output (streams:4.0.6.17)
- Fix MD5 check error (License load error) occurring on refresh of Login page (license:4.0.6.2)
- Web export will now include all listed metadata from the export dialog (hw:4.0.6.7)
- Sequences with markers in latest Premiere 2021 version will not longer be indexed as mimeType DATA (co:4.0.6.4)
- Force deletion of old project files that has been used for project index (co:4.0.6.5)
- Job Render with FFMPEG Action node provides progress again (streams:4.0.6.17)
- Selected profiles from cosmo are not longer be displayed in io (hw:4.0.6.7)
- HK profiles with the flag "Hide from user" = true will now be displayed in the add/edit Task dialog (hw:4.0.6.7)
- Fix Asset creation in Stratus (streams:4.0.6.17)
  - Fix asset type and description field transmitting
- Changing stream event within the stream designer now moves the stream into the correct event trigger in the helmut streams view (streams:4.0.6.20)
- Refactored File & Folder Multiple Appearing Condition (streams:4.0.6.14)
  - Fix wrong positive response whenever one of several inputs satisfies condition
  - Fix counter that checked the amount of checks the user provides +1 
  - Handle negative interval inputs
- Fix "include null" behavior of Empty String Condition (streams:4.0.6.20)
- Long tooltips in Dashboard are not flashing anymore (hw:4.0.6.13)
- Action menu does not rapidly switch positions whenever there are a lot of entries (hw:4.0.6.13)
- Improved error descriptions for Project Category Condition, Project Creator Condition, Project Extension Condition, Project Name Condition, Project Personal Condition, Project Template Condition, Project Task Condition, Project Team Condition
### Changed
- Replace all jsx polling events from premiere panel -> performance boost (hp:4.0.6.2)
- Cosmo Add Asset to Project Action now accepts a comma separated list as input for project id parameter (streams:4.0.6.14)
- All % signs in wildcards which where used as placeholders have been replaced with the current curly brackets (streams:4.0.6.14)
- Premiere Version Converter shows now v2021 rather than v2020_1 (streams:4.0.6.17)
- Remove default config initialization on first helmut installation (fx:4.0.6.3, streams:4.0.6.17)
  - A predefined set of streams and preferences will be imported using the restore feature now
  - This solves the problem of non starting streams container whenever there is an unknown node used in an existing stream
- Change default variable of source file in "Job create Job Action Node" from {job.destination} to {job.source} (streams:4.0.6.17)
- Import a folder via cosmo tab in the panel will now transfer the bin structure of the source project and will trigger a new stream event called PANEL_IMPORT (hw:4.0.6.7; co:4.0.6.4; streams:4.0.6.17; io:4.0.6.2; hp:4.0.6.5)
  - It's a manual sync process coming from cosmo to enable consolidated import on one hand (avoid flashing premiere import dialog) and avoid direct timing problem with the new PANEL_IMPORT stream where the assets could be changed before sync
  - Import single asset will work like before but with additional PANEL_IMPORT stream
- Minimum mandatory character for project name is now 1 (hw:4.0.6.7)
- In/Out points will now be handled as relative to a potential time code offset of the target asset (hp:4.0.6.5)
- Changed Streamdesigner browser tab logo from HFX to helmut logo (streams:4.0.6.17)
- Changed Jobs dashboard update logic to improve performance (hw:4.0.6.9; hp:4.0.6.8) 
- Changed the behavior of the select sequences multi select field in export tab of the panel (hp:4.0.6.8)
  - Add a select all checkbox
  - Add a loading indicator for giving the user feedback of the sequence request from premiere
  - Improve performance of the function that reads out all sequences of the project (about 4 seconds per 100 sequences)
  - Show only first item following by a counter of the additionally selected items
- Make message input field of EmailOutput node multiline (streams:4.0.6.20) 
- Improve description fields of nodes and wildcards
- Change error message of Premiere Alert Action if premiere is not running to a more understandable one (streams:4.0.6.20)
- Change color of lock icons in panel in the projects view (hp 4.0.6.12)
- In the description overlay of nodes the node type will now displayed only ones (streams:4.0.6.20)
- Add highlighting to fixed filters in fx if they are set (hw:4.0.6.13)
- Add response code != 200 check for vantage nodes (streams:4.0.6.20)
- Switched zoom orientation to be in line with the system default (streams:4.0.6.24)
- EFS get free space node returns floats instead of integers (streams:4.0.6.24)
- Stream snapshots are now associated with their corresponding stream, and by default only those are shown (only works for new snapshots). You can toggle a switch to show all snapshots, including old ones (streams:4.0.6.24)
### Removed
- (Single) HUE light preferences and nodes (Replaced by new HUE bridge support)
- Helmut Cloud Services nodes (streams:4.0.6.17)

## [4.0.5-release-2] (stable release)
### Fixed
- Fix Panel import with proxy where second proxy attachment fails due to wron JSON definition

## [4.0.5-release-1] (stable release)
### Added
- Add Telestream Vantage Nodes
- Add EFS Nodes
### Fixed
- Fix UI table out of range bug for variable store and snapshot modal

## [4.0.5-release-0] (stable release)
### Added
- Added an automatic Node Tree sorting function. Win: CTRL + L, Mac: CMD/Control + L. 
  - Nothing selected: Entire Node Tree will be adjusted
  - One Node selected: Node acts as anchor, only the downstream Nodes will be adjusted
  - Multiple Nodes selected: Only the selected Nodes will be adjusted
- Basic Auth support with username:password and clientId:clientSecret (oAuth tokens) instead of Bearer token.
  - Bearer Auth still supported
- We added an extra level of security to the way Helmut components connect to the message bus:
  - You will need to install the new client 4.0.5.x
  - Client 4.0.5.x is compatible with Helmut versions < 4.0.5.x but not the other way around.
- RevApp integration to Upload Assets, Share Assets (public and private) and Delete Assets (streams: 4.0.5.24, hw:4.0.5.11)
  - Add your RevApp credentials under Preferences -> Modules -> RevApp
- Will Now show the name of the stream in the delete confirm message (translatable)
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
  - Load a saved Snapshot, and replace your current node tree with it
  - Independent of 'save' functionality, unsaved progress will be lost
  - Delete Snapshots
- Block switching active project whenever a sync process is active (hp:4.0.5.5)
- Add option "Don't change breadcrumb" and renamed the corresponding asset name feature of the Add Asset to Project Action (hp:4.0.5.5; streams:4.0.5.26; co:4.0.5.4; hk:4.0.5.2)
- Add select all option to multi select field (for example to select all groups in add user dialog) (hw:4.0.5.13)
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
- Added {path.map.to.json.?} functional wildcard that escapes \ in a path (streams:4.0.5.39)
### Fixed
- Requests to Premiere like render project, render AAF etc. would timeout (and loop sometimes) after 2 minutes (also patched in 4.0.4-release-0)
- Removed default 1970 date for datetime metadata (hp:4.0.5.2, hw:4.0.5.6)
- Fixed web interface asset update for synced callback loop
- Project filters can now be saved if the language has changed
- Fixed Scrollbar in the Streamdesigner's 'edit panel' to be full size again (streams:4.0.5.14)
- Duplicate profile when group is selected is not working without throwing JSON parse error (hw:4.0.5.10)
- Fix umlauts and "-" char of metadata keys coming from premiere sync (co:4.0.5.3)
- Fix preload profile at export page loading of panel (hp:4.0.5.6)
- Fix stream renaming issue where a renamed stream appears to be empty and finishes without running any node (hw:4.0.5.12)
- Proxy path will now change if an asset is indexed that had already a proxy set (co:4.0.5.3)
- {job.proxy} is not null anymore for auto import streams (co:4.0.5.3)
- Reset footer selection count and action button if an individual action button of a table entry is used (hp:4.0.5.8)
- Store variable can now not be duplicated by renaming an existing one (streams 4.0.5.27)
- Fix action menu in housekeeper multi select (hw:4.0.5.13)
- Fix "Medialoopster Update Asset Delete Date Action" for IMAGE and AUDIO assets (hw:4.0.5.13; users:4.0.5.4; streams: 4.0.5.27)
- Editshare nodes used to show 'successful' when no work was done (Because of missing user input). Now it shows that it fails (streams: 4.0.5.28)
- Editshare nodes used to work, even if the module is disabled. Now they will fail (streams: 4.0.5.28)
- File Copy Action Node will cancel the job at first try rather than resetting the job status back to RUNNING (streams:4.0.5.29)
- Fix bug where a streams import was impossible when trying to import streams from an older version that has a higher patch version (hw:4.0.5.15 ;streams:4.0.5.30)
  - Example: importing 4.0.4.125 streams export into a 4.0.5.5 streams version
- Fix Stratus Asset Create Action node -> Description field behavior that no longer transfers project related metadata (streams:4.0.5.28)
- Fix all Store variable nodes to work in production environment -> They do not throw bad requests (streams:4.0.5.28)
- Add Snapshots dialog is now showing "Name:" instead of "Key:" (streams: 4.0.5.31)
- Add job or project over message bus removes an entry at bottom of the list to avoid exceeding the limit (25/50/75/101). When limit is not reached
  Jobs/Project have been removed from the list by mistake (hw:4.0.5.14)
- Improved Get Assets From Project Action node performance (co:4.0.5.5)
- Fixed result reporting for the following nodes (which where using setLastResult only, so their result was always being overwritten by the next node            calling either addLastResult or setLastResult):
    -ProjectCreateActionImpl, ProjectCreateActionImplV2, PremierePromptActionImpl, FileMoveActionImpl, FolderMoveActionImpl
- Rename, duplicate, change the group assignment or the order does not lead to create a corrupt version of the stream (hw:4.0.5.17)
  - Changing the order from now on is only possible for FX streams due to the fact that the mechanism for other products is now fully replaced by the Job Create Job action node
- Change sort order of first metadata entry of directly new created group is now possible (hw:4.0.5.17)
- Add "move" and "copy" to selection field of add task dialog (hw:4.0.5.17)
- Pass correct breadcrumb to job.breadcrumb into stream when auto import assets from subfolder (hp:4.0.5.11)
- Fix warn signal rotation for language translation view (hw:4.0.5.19)
- Fix group assignment for Streams where streams appeared to be empty after assignment has been done (hw:4.0.5.19)
- Avoid passing project related metadata to job.metadata from panel (hp:4.0.5.11)
- Remove generic error when attaching an invalid proxy filepath (hp:4.0.5.10)
- Change Team to Group in import users dialog (hw:4.0.5.19)
### Changed
- Adding new jobs/projects via the the message-bus will now remove the last entry of a list to never exceed the selected size of shown elements (25/50/75/101)
  - We received reports of huge performance issues when being on the dashboard and a lot of new jobs showed up
- Search for projects or jobs in the Web interface now adds a delay of 500ms while typing before the search will be executed to avoid spamming the server
- Changed Variable Store shortcut from v to k (streams:4.0.5.14)
- Changed loading indicator for autosync process by moving it to the footer (hp:4.0.5.4)
- Changed multi select and moved it to footer (hp:4.0.5.4)
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
- Change behavior to text input fields to select everything only for first click, every other click will navigate the cursor between the text (hw:4.0.5.13, hp:4.0.5.8)
- Change add project access rights check to be made on project create dialog instead of disabling the add project button (hw:4.0.5.17)
- Disable sorting of streams for all products except FX since it's replaced by Job Create Job Action (hw:4.0.5.17)
- Use "FilePath" entry instead of "ActualMediaFilePath" entry if a project gets indexed (co:4.0.5.6)
  - The ActualMediaFilePath holds the previous filepath before Premiere native consolidation is performed. If that is the case the media is offline since the FilePath holds
    the most recent information about the asset location.
- Improved table view sorting for all table views (hw:4.0.5.19)
- Change default variable of source file in "Job create Job Action Node" from {job.destination} to {job.source} (streams:4.0.5.39)
### Removed
- EFS nodes
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
- Search for projects or jobs in the web interface now adds a delay of 500ms while typing before the search will be executed to avoid spamming the server

## [4.0.4-release-0] (stable release)
### Added
- Support for HTML tags in Wildcard Resolver (Streamdesigner) (streams:4.0.4.2)
- Highlight projects that are locked by you (hw:4.0.4.2)
- Pagination to Metadata page (hw:4.0.4.3)
- Switching to dashboard after executing a task within Housekeeper (hw:4.0.4.2)
- Add Premiere Generate New UUID Action node. Will give a Premiere Project a new global UUID to avoid duplicates. (streams:4.0.4.4)
- Premiere OS Path Mapper now also maps <ActualMediaFilepath> (streams:4.0.4.4)
- FFMpeg Render Node now outputs to node.result and {job.destination} (streams:4.0.4.4)
- Added all sequence information to sequence exports via JSON side car file (streams:4.0.4.4)
- The Panel now logs out if a user disconnects from the local Helmut client or quits the client (hp:4.0.4.3)
- Nodes to add/remove Asset's to/from Medialoopster (streams:4.0.4.27)
- {user.client} wildcard which resolves to the clients version number (available in server streams too) (streams:4.0.4.27)
- Links between {node.result.?} wildcards and the actual linked Node in Streamdesigner (streams:4.0.4.27)
- Denied deletion within the Streamdesigner of linked Nodes using {node.result.?} (streams:4.0.4.27)
- Functionality to expand/reduce single/all (all = shift+click) Nodes individually next to the global 'Show settings' function within the Streamdesigner (streams:4.0.4.27)
- Feature to enlarge the inline Stream debugger withing the Streamdesigner (chevron on the right site when Debugger is open) (streams:4.0.4.27)
- Manual refresh button to the IO/CO/HK-Dashboard if filters are set (new events will no more be pushed on top of the list regardless of the filter) (hw:4.0.4.8)
- Feature to live debug log files of connected clients via the the Action menu in the FX-Dashboard (license:4.0.4.1 hw:4.0.4.8 users:4.0.4.2)
- DISCONNECTED event (delays client logout until all Streams are executed) (license:4.0.4.1 hw:4.0.4.8 users:4.0.4.2)
- Relative date filters for custom metadata from type date (fx:4.0.4.1, hw:4.0.4.4, hp:4.0.4.3)
- Stream trigger point for unindexed assets (co:4.0.4.3)
- HTTP Request Node (experimental; streams:4.0.4.32)
- Natural, alphabetical Metadata sorting in Project, Asset and Dashboard overlay (hw: 4.0.4.12)
- Helmut Confirm Dialog Action to ask a user confirm a question within the web browser (streams:4.0.4.32 hw:4.0.4.12)
- Helmut Input Dialog Confirm Action to ask a user answer a question within the web browser (streams:4.0.4.32 hw:4.0.4.12)
- Add User To Group Node to add user(s) to a Group (for example during group/user creation) (streams:4.0.4.32)
- Added more null pointer checks to index project logic (co:4.0.4.5)
- <s> Version to name of downloaded clients (hw:4.0.3.14) </s>
- Added Multi language support to web interface and Panel. Streamdesigner and error messages will NOT be translated.
  - Add Languages under "Language" Menu entry and set them as default Language under Preference > General
  - This Language will also be applied to the Panel
  - Languages marked with a red color are not yet translated - same goes for new entries after updates.
- Added indicator for missing translations
  - Missing translations always fall back to English (unchangeable/undeletable language)
- Added multi select to most of the table views of the web interface (hw:4.0.4.21)
- Add Medialoopster Update Asset Delete Date Node
- Some Nodes did not create the destination folder if it didn't exist, this has been changed in various nodes
- "Import Project To External Helmut Action" to import a Project into an external Helmut using OAuth
  - The project file will be uploaded
  - Metadata will be merged by names if enabled in Node
- Stratus Asset Add Folder Membership Action to Streams (streams:4.0.4.54)
- Added delete job and delete multiple jobs functionality and the corresponding access preset (hw:4.0.4.23, fx:4.0.4.7)
- Multi node copy to StreamDesigner (cross tab requires SSL) (streams:4.0.4.67)
- Free text search does now also cover IO job statusMessage field in dashboard view (io:4.0.4.11)
- Added Multi select in panel and web and reworked the selection to avoid sort order variation during selection (hp:4.0.4.12, hw:4.0.4.24)
- Added a boolean field "filterable" to metadata to enable/disable the possibility for filtering for it. Not filterable metadata which are already set as filter will be 
  kept until they will be removed. After Removal they cannot be filtered until filterable is enabled again (hw:4.0.4.24, hp:4.0.4.11, metadata:4.0.4.4.2)
- Added wildcard to count words in a string (streams:4.0.4.68)
- Added "hidden" field to profiles to hide them from the user interface (io:4.0.4.12, hp:4.0.4.14, hw:4.0.4.27)
- Added scroll bars to metadata section of export tab of panel (hp:4.0.4.18)
- Transfer Stream variables from pre stream's to actual Stream
- Added custom datetime filter (hw:4.0.4.30, hp:4.0.4.16)
- {job.unique} wildcard usable in INDEXED_ASSET, UNINDEXED_ASSET and ADDED_ASSET streams and after "Cosmo Get Project Assets Action (streams:4.0.4.84, co:4.0.4.27, io:4.0.4.13)
- Added a CMD Execute and BASH Execute Action next to the existing command line action which causes problems from time to time depending on the command to execute
  - Command line Action is spawning an internal shell which is limited, CMD (windows) and BASH (MacOS/Linux) use the desired shell
- Added Cronjobs (HK -> Cron) to Helmut:
  - Cronjobs support scheduled execution of TASKS and ActiveDirectory Syncs
  - For existing installations, patch your Docker stack file with:
    - curl -s https://repo.moovit24.de:443/install/patch-cronjob.sh | bash
    - If you plan to use ActiveDirectory Sync via Cronjobs, you need to modify existing AD Groups in Order for them to work. Just click and unfocus first ActiveDirectory Groups field.
- {user.ip} wildcard to resolve a users real IP
- Stratus Transfer Asset Action to trigger transfer in Grass Valley's legacy Stratus system (and monitor those)
- New icons for the Adobe applications
- Added scroll bars to multi select overlays (hw:4.0.4.49, hp: 4.0.4.24)
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
- Miss leading message when only reserved license slots were available
- No overwriting of user specifications for active directory sync whenever new users are imported to helmut (users:4.0.4.3)
- All other objects than user objects will now be skipped during active directory sync process (users:4.0.4.3)
- Client would drop connection to server when trying to execute (large) Streams > 10MB (license:4.0.4.5, linux: hc:4.0.4.6)
  - Requires client rollout!
- Wildcards would not resolve backslashes and other regex characters (streams:4.0.4.41)
- Reworked canceling of jobs (streams:4.0.4.41 io:4.0.4.8 license:4.0.4.7)
- Added skip for native AE elements for project index (co:4.0.4.13)
- Autosync asset into project in windows environment -> path mapping added to message bus response (hp:4.0.4.11)
- FX Metadata page would show "Add Metadata Set" instead of "Add Metadata"
- IO Metadata page would show "Action" instead of "Delete"
- pre streams are now hidden from Cosmo Profile view as Cosmo has no pre streams
- Command line parser does no more add quotes when not needed to a command
- Removed > sign from export modal (hw:4.0.4.22)
- \E is no more causing problems in wildcards (streams:4.0.4.61)
- Saved Streams content would sometimes be "Success Action" only instead of the actual stream
- Cosmo Get Assets For Project node is working properly again
  - This node looped over one asset only instead of all found assets
- FX Dashboard now shows correct IP for clients using autocorrect
- Fixed path issue within Command Line executor node (streams:4.0.4.69)
- Fixed fps condition to work with floating point numbers (streams:4.0.4.70)
- Fixed metadata sorting for fx and io metadata table views (hw:4.0.4.25)
- Changed payload cleanup for Json extract node to avoid creating functional chars by having backslash following by a numerical char like '\1.mxf' (streams:4.0.4.75)
- LowerCased node names have been upper cased
- Fixed bug where hitting 'Enter' in the EnterTextDialog would refresh (redirect) the page
- Re-added sorting to filter values
- Relative TODAY filter to not act like TODAY_GREATER
- Pasting nodes to the streamdesigner does no more paste nodes outside of canvas
- {file.content.?} now supports {path.to.win/mac.?} nesting
- Tag typeahead field is working again in addProject dialog and filter field (hw:4.0.4.30 hp:4.0.4.16)
- Removed file chooser icon from numerical input fields in streamdesigner (streams:4.0.4.85)
- Covered duplicate bin creation by adapting synchronization process of "normal" assets for bins as well (co:4.0.4.18, hw:4.0.4.34)
- Add proxy to an asset and index project before synchronization -> proxy path will remain instead of being deleted (co:4.0.4.19)
- Project Metadata Changer Action did not trigger valueObject calculation for DATE and DATETIME Metadata to search in those relatively
- Chosen filter value will no be translated (hw:4.0.4.41, hp:4.0.4.18)
- Change variable value in preference tab will now be updated in web ui (hw:4.0.4.42)
- Saved dashboard filter in cosmo product are now listed inside the filter menu (hw:4.0.4.43)
- Set initial sort order of assets in project detail page to name ascending and fixed multi select (hw:4.0.4.48)
- Fixed scrollbar overlapping footer and not reachable metadata fields in export tab (hp:4.0.4.22)
- Edit project -> delete the tag will now really delete the tag entry(hw:4.0.4.48)
- Removed unused buttons cancel, save, confirm that belongs to filter dialog from save filter dialog (hp:4.0.4.22)
- Further optimized the synchronization process to enable correct behavior when it comes to intermediate manual sync trigger (co:4.0.4.23, hp:4.0.4.23)
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
- Reworked the pre stream logic.
  - pre streams are working as a client stream only now
  - pre streams are now being executed in the same logic as normal streams. They are only shown to admin users until they either turn in a "real" job (just be successful) or are dismissed
  - You can add separate render nodes for pre streams so they are executed quickly - dedicated pre stream render nodes should NEVER do long living / heavy tasks - thats why asynchronous actions are not "supported". (streams:4.0.4.32 io:4.0.4.3 hw:4.0.4.13)
  - pre streams always have priority over "real" jobs when a render node is asking for a new job - no matter in which order they have been added
- Changed scrolling of panel to whole view instead of table view only (hp:4.0.4.5)
- Replaced cross in filter dialog at top right with "Delete", "Cancel" and "Confirm" buttons (hw:4.0.4.13 hp:4.0.4.6)
- Completely refactored synchronization process of assets to projects (hp:4.0.4.7 co:4.0.4.7)
- Folder Delete Action has now conditions if folder is not empty "DELETE_ANYWAY", "SKIP", "FAIL"
- Active Directory perform action api endpoint is now expecting a uuid of the groups entry for which the action should be performed (web:4.0.4.23, users:4.0.4.6)
- Added "Keep original name" checkbox to "Cosmo Add Asset To Project Action" to avoid changing the asset name during synchronization process (streams: 4.0.4.68 co:4.0.4.15 hp:4.0.4.13)
- Added autocomplete behavior to tag filter in fx (hp:4.0.4.13 hw:4.0.4.25)
- Added query parameter to AD sync endpoints to avoid sync result message -> Preparation for cron job (users:4.0.4.11)
- Add proxy will now trigger an autosync of this proxy if the corresponding project is open otherwise it will have the sync behavior of its highres whenever the project will be opened (co:4.0.4.20)
- Updated the adobe product icons (hw:4.0.4.48, hp:4.0.4.22)
- Disabled the possibility to save empty filters (hw:4.0.4.48, hp:4.0.4.22)
- Landing page for HK product is now projects page instead of dashboard (hw:4.0.4.49)

### Removed
- Removed hardcoded Job Status Update from Execute Extendscript Action
- Temporary removed toggle recursive synced by triggering set (un)sync on folder (streams:4.0.4.84, co:4.0.4.27, io:4.0.4.13)
- Removed the possibility to rename an access preset since it will not be updated in the user objects (hw:4.0.4.49)

## [4.0.3-release-1] (stable release)

### Fixed
- Client would drop connection to server when trying to execute (large) Streams > 10MB (license:4.0.3.7)
  - Requires client rollout!

### Change 
- Removed parent bin selection for auto imported clips (hp:4.0.3.30)

## [4.0.3-release-0] (stable release)

### Added
- OAuth authentication
- Open Logs (folder) from client menu
- MD5 checksum to streamEngine download
- Advanced error output when a client failed to execute a stream
- Uninstaller (windows only)
- Endpoint check by product in web interface
  - It was possible to reach the project page within IO for example even tho it doesn't exist for IO
- Added relative date filters to panel
- Added a logging entry for the case that a render node is not part of the group, which is assigned to the io profile in cosmo
- Support for Premiere 14.3.1 (requires hp:4.0.3.6 to work)
- Drag wires in Streamdesigner everywhere onto a Node instead of the connector only
- Nodes are now at 95% opacity to make wires visible underneath
- File Increment Name Action and Folder Increment Name Action
- Enabled Add Project Button in restricted mode (experimental)
- Custom confirm dialog when switching to another Stream with unsaved changes
- Placeholders to input fields in Streamdesigner (used for example input data)
- Search bar to Metadata
- Extended descriptions to every input for all Nodes
- The active project has been added to the project select dropdown in the Helmut Panel
- FFMPEG Render Node Action to render with ffmpeg
- Audio Streams Condition to check how many audio streams exist in a file
- Wildcard {project.locked.status} that returns the status of a lock (LOCKED, HOUSEKEEPER, ARCHIVED, RESTORED)
- COPY and MOVE Profiles to Housekeeper
- Delete All Button to Upload File Dialog to clear the list of selected files
- Wildcard {job.mimeType.?} where ? must be replaced by an extension. Will be replaced with the mime type for the given extension on the fly (defaults to DATA)
- Server sided FileChooser to Streamdesigner
- System wide Backup and Restore to Preference Tab
- JSON Payload Extract Action
- Optional Group to Watch folders to enable new jobs to be attached to a group a user can be part of (visibility in dashboard)
- Regex Apply Action to sanitize strings (eg. project names)
- Mediainfo Json Action (will return the complete Mediainfo of a File as JSON, so you can extract values)
- FFProbe Json Action (will return the complete FFProbe info of a File as JSON, so you can extract values)
- The table sort order will be reset to default and the free text search string will be deleted if "Clear current filter" has been triggered (hp:4.0.3.13 hw:4.0.3.22)
- <s> If an asset is imported into the opened premiere project via cosmo tab in panel the same asset will now immediately be added to the database to keep the web frontend synced with the project content (hp:4.0.3.13 hw:4.0.3.22) </s> removed, will be implemented in next version
- XML Generator Action to export XML's in a desired format out of Helmut information (project, job and user)
- File/Folder Appearing Condition - monitor if one or multiple files/folders appear or disappear
- Illegal Character Filter to 'Add Metadata' dialog
- Added ID search filter to search projects by its id (hw:4.0.3.28 only by filter; hw:4.0.3.31 also as free test search)

### Fixed

- Only 5 watch folders would be shown in web interface
- Auto login would fail on Windows and Mac
- Non admin users can now save the amount of items listed
- Relative date filters can now be saved and restored
- Creator value typeahead is now working in all products
- Cosmo can now execute Streams again without problems
- Global variables (preferences) are updated correctly in the web interface
- Notification after AD-Syncs will be sent back to request user only
- Profiles in Cosmo can be filtered by group
- Node outputs cannot connect to same Node's input
- Client does no more break when a stream times out
  - We changed the logic how stream requests are being received and executed to avoid the client to crash if a GENERIC or IO stream times out (client v3.0.3.8, linux client mcp_hc:4.0.3.8)
- All Jobs would be populated to a users dashboard by the message bus - they are now filtered correctly.
- Ctrl key can now be used to select multiple entries on windows (currently admin only; will be reworked)
- Regex Apply Action will now find the regex provided
- Added alphabetically sorting of fx filter keys (hp:4.0.3.13 hw:4.0.3.23)
- Fixed the creation of multiple auto import jobs for same asset if it has been imported via parent folder or as fcp xml (hp:4.0.3.13 hw:4.0.3.22)
- Fixed asset import from panel into root level of current project (import without any bin selected) (hp:4.0.3.14)
- Index project with clipProjectItems without nodeId is now working without throwing null pointer exception (co:4.0.3.6)
- Saving a task with a relative date filter set is now possible (hw:4.0.3.26)
- Filtered out sequences from auto import job adding if a sequence is imported as a child project item of a folder (hp:4.0.3.15)
- Sequence Export would write the extracted sequence project used for rendering to C:\HelmutIO on Windows with premiere >= 14.3.1
- Cosmo projects detail page: Navigate into bin which was previously searched by free text search is now working (hw:4.0.3.28 hp:4.0.3.17)
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
- It's now possible to have multiple filters with same key
- A project sync will now set all assets to synced even though an error occurred while import or sync is performed
- Remove metadata copy to parent bins, which were created from asset breadcrumb
- Recursive Folder uploads are now being uploaded to the relative path - use {job.source} to get the path to the file relative to the upload folder
- The Panel Dashboard will now only show jobs of the currently open project, no more all in a users groups
- Text typed values of filters will now be selected if the text field is clicked -> directly overwriting previous value now possible (hp:4.0.3.13 hw:4.0.3.22)
- Changed default comparator to CONTAINS for all text based filter values (hp:4.0.3.13 hw:4.0.3.22)
- Add 'replacer' to Regex Apply Node (replace found matches with a string or nothing)
- Project Create Action and Project Import Action Template descriptions and added Type field
- <s> Assets that will be synced into a premiere project will be automatically set to be synced as soon as they are requested from database to avoid stucking synchronization queue (hp:4.0.3.20 co:4.0.3.7) </s> -> removed, will be implemented in next version

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

- Only 5 watch folders would be shown in web interface
- Auto login would fail on Windows and Mac
- Non admin users can now save the amount of items listed

## [4.0.2-release-0] (stable release)

### Added

- Render node(s) to job overlay if there are any and less then 10
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
- pre stream's to filter IO jobs in advance, like auto import or watch folders (extensions for eg)
  - New feature called pre streams.
    Whenever you setup an IO Profile, you can optionally choose a pre stream (new Stream Event in IO) that will be executed before the Job is published.
    This can be either a client or a server Stream. It’s an generic stream so it should NOT be used for heavy tasks (since multiple might run simultaneously).
    If the Stream fails, a job will NOT be created and an error message will be thrown in the panel. You can use the Job Status Action to set the job to FAILED or SUCCESSFUL (or QUEUED) right away.
    You can also use the Job Delete Action which will delete the Job silently, no errors, no Job in the Dashboard etc. Perfect for unwanted extensions / paths during auto import or watch folders. Keep in mind that it's hard to debug for a user why a job does not show up (only debuggable in stream debugger)
- Stream name and render nodes to watch folder profile chooser
- Sort users per default by username and allow sorting by username and display name
- Added housekeeper actions to type filter of dashboard tab
- <s>Search assets over Projects in new 'Assets' tab and jump between this page and the project details page</s>
- Added current filter engine from web to panel
- Set maximum results to 25, 50, 75 or 101 for Projects, <s>Assets</s>, Users and Dashboard
- Wildcards in upload path and temp upload path in CO preferences
- {job.breadcrumb} for Exports and auto imports
- HouseKeeper endpoint (new microservice)
- Tasks to HouseKeeper for automated mass housekeeping (experimental)
- New Traefik version 2.2
- Automatic project save after a manual project sync has completely been finished
- wildcard {job.mimeType} after Cosmo Get Assets Action
- Job Priority Action (useful for pre streams)
- INCREMENT_NAME to File Move Action, File Copy Action, Folder Move Action, Folder Copy Action
- Possibility to trigger index project inside a duplicate project stream
- Toggle all switch for assigning metadata to all groups (fx) or metadata sets (io) at ones
- {job.last.proxy} wildcard after Get Assets From Cosmo Node holding the last used proxy path when setting a new one
- {node.result.?} wildcard to use results of previous nodes (including error messages; requires to re-save all streams)
- Jump from StreamDebugger to Stream and highlight according Node by clicking on the thumb (requires to re-save all streams)
- Scrollbar to overlays
- Add .srt file support
- {user.os} wildcard (will be replaced by the client's OS, win or mac, requires client client >= 4.0.2.13)
- Project Metadata Changer and Job Metadata Changer nodes can now set metadata values, that didn't exist in the project/job object
- Relative date filters for projects modify date in FX and for jobs start date in IO
- node.result to File Move Action
- Automatic reconnect if auto login client looses connection
- Toggle All Button to Streams and Profiles
- Overlay-Scrollbar to Streams, Assets and Profiles
- Wildcards to Node pallet in Streamdesigner
- Descriptions to node inputs to Streamdesigner
- Better support for automatic reconnect after server restart for auto login clients
- After a project deletion all project asset references will be removed for project assets
  - Removing projectId and group entries
- Debugger to Streamdesigner (debugs only open stream)
  - Support for asynchronous streams
  - Added highlighting
- Metadata pre resolve functionality to metadata filter
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
- Error in project file Copy action in duplicate streams
- Upload would not work if last used profile does no more exist or is not available
- Added creator and lastModified value to free text search
- Reworked UNC based path mapping for index project workflow
- Added missing filter keys for all products
- Apostrophes in filepaths are supported for asset sync in panel now
- Restore last used profile in upload asset modal is now working properly
- InOutPoints will now be set correctly also for assets with time code offset
- Stream engine could run out of memory when using big streams (memory leak)
- Save and delete filter templates in housekeeper now possible
- Import Sequence from cosmo panel is now working again
- Fixed one issue with UNC path mapping and added path mapping for proxy path for index project workflow
- Completely reworked metadata validation
- Boolean typed metadata filters are now working properly
- Added modified by and creator to free text search of projects view
- Value of tag field in add project dialog will now be save even if it has been the last field modified before add button was clicked
- If key of filter bubble change the comparator field will now be pre filled with the first allowed entry if previous entry is not available for new filter key
- Check for duplicate non AD usernames to avoid duplicate entries in database
- New (never saved) tasks would not be saved if tested before saving them
- Added metadata field validation for web export asset dialog and profile filed of add watch folder dialog
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
- Editing an existing filter bubble from type multi select is now possible
- Select and multi select metadata fields in export tab of panel are now being highlighted if validation fails
- Blocked multiple click add button in add user modal and changed backend logic to avoid the creation of duplicate users
- Assets from type CAPTIONS are now being relinked during project sync
- Fixed non responsive chip filter view in dashboard tab on initial panel load
- Profiles would not be filtered in HK projects menu
- Deleting a pre stream from a profile will not cause an exception inside the panel telling that the pre stream cannot be found

### Changed

- Write File Output Node supports [NEWLINE] now
- Sequence multi select inside export tab of panel has now two icons for set selection either to active sequence or selected sequences in project view
- Composition multi select inside export tab of panel has now two icons for set selection either to active composition or selected compositions in project view
- Clean current filter in projects view of helmut will now also reset group, category and template filter to default
- Changed default sort order of assets from descending modify date to ascending name
- Replaced "Import Project" preference with an access preset entry
- Watch folder is now writing a lock file instead of touching it, to support curlftps (ftp) workflows
- It's now enabled to let groups, products and access preset for users empty when using new Active Directory module
- Active directory user import -> helmut user display name can be binded to one of the ad fields username, display name or email
- Changed active directory response message and added logging for evaluation
- Enabled blank fields for active directory sync
- In add project dialog if a project is selected for import the name of the project will be filled into the project name field if it is empty
- Changed the way to match cosmo database content with the premiere project content in terms of making nodeId information available for project index
- Limit the request for unsynced assets in panel for project sync workflow to 500 at a time and limit the unsynced assets counter to 500 as well
- Reworked Streamdesigner
  - Documentation with release Q2 end of june
- Active Directory sync will now push the result to the web interface via message bus instead of direct response
- Value field of creator filter for fx (projects) and io (jobs) is now a typeahead field
  - Suggestions will be provided after two chars have been typed
- Sort order of Manage Groups dialog
- Added dynamic max with setting of chipContent inline modal to proper display filters
- Cosmo Change (Project) Asset node has now a checkbox for auto import triggering
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
- Add path mapping to Watch folder
- Add new access presets (user and group)
- Add new filters
- Add user email to web interface, including change email (action menu)
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
  - user.display name is now creator
  - filter dropdown entries are now sorted
- Extended mime type detection for incomming assets
- Add extension check for template when calling createProject endpoint (from node for exmaple)
- Add FCPXML render support via HelmutIO
- Add info if projects are opened without helmut (no panel available)

### Fixed

- Resolution condition node works properly
- Typeahead typed metadata works properly
- Mandatory metadata fields are now also checked within the panel
- Mandatory metadata fields are now also checked within Cosmo web upload
- Profiles to group assignment and order at profiles tap of web interface works properly now
- !Single jobs could be handed out to multiple render nodes simultaneously
- WildcardCondition now matches in the correct order
- Access preset to group assignment now working properly
- Render node assignment to profile is now working properly (third and following entries won't have double white spaces between ',' delimiter anymore)
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
- multi select metadata fields in jobs etc. will no more cause problems after adding pre-resolve feature
- Housekeeper assets search is now working properly
- Event trigger node in Streamdesigner would always show an old title then renaming a node or importing a stream
- Event triggers in Streamdesigner will now always show the latest, sorted list of events
- Mimetype detection for M4A and OMF files is now working properly
- Validate user against Auto Active Directory Module now working properly
- Certificate trust for Auto Active Directory Module now working properly
- Saving dashboard filter from HK is now possible
- Sequence and Composition which names includes ":" will now be displayed correctly inside the select dropdown
- auto import as well as asset sync is now working properly for premiere versions 2018, 2019, 2020
  - For 2020 new World is supported
- Added database index for date sort function to avoid mongodb buffer overflow bug
- Added path mapping for proxy import
- auto import groups would not be checked when choosing an auto import profile for an open project
- ActiveDirectory Auto sync will now trigger CREATE_USER for each new user
- Single quotation mark within a filename does not cause errors inside the panel
- Add priority and source to filter list for dashboard filters
- Render node could get a job it isn't responsible for
- FX and CO Server Streams could not send emails (via Node)
- Sequence and/or profiles could not be chosen in the export panel
- Metadata did not behave properly in AddProject Dialog

### Changed

- Improved file size filter for projects and assets -> B,KB,MB,GB,TB are now supported as value suffix
- Project sync process is now working in packages of 25 assets
- Improved upload counter and progress which will be reverted if no upload is currently active
- Switch between opened projects in panel can be made by new added dropdown list, previous switch icon can be used for panel refresh
- Typeahead metadata field now allows arbitrary inputs
- Message dialog can now show large text
- SwatIO channel id is now type string to support wildcards
- Reworked Access Presets and added APs for all products
- All media files of an imported folder in AE or PPRO will now be added to auto import list
- Wildcard replacer to support all kinds/levels of nesting now
- Enlarged input fields in Streamdesigner are now better readable
- Reworked project related filters
  - Group, category and template filters are now fixed filters and their values are dependent to each other
  - Removed edit filter dialog and replaced it with quick pick inline dialog
  - Moved filter saving and restoring functionality to main project page -> it will be find inside the quick restore menu
- Metadata 'Values' and 'Default value' are now being edited using an overlay to have more space horizontally & vertically
- A renoder node (pool) can now be set when adding a new job to IO instead of using the pool of the profile
- Create Job Action can now set Render node(s) within the node (empty = read from profile) to designate a new job to a node (pool)
- multi select of projects and jobs is now only allowed for admin users
- Private project toggle is now only available for admins or the creator of a project
- Renewed IO and CO filters and removed all/any switch
- Copying nodes via browser tabs is only possible when using SSL (or localhost) - this is a browser restriction we can not work around
- Add asset to project will now update project size value
- Extended mime type list
- Updated node's using AME or Premiere default value to v2020
- Add path to premiere lock file to Premiere Native Lock Action
- Project size will now be live updated with every asset which has been added to cosmo
- Removed all/any switch for all search filter
- The way we detect the logged in domain and user for Single Sign On

### Removed

- Hardcoded (double) project name check from duplicate project endpoint

## [4.0.1-2020-02-04-155216] (unstable)

### Added

- Warning to Streams containing deprecated Nodes to Streamoverview
- SwatIO as module and node
- Implemented multi select for jobs in dashboard view (only cancel jobs is supported right now)
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
- Added unprocessed asset property to enable triggering auto import streams for assets synced from cosmo
- Added Helmut auto login download to users action menu
- Released helmut linux client (docker; experimental)
- Added path-mapping / variable insert at desired location (splice)
- Added MD5 checksum wildcard - %file.md5.?% (CPU intensive!)
- Added recursive toggling synced if parent bin has been set to synced / unsynced
- Added restricted mode (non client mode) to web interface (use project tab without helmut client, eg from phone)
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
- Add WEB_EXPORT and WEB_IMPORT Events and Streams (you can still use IMPORT for web ingest)
- Add WEB_EXPORT support for media files to web interface

### Fixed

- Export sequences from Cosmo web interface
- Import composition to premiere project
- Simultaneously add different project types (aepx,ppro,sesx) leaded to empty names for at least two created projects
- Parentheses are now working as expected in wildcards
- Assets without media type (data assets) create an infinite loop when add to something else then root (/)
- Modified date for bins inside assets table in web interface and panel does not show "invalid date" anymore
- Metadata sorting works properly
- Asset export is now sending the asset instead of the project path

### Changed

- Reworked project sync icon (number and icon will now trigger the sync event; added animation to icon to call attention to new unsynced assets)
- License tab in web interface is now showing the major version
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
- Preference Tab in Helmut web interface is now working
- Profile select in Cosmo uploader stuck in certain situations
- Metadata sorting broken when adding/removing metadata entries from other groups
- Metadata CHOOSE_FOLDER in Premiere on Windows would return paths with forward slashes (Adobe special)

### Changed

- Cosmo Database structure (requires re indexing of existing projects to work properly)

### Removed

## [4.0.1-2019-12-06-180706] (unstable)

### Added

- AEFT composition export
- AEFT - auto import, manual import and import from cosmo tab for assets, sequences, compositions, bins, folders
- PPRO - auto import, manual import and import from cosmo tab for assets, sequences, compositions, bins, folders
- AEFT & PPRO - auto import, manual import and import from cosmo tab for compositions into PPRO and sequences into AEFT
- Watch folder to IO
- client version to FX dashboard for connected clients
- Streams for Cosmo
- ADDED_ASSET (called after asset has been - externally)
- INDEXED_PROJECT (called after project has been indexed)
- flat hierarchically folder view for Cosmo Projects details view for WI and Panel
- web upload into Cosmo project detail view (requires HelmutIO)
- „create folder“ into Cosmo Project detail view (Autosync: false)
- local database Logging (removed Elasticsearch and Kibana)
- client version to FX Dashboard
- auto login feature for HelmutClient (dedicated Render node-feature)
- „POST_CREATE_PROJECT“ Event to FX
- MediaInfo Condition Node FPS
- MediaInfo Condition Node Codec
- MediaInfo Condition Node Resolution
- MediaInfo Condition NodeBitrate
- MediaInfo Condition Node Audio Tracks
- MediaInfo Condition Node Color Space
- search filters to IO dashboard
- CatDV Integration
- Create Catalog in Group (recursive)
- Delete Catalog in Group (recursive)
- Add Asset to Catalog in Group with Metadata
- Hostname to HelmutFX Dashboard
- advanced project scan (detailed sequence scan)
- sequence reference visualization in web frontend
- Premiere WS Panel in Helmut Client installer (hidden)
- IO Server Streams (restricted)
- IO Custom Streams (via Panel)
- Node Export AAF via Premiere
- Node Export Sequence via Premiere
- Node Open File/Folder Choose Dialog in Premiere
- Node Delete Project by ID
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
- Wildcard %job.user.display name% - User display name of job creator
- Wildcard %job.user.role% - User role of job creator
- Wildcard %stream.variable.?% - Get a temporary custom stream variable
- Proxy Workflow
- "show in source monitor" action for premiere panel
- Icon-Product switch for Mini-Navigation mode
- Export-Sequence to Cosmo web interface
- support to nest wildcards
- search filter quick select
- projects multi select
- toggle sync / unsync asset in web interface
- Multi project support for premiere
- Multi project select in fx projects view of the web interface
- Multi-Export Sequence in panel
- Consolidated media typed asset import in panel to avoid multiple Premiere import dialogs
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
- Non working multi select metadata field
- hidden metadata fields are not persistent within edit or duplicate project
- path mapping would be applied twice and lever itself
- (force) locked projects could be opened for detail view in Cosmo
- non-admin users would not see any job's in the io/co/hk Dashboard
- empty path-mappings would map url slashes
- projects could not be shift-multi selected bottom-up
- Job-cancel would require a client restart in various situations
- Preferences would be invisible when switching applications
- PathMapper would not map to requested OS
- Premiere Rendering requires EPR Preset Paths with forward slashes on Windows

### Changed

- Changed „Helmut Client is in use“ with „No free License slot available“ when no License slot is available
- Export Profiles are now being filtered by the Projects Group
- auto import Profiles are now being filtered by the Projects Group (first comes, first serves)
- Navigation Tabs that require administration rights in HelmutIO are now filtered properly
- The default state of „Remember me“ for Logins has been set to true
- Added thumbs (up/down) to Cosmo ProjectDetail view instead of true/false
- Removed Elasticsearch and Kibana
- The FX Dashboard now shows ‚display name (Username)‘ instead of ‚Username‘
- Upload paths (target + temp) are now set in the HelmutCO Preferences instead via docker compose
- Implemented folder creation by breadcrumb if asset has been added
- %path.split.#:?% Node has been changed to %path.split.#-#.?% to support ranges (including negative)
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
[4.0.4-release-4]: https://www.helmut.de
[4.0.5-release-0]: https://www.helmut.de
[4.0.5-release-1]: https://www.helmut.de
[4.0.6-release-0]: https://www.helmut.de
[4.0.7-release-0]: https://www.helmut.de
[4.0.7-release-1]: https://www.helmut.de
[4.0.7-release-2]: https://www.helmut.de
[4.1.0]: https://www.helmut.de
[4.1.1]: https://www.helmut.de
[4.2.0]: https://www.helmut.de
