# OmegaT project samples with XLIFF

This repo contains two sample projects to show how the Okapi XLIFF filter can be used in OmegaT for both translation and editing tasks:

-   Use `XLIFF_untranslated_OMT` for translation tasks.
-   Use `XLIFF_pretranslated_OMT` for editing tasks (verification, adaptation, revision, etc.).

In the first case, the target node in the XLIFF files must be empty.

In the second case, the translation unit must be approved (in other words, all `trans-unit` nodes in the file must have the `approved="yes"` attribute-value pair).

## Contents

-   The _projects_ folder contains the two OmegaT projects.
-   The _packages_ folder contains the two OmegaT projects, packed.
-   The _template_ folder contains a OMT package template (containing no files).
