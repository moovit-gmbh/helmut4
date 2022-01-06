# Helmut4
This is a public representation for the private product [Helmut4](https://www.helmut.de/) by [MoovIT GmbH](https://www.moovit.de).

### Versioning
From release 4.1.0 we switch to semantic versioning for all our microservice endpoints starting by 4.1.0.1 like follows
Helmut_Version.Major_change.Minor_change.Patch
As an example the next bugfix of one of the endpoints would lead to a version 4.1.0.2, an breaking change that is not downwards compatible to 4.2.0.1

The product version is defined with 
Helmut_Version.Major_snapshot.Snapshot_patch
As an example here the next snapshot after the next development cylcle will be 4.2.0 and if patched snapshot is needed in between there will be an 4.1.X

Due to the fact, that we decoupled the microservice versioning from the product version (snapshot version) there might be mixed version numbers for a single snapshot, like 4.3.0.1 container verion in a 4.5.0 snapshot. In such an environment a snapshot update will not force the update of all microservices and therefore docker image pulls anymore, which results in a smaller downtime and less untagged/unused but still cached images on the host system.

### Known issues
- Save Project not possible with Premiere Version 15.2 if project has been opend via Helmut4. Please skip this version and use latest 15.4.

### Supported Adobe Version
4.1.0
- Premiere: 15.X to 22.X
- After Effects: 18.X to 22.X
- AME: 15.X to 22.X

4.0.7.x:
- Premiere: 14.0 to 15.4.1
- After Effects: 17.0 to 18.4.1
- AME: 14.9 to 15.4.1

4.0.5.x:
- Premiere/AME: <= 15.1 (mcc_license/client:4.0.6.1 required)

4.0.4.x:
- Premiere/AME: <= 14.9

![helmut-family](https://sev.moovit24.de/uploads/TW9vdklUIEdtYkg/OxHA6b6M3JAoqhup7HTVSUgew9Tt0DP66E8JJZSFe0v8xxDoRfxYuOzzl9g5jR3ElGWTcsuu6NQ1xjS3VlpOdRNDco5vmnP1vVbW/Helmut-4-Family-Logo-2.png)
