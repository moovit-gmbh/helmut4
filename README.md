# Helmut4
This is a public representation for the private product [Helmut4](https://www.helmut.de/) by [MoovIT GmbH](https://www.moovit.de).


### Helmut4 & 3rd application support cycle
MoovIT will deliver support on the 3 most current Helmut4 stable releases. Bug fixes will always be applied in the current stable release. Clients are encouraged to keep their installed systems up to date.

Please always refer to our compatibility notes in respect to the Adobe Premiere, After Effects and Audition applications and its versions, before updating Helmut4. The compatibility information can be found under https://github.com/moovit-gmbh/helmut4/blob/master/README.md

MoovIT will only support 3rd party application versions, that are actively being maintained and supported by the vendor of the 3rd party product - eg [Adobe](https://helpx.adobe.com/support/programs/cc-support-policy.html#cce)


<br />

### Before updating Helmut please consider our [update guideline](https://github.com/moovit-gmbh/helmut4/blob/master/INSTALLATION_GUIDE.md)

### Versioning
#### Release (snapshot/product) versions:
The product version is defined as <br> 
_Helmut_Version.Major_snapshot.Snapshot_patch_ <br>
The current version is 4.6.0 and the next snapshot after the following development cycle will be 4.7.0. If a snapshot gets patched there will be a 4.6.x

#### Endpoint (microservice/docker image) versions:
These are only relevant if you manually update specific microservices (e.g. via portainer). <br>
In release 4.1.0 we switch to semantic versioning for all our microservice endpoints starting with 4.1.0.1 meaning: <br>
_Helmut_Version.Major_change.Minor_change.Patch_ <br>
As an example the next bugfix of one of the endpoints (e.g. streams) would lead to a snapshot version of 4.1.0.2, a breaking change that is not downwards  compatible (within that endpoint) would result in a 4.2.0.1

Due to the fact, that we decoupled the microservice versioning from the release (snapshot / product) version, there might be mixed version numbers for a single snapshot. Like a 4.3.0.1 container verion in a 4.5.0 snapshot. In such an environment a snapshot update will not force the update of all microservices, and therefore won't download docker images that are unchanged. This will result in a smaller downtime and fewer untagged/unused but still cached images on the host system.

### Known issues
- Creating a project without attaching any metadata may corrupt the project in the database. If this occurs, there will no longer be an option to open the project using HelmutFX
- Canceling a job in synchronous path (during running status) and restarting the job afterwards does not proceed with the stream ("Stream has been canceled")
- The Helmut4 Windows client 4.2.0.35 shipped with stable release 4.7.0 is not signed yet. The conformation of this will be made soon. You will be updated once the client customizations have been finished. 

### Non-supported Adobe Versions
development
- any Beta version (24.x+)


### Supported Adobe Versions

#### 4.7.0
- Premiere: 22.x to 23.6.x
- After Effects: 22.x to 23.6.x
- AME: 22.x to 23.6.x // [AME CC22 limitation](https://github.com/moovit-gmbh/helmut4#440)

**Please reinstall the client after upgrading to CC23!**

#### 4.6.0 | 4.6.1 | 4.6.2
- Premiere: 22.x to 23.6.x
- After Effects: 22.x to 23.6.x
- AME: 22.x to 23.6.x // [AME CC22 limitation](https://github.com/moovit-gmbh/helmut4#440)

**Please reinstall the client after upgrading to CC23!**


#### 4.5.0
- Premiere: 22.x to 23.2.x
- After Effects: 22.x to 23.2.x
- AME: 22.x to 23.2.x // [AME CC22 limitation](https://github.com/moovit-gmbh/helmut4#440)

**Please reinstall the client after upgrading to CC23!**


#### 4.4.0
- Premiere: 15.x to 22.6.x, 23.0
- After Effects: 18.x to 22.6.x, 23.0
- AME: 15.x to 22.6.x, 23.0
  - AME: 22.3.0 is not supported due to an internal AME change 
  - AME 22.3.1+ / 22.4.x / 22.5.x requires Helmut client 4.2.0.8 or above

**Please reinstall the client after upgrading to CC23!**

***Known issue:*** - Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.

#### 4.3.0
- Premiere: 15.x to 22.6.x
- After Effects: 18.x to 22.6.x
- AME: 15.x to 22.6.x
  - AME: 22.3.0 is not supported due to an internal AME change
  - AME 22.3.1+ / 22.4.x / 22.5.x requires Helmut client 4.2.0.8 or above

***Known issue:*** - Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.


#### 4.2.0
- Premiere: 15.x to 22.2.x
- After Effects: 18.x to 22.2.x
- AME: 15.x to 22.2.x

***Known issue:*** - Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.

#### 4.1.0
- Premiere: 15.x to 22.2.x
- After Effects: 18.x to 22.2.x
- AME: 15.x to 22.2.x

***Known issue:*** - Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.

#### 4.0.6.x + 4.0.7.x:
- Premiere: 14.0 to 15.4.x
- After Effects: 17.0 to 18.4.x
- AME: 14.9.x to 15.4.x

***Known issue:*** - Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.

#### 4.0.5.x:
- Premiere/AME: <= 15.1 (mcc_license/client:4.0.6.1 required)

#### 4.0.4.x:
- Premiere/AME: <= 14.9.x
