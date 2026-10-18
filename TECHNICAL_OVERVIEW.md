# Technical Overview

## Scope

RMCA Tephritidae Collection Genomics is an operational information architecture linking physical collection curation, molecular laboratory provenance, DNA extracts, genomic datasets, digital files, reproducible analyses and downstream institutional publication.

It is intentionally distributed across several systems rather than implemented as one monolithic database.

## 1. Collection core

### Historical collection model

The historical Access database distinguishes collection lots from individually catalogued material.

The principal collection concepts are:

```text
Specimen
    collection lot

FrozenCollection
    individually identified frozen specimen
    linked to a parent Specimen lot

dry collection
    individually catalogued pinned specimen
    linked to a parent Specimen lot
```

The operational collection-genomics layer is additive. Historical tables are retained as evidence and are not destructively redesigned.

### Operational voucher

A curated individual becomes an operational genomic voucher through `CG_Voucher`.

A voucher may link to a historical frozen individual, a historical dry individual, or another validated collection object.

Identifiers such as AB codes remain operational identifiers rather than relational primary keys.

## 2. Molecular laboratory model

The molecular model distinguishes work packages, extraction processes and physical molecular objects.

```text
CG_LabBatch
    archived laboratory workbook or work package

CG_ExtractionBatch
    extraction event or extraction identifier within that work package

CG_DNAExtract
    physical DNA extract
```

A DNA extract always retains direct voucher provenance.

### Optional Sample

`CG_Sample` is optional.

It is used only when the laboratory process involves a genuinely distinct physical sample such as a separated tissue or body part.

A spreadsheet row or laboratory label alone is insufficient evidence for creating a Sample.

This rule prevents artificial proliferation of biological entities.

## 3. Minimum operational Access schema

The first operational collection-genomics migration created a minimum relational extension containing:

- 10 `CG_` tables;
- 94 fields;
- 16 enforced relationships;
- 14 indexes;
- 11 unique indexes;
- no database-level default values.

Required values are inserted explicitly by controlled workflows.

The schema is additive to the historical collection database.

## 4. Laboratory source authority

Completed MLab workbooks are source records.

Before a workbook is used operationally, the intended procedure records:

- filename;
- archive location;
- cryptographic checksum;
- workbook/template version where available;
- relevant dates and operator information;
- project context where documented;
- the exact mapping configuration used;
- import or registration audit evidence.

Corrected workbooks should be versioned rather than silently replaced.

## 5. Genomic data model

Large genomic files are not stored in Access or GitHub.

The digital model separates logical datasets from digital assets and physical file instances:

```text
GenomicDataset
    |
DigitalAsset
    |
FileInstance
```

A sequencing dataset is the biological/technical dataset.

A digital asset is a logical digital object belonging to that dataset.

A file instance is one stored copy at one storage location.

This distinction is important when the same bytes exist under more than one filename or storage path.

## 6. Checksum semantics

Cryptographic checksums establish byte identity.

They do **not** establish:

- specimen identity;
- taxonomic identity;
- provenance;
- biological equivalence.

Those meanings come from the relational provenance chain.

For example, a renamed FASTQ copy with an identical SHA256 is another file instance of the same digital asset rather than a new biological sequencing dataset.

## 7. Storage model

RMCA NAS storage is represented conceptually as:

```text
StorageRoot + RelativePath
```

rather than by workstation-specific drive letters.

This separates persistent storage identity from transient local mount points.

## 8. GitHub role

GitHub stores the reproducible method rather than the raw genomic payload.

The private operational repository contains:

- scripts;
- machine-readable configuration;
- schema specifications;
- mapping rules;
- methodological documentation;
- compact audit summaries;
- release and handoff documentation.

Substantive analytical and migration scripts document their purpose, conceptual rationale, methodological rationale, source authority, inputs, outputs, mutation behavior, validation criteria and reproducible run command.

## 9. DARWIN publication model

DARWIN is a downstream institutional publication layer.

It is not the operational master database for collection genomics.

A controlled DARWIN synchronization should preserve:

- existing DARWIN UUIDs;
- explicit update-versus-create semantics;
- institutional scope;
- bounded exclusions;
- source authority;
- rollback/restart capability;
- batch manifests;
- post-write quality assurance.

Information is published only when the target route can represent it appropriately.

## 10. Host-association policy

Host associations are not flattened into DARWIN when doing so would lose essential reliability structure.

Internal host information can therefore remain richer than the downstream public representation.

This is an example of a general principle: publication convenience must not redefine the scientific meaning of the source data.

## 11. Audit model

Operational results are expected to be auditable at several levels.

### Source identity

Input databases, workbooks and important reference files are pinned by checksum when feasible.

### Rule identity

Machine-readable configuration records how source fields or cases are interpreted.

### Method identity

Scripts are versioned in Git.

### Result identity

Tracked audit summaries record the outcome of important validation or migration steps.

### Mutation control

Write workflows define preconditions, backups, transaction behavior and post-write checks.

## 12. Historical immutability and operational mutability

The system distinguishes:

**Historical immutable sources**

Original historical databases and source files are preserved and never silently corrected in place.

**Validated checkpoints**

Curated checkpoints record accepted historical corrections and can be frozen for downstream release work.

**Operational successor**

The collection-genomics successor is intentionally mutable, but only through controlled and auditable procedures.

## 13. Public/private separation

The public repository documents the architecture and reproducibility principles without publishing private operational content.

The private repository remains the canonical complete source.

The public publication surface is therefore informative but deliberately incomplete.

## 14. Current development boundary

The architecture has passed its first controlled real-voucher registration.

The next NAS-dependent molecular continuation is intentionally frozen.

Current work can continue independently on:

- documentation;
- genomic dataset semantics;
- digital-asset semantics;
- manifests;
- project linkage;
- analysis provenance;
- external identifiers;
- controlled publication routes.

This boundary is explicit so that a paused pilot cannot be mistaken for a failed or incomplete validation.
