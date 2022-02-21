# OmegaT project package template

Here is an OmegaT project template that can be used to create OmegaT project packages.

## Preconditions

It is assumed that the user's OmegaT installation has been customized with the files available [here](https://github.com/capstanlqc/omegat_customization), as explained in our [installation and customization guide for OmegaT 5.7](https://slides.com/msoutopico/omegat5-installation-and-customization-guide-for-rtl/fullscreen).

Customization for version 5.7 of OmegaT is currently under testing and could be unstable. Please report any issues found.

## Steps

To create actual project package instances, proceed like this:

1. Put the source files in the `source` folder.
2. Change the target language code (text content of the `<target_lang>` node) in each project’s `omegat.project` file, replacing `xx-XX` with the actual correct expected code (see below).
3. Give the project package an appropriate name (observing some naming conventions, e.g. ending in `_OMT`).

## Language codes

The language code used in the project settings must be taken from the **OmegaT** column of cApStAn's [Language code finder](https://capps.capstan.be/langtags.php) (or fetched using the [language code basic API](https://github.com/msoutopico/langtags_basic_api)). Use the OmegaT tag that corresponds your three-letter PISA language code.

You can check OMT packages for language code compliance with [this utility](https://github.com/msoutopico/check_omt_langtags).
