# OmegaT project samples with XLIFF

This repository contains some sample projects to simulate in a simplified manner how a workflow (including both translation and editing tasks) would be implemented, either using XLIFF or the original files:

-   The _projects_ folder contains the OmegaT projects, unpacked.
-   The _packages_ folder contains the OmegaT projects, packed.
-   The _template_ folder contains a OMT package template (containing no files).

The packed and unpacked versions have the same content. The unpacked projects are provided so that files can be inspected without the need to download and unpack projects first.

## Naming

In the names of the sample projects provided, `QQ` stands for `questionnaires`.

On the other hand, `pretranslated source` refers to source files that have a translation:

```xml
<trans-unit id="tu11">
  <source xml:lang="en">Not interested</source>
  <target xml:lang="ar">غير مهتم</target>
</trans-unit>
```

Whereas `untranslated source` refers to source files that do not have a translation:

```xml
<trans-unit id="tu11">
  <source xml:lang="en">Not interested</source>
  <target xml:lang="ar" />
</trans-unit>
```

## Workflow simulation

The following structure of directories simulates a simplified workflow for new materials ("new") and one where some translations already exist ("transfer"):

```
.
├── NEW
│   ├── 01_ToTranslation
│   │   ├── HTML-XML_QQ_OMT.omt
│   │   └── XLIFF_QQ_untranslated-source_OMT.omt
│   ├── 02_FromTranslation
│   │   ├── HTML-XML_QQ_OMT.omt
│   │   └── XLIFF_QQ_untranslated-source_OMT.omt
│   ├── 03_ToVerification
│   │   ├── HTML-XML_QQ_OMT.omt
│   │   ├── XLIFF_QQ_pretranslated-source_OMT.omt
│   │   └── XLIFF_QQ_untranslated-source_OMT.omt
│   └── 04_FromVerification
│   │   ├── HTML-XML_QQ_OMT.omt
│       ├── XLIFF_QQ_pretranslated-source_OMT.omt
│       └── XLIFF_QQ_untranslated-source_OMT.omt
└── TRANSFER
    └── 01_ToTransfer
        ├── HTML-XML_QQ_OMT.omt
        └── XLIFF_QQ_untranslated-source_OMT.omt
```

The "new" workflows exemplify a regular translation + verification task, from the starting point where the materials only exist in the source language up to the point where the target-language version(s) of the materials have been produced.

The "transfer" workflow can be applicable to different scenarios: e.g. for a trend transfer task, or for a version that borrows and adapts from another common version rather than translating from scratch, or for a component that must be consistent with other components already translated.

Here, the two workflows are separated for clarity, but in practice both get mixed often, i.e. a regular translation often requires transfers from existing translations.

## Projects

For every task, there's a `ToX` folder and a `FromX` folder, to exemplify the project that is outgoing (dispatched) to the user and the project that is incoming (delivered) from the user.

### Translation task

IN the project handed off to the translator, the working TM of the project has no translations. Therefore unless a reference TM is added target files would be identical to the source files if they were generated.

Dispatched:

-   `HTML-XML_QQ_OMT`: contains monolingual XML and HTML files in English
-   `XLIFF_QQ_untranslated-source_OMT`: contains untranslated XLIFF files (source in English, empty target)

In the projects handed back from the translator, the working TM has now a translation for every segment in the project. The translated files can now be generated, which would be:

-   `HTML-XML_QQ_OMT`: monolingual XML and HTML files in the target language (Arabic)
-   `XLIFF_QQ_untranslated-source_OMT`: translated XLIFF files (source in English, populated target in Arabic)

### Verification task

Project `XLIFF_QQ_untranslated-source_OMT` is the same project that the translator handed back, which has source XLIFF files with empty target and translations stored in the working TM of the project. The same applies to the `HTML-XML_QQ_OMT` project, where the source files are still the same and the translations are stored in the working TM.

In contrast, the input to project `XLIFF_QQ_pretranslated-source_OMT` is already bilingual, the project contains translated source XLIFF files (e.g. generated from `NEW > 02_FromTranslation > XLIFF_QQ_untranslated-source_OMT`). The translation is already included in the source files, whereas the working TM of the project can be empty.

In both `XLIFF_QQ_untranslated-source_OMT` and `XLIFF_QQ_pretranslated-source_OMT`, the final translation including edits made by the verifier will be stored in the working TM of the project, and it will be used when generating the target XLIFF files.

In the project `XLIFF_QQ_pretranslated-source_OMT`, edited translations saved in the working TM will replace the original translations included in the source files.

The following diff reports show the changes in these two packages made during verification:

-   https://capps.capstan.be/xdiff/r/XLIFF_QQ_untranslated-source_OMT.omt/20220302204427/
-   https://capps.capstan.be/xdiff/r/XLIFF_QQ_pretranslated-source_OMT.omt/20220302204458/
