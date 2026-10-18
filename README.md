# RMCA Tephritidae: From Collections to Genomics

This directory contains the **public-safe source material** for the RMCA Tephritidae Collection Genomics overview.

The public overview is intended to serve two audiences at the same time:

1. the general public, students and collaborators who want to understand what the system does and why it matters;
2. researchers, collection managers, laboratory staff and data stewards who need the conceptual and methodological detail behind the system.

The operational repository remains private because it contains detailed audit evidence, internal source material, operational metadata and local storage information.

## At a glance

![RMCA Tephritidae: From Collections to Genomics](assets/RMCA_Tephritidae_From_Collections_to_Genomics.png)

Graphical overview of the workflow linking collection vouchers, laboratory records, genomic files, reproducible analysis and downstream publication. Featured specimen: RMCA_ENT_000011071, *Ceratitis quilicii*.

## In plain language

Natural-history collections are most useful when the physical specimen, the laboratory work performed on it, the DNA derived from it, the genomic data produced from that DNA and the analyses based on those data can all be traced back to one another.

This project builds that traceability for the RMCA Tephritidae collection.

The aim is not to force every kind of information into one database. Instead, each system keeps the type of information it is best suited to manage, while explicit links and reproducible procedures connect the pieces.

## Why this matters

The system is designed around six practical principles:

**Collections first.** Physical specimens remain the biological foundation of the system.

**Voucher-linked genomics.** Physical voucher specimens anchor the identity of linked DNA extracts, residual specimen material and genomic datasets.

**Laboratory traceability.** Structured MLab workbooks preserve wet-laboratory provenance.

**Secure data stewardship.** Large sequencing files remain in managed RMCA storage rather than in GitHub.

**Reproducible research.** Code, configuration, manifests and audit summaries are versioned.

**Public access.** Curated collection information can be published downstream through DARWIN when appropriate.

## Core lineage

The biological and digital lineage is:

```text
collection lot
    |
individual voucher
    |
optional distinct physical sample
    |
extraction batch
    |
DNA extract
    |
sequencing dataset
    |
digital asset
    |
file instance
    |
analysis
```

An optional Sample is created only when a genuinely distinct physical tissue or body-material object exists. A laboratory row, tube label or spreadsheet line does not by itself create a new biological entity.

## Systems and authority

No single platform is the complete system.

| System | Operational role | Authority boundary |
| --- | --- | --- |
| **Access** | Daily relational hub for collection and collection-genomics links | Curated collection relationships and operational collection-genomics entities |
| **MLab** | Wet-laboratory source record | Recorded laboratory observations, processing metadata and archived workbook provenance |
| **RMCA NAS** | Large-file storage | Presence and byte identity of raw and important derived genomic file instances |
| **GitHub** | Reproducible methods and provenance | Versioned code, configuration, manifests, documentation and compact audit evidence |
| **DARWIN** | Downstream institutional publication | Existing DARWIN object identity and the institutional publication layer |

Authority is therefore **field-specific and object-specific**.

For example, a checksum can establish that two FASTQ files are byte-identical, but it cannot prove which insect they came from. Biological identity comes from the curated voucher and molecular provenance chain.

## Reproducibility model

Every important operational result should be traceable to four things:

1. the source object or source file;
2. the explicit rule used to interpret it;
3. the executable script or documented manual procedure that applied the rule;
4. audit evidence sufficient to verify the result.

Historical source databases are preserved.

Operational database changes are scripted, backed up and validated.

Biological entities are not invented solely to satisfy a target software schema.

Large raw genomic data do not belong in GitHub.

DARWIN is treated as a downstream publication layer rather than as the operational master database.

## Current public status

A versioned operational collection-genomics schema has been established.

The first controlled voucher registration has been validated in the operational database without altering historical source records.

The NAS-dependent continuation of that pilot is intentionally paused while development proceeds on the broader architecture, documentation, genomic dataset model, digital-asset model, manifest standards and downstream interoperability.

## Technical documentation

For a more detailed description of the architecture, entity model, authority rules, audit model and reproducibility requirements, see:

[Technical overview](TECHNICAL_OVERVIEW.md)

For the public/private publication boundary and synchronization record, see:

[Public provenance](PROVENANCE.md)

For visual material and image attribution, see:

[Image credits](IMAGE_CREDITS.md)

## Public and private boundary

This public material intentionally excludes:

- private collection records;
- unpublished specimen-level operational data;
- raw sequence files;
- exact internal storage paths;
- detailed internal audit packages;
- credentials, tokens and infrastructure details.

The private operational repository remains the canonical source for the complete workflow.

The public repository is a deliberately limited publication surface derived from reviewed public-safe source material.
