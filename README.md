# Helmut4
This is a public representation for the private product [Helmut4](https://www.helmut.de/) by [MoovIT GmbH](https://www.moovit.de).

### Before updating Helmut please consider our [update guideline](https://github.com/moovit-gmbh/helmut4/blob/master/INSTALLATION_GUIDE.md)

### Versioning
#### Release (snapshot/product) versions:
The product version is defined as <br> 
_Helmut_Version.Major_snapshot.Snapshot_patch_ <br>
The current version is 4.1.0 and the next snapshot after the following development cycle will be 4.2.0. If a snapshot gets patched there will be a 4.1.X

#### Endpoint (microservice/docker image) versions:
These are only relevant if you manually update specific microservices (e.g. via portainer). <br>
In release 4.1.0 we switch to semantic versioning for all our microservice endpoints starting with 4.1.0.1 meaning: <br>
_Helmut_Version.Major_change.Minor_change.Patch_ <br>
As an example the next bugfix of one of the endpoints (e.g. streams) would lead to a snapshot version of 4.1.0.2, a breaking change that is not downwards  compatible (within that endpoint) would result in a 4.2.0.1

Due to the fact, that we decoupled the microservice versioning from the release (snapshot / product) version, there might be mixed version numbers for a single snapshot. Like a 4.3.0.1 container verion in a 4.5.0 snapshot. In such an environment a snapshot update will not force the update of all microservices, and therefore won't download docker images that are unchanged. This will result in a smaller downtime and fewer untagged/unused but still cached images on the host system.

### Known issues
- Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.

### Non-supported Adobe Versions
development
- Premiere: 22.3.x / 22.4.x / 22.5.x
- After Effects: 22.3.x / 22.4.x / 22.5.x
- AME: 22.3.0 due to an internal AME issue 
- - AME 22.3.1+ / 22.4.x / 22.5.x requires Helmut client 4.2.0.8 or above
- Beta versions

### Supported Adobe Versions
4.2.0
- Premiere: 15.X to 22.2.x
- After Effects: 18.X to 22.2.x
- AME: 15.X to 22.2.x

4.1.0
- Premiere: 15.X to 22.2.x
- After Effects: 18.X to 22.2.x
- AME: 15.X to 22.2.x

4.0.6.x + 4.0.7.x:
- Premiere: 14.0 to 15.4.x
- After Effects: 17.0 to 18.4.x
- AME: 14.9.x to 15.4.x

4.0.5.x:
- Premiere/AME: <= 15.1 (mcc_license/client:4.0.6.1 required)

4.0.4.x:
- Premiere/AME: <= 14.9.x

![helmut-family](https://sev.moovit24.de/uploads/TW9vdklUIEdtYkg/OxHA6b6M3JAoqhup7HTVSUgew9Tt0DP66E8JJZSFe0v8xxDoRfxYuOzzl9g5jR3ElGWTcsuu6NQ1xjS3VlpOdRNDco5vmnP1vVbW/Helmut-4-Family-Logo-2.png)
