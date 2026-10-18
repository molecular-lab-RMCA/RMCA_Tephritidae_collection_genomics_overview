# Public Provenance

## Purpose

This file records how the public overview relates to the private operational RMCA Tephritidae Collection Genomics repository.

## Canonical source

The complete operational repository is private:

`molecular-lab-RMCA/RMCA_Tephritidae_collection_genomics`

It contains detailed scripts, configuration, audit material and operational documentation that are not all appropriate for public release.

The public repository is a publication surface only.

## Source-of-truth rule

Public technical statements should be derived from reviewed public-safe source material under the private repository's `public/` directory.

Public publication must not be used to overwrite or redefine the private operational record.

## Publication record

For each substantive public update, record:

- private source commit;
- public destination commit;
- files published;
- date;
- notable content changes;
- image or media credits where applicable.

### Initial publication, 18 October 2026

Private source branch: `public-overview-v1`

Reviewed private source commit: `3b418ced65cb7743d6497d006f66f6cb5b01434e`

Canonical private `main` merge commit: `9db5b60daaad22d1ee92b75c321d1e3a930f33e3`

Public content snapshot after publishing README and technical documents: `1d71da7357c8406c03029f839a95f9dff4b2b6c7`

Published text files:

- `README.md`
- `TECHNICAL_OVERVIEW.md`
- `PROVENANCE.md`
- `IMAGE_CREDITS.md`

### Graphical-asset publication, 18 October 2026

Binary asset publication/rename commit: `26221f8addaf42f0c621f3246529c09b810b53b4`

Published assets:

- `assets/collection_genomics_workflow.jpg`
  - bytes: `247813`
  - SHA256: `70bc4eed5b26430e6f14f29bc61c3ccde9876b22eb928324e3e6d1b9d22ef236`
  - Git blob: `917ec5cd084b63130b533c674b75dcf05ac65ac1`
- `assets/why_this_system_matters.jpg`
  - bytes: `184054`
  - SHA256: `8ee7520de14b64622ff1b25490410f4a75693c6a3943ca198b24b166295ee184`
  - Git blob: `20554149ded8a87340a524e50679e84b4690ee13`

Both graphics use a male *Ceratitis quilicii* reference supplied for the project.

Image/reference credit: **© Antoine Franck / CIRAD**.

README embedding commit: `6f56beb8dbc7838137236ae984707bfb0fb8b89b`

Image-credit linkage commit: `59411fcdacb0b6041e265cf3d3d3ad8efd56ba0e`

Asset checksum documentation commit: `160eb438f70a285fb638092fbcc5dc8f82f38070`

Credit-format correction commit: `694b0be9f79cf81dd1dc04771ad1c88d435816e4`

## Reproducibility principle

The goal is that a public statement can be traced back to a versioned private source without exposing private collection records, storage paths, raw data or internal audit packages.
