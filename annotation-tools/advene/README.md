# Annotation examples from Advene

Advene sources can be downloaded from
https://github.org/oaubert/advene (git tree).

You can run the application directly from the sources (on linux at
least, Windows and MacOS X work but need some setup to work), or
download an installer from https://www.advene.org/

## Content of the files

`Rudi_and_Mireille.azp` is an Advene package, converted from
`elan/Rudi_and_Mireille.eaf` using the ELAN import filter present in
Advene. Note that if you want to have a look at the insides of the
.AZP file, it is only an XML file stored inside a Zip file.

`Rudi_and_Mireille.jsonld` is the conversion of the previous file into
WebAnnotation, with the convention of mapping types/tiers to
AnnotationCollectiobs.

`Rudi_and_Mireille-roundtrip_import.azp` is the roundtrip import of
the previous JSON-LD file inside Advene, to be able to compare them.

## How to test import filters?

From the Advene sources, you can run

`scripts/import_package list` to get a list of available import
filters.

Then you can run

`scripts/import_package ELAN_importer source.eaf destination.azp`

to export the `source.eaf` ELAN file into a `destination.azp` Advene package, which you can open in Advene.

You can also simply launch the Advene GUI and use the `File/Import
file...` menu.

## How to test export filters?

From the Advene sources, you can run

`scripts/export_package list` to get a list of available export
filters.

Then you can run

`scripts/import_package -o split WebAnnotationExporter source.azp destination.jsonld`

to export the `source.azp` Advene package into a `destination.jsonld`
webannotation file (note: the `-o split` option is necessary to
activate the 1-collection-per-type behaviour).

You can also simply launch the Advene GUI and use the `File/Export`
menuitem.
