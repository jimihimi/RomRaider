## RomRaider Stock Rom Repository

This git repo contains all the known stock ROM files for Subaru vehicles shared on the RomRaider forum
http://www.romraider.com/forum

## ECU package-image import (2026-11-24)

This import adds 730 distinct, identity-supported ECU images extracted from local
SSM package collections. Another six SHA-256-identical images were already in
this repository, so they were not copied. The [import manifest](ECU-IMPORT-MANIFEST.csv)
lists every distinct image, its package/member aliases, source path, byte count,
SHA-256, and destination. Source files were copied, never changed.

The placement plan uses exact package numbers in Subaru's updater catalogs and
their `Country Spec` field. The 302 new images marked `N.AMERICA` are under
`USDM`, following this repository's existing North American convention. This
label does not establish that a file is exclusive to the United States. The
428 other new images are under top-level [`unknown`](unknown): 423 carry
`EUROPE/GENERAL` in the updater catalog, four carry `GENERAL`, and one has
conflicting `GENERAL`/`N.AMERICA` rows. None of those values establishes a
specific country. The `unknown` directory is deliberately flat and its filenames
retain package number, inner member name, and a hash prefix.

An official [Subaru of America service bulletin hosted by NHTSA](https://static.nhtsa.gov/odi/tsbs/2023/MC-10231316-0001.pdf)
independently links packages such as `22765AP813.pak` and `22765AR673.pk2`
to US-market Crosstrek and Forester model years. An [earlier bulletin](https://static.nhtsa.gov/odi/tsbs/2019/MC-10168604-0001.pdf)
likewise links `22765AK041.pak` to a 2017 BRZ. These are spot checks, not proof
of fitment for every imported image. The requested `parts.subaru.com` lookup
could not be used because the site returned HTTP 403 and search produced no
part-specific result; no fitment claim rests on that site.

The recorded validation is exact inner identity text plus byte-for-byte SHA-256
matching of the extracted output. Firmware checksums, processor selection,
load addresses, and full physical-flash coverage have not been independently
verified. A package image may represent only the logical update payload. The
`.hex` extension follows the existing repository convention; files are binary.
Do not infer a flashable image from their presence here.
