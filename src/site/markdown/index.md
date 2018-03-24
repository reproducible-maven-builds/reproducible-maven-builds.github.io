Reproducible Maven Builds
---------------

Getting reproducible builds with Java, ie. builds that always produce the same binary output, requires some tweaks
since Java is not reproducible-friendly from the beginning: jar files, with files order and timestamp, is a first
natural source of variation. In addition to issues caused by Java, some Maven plugins cause additional variations: see
[Maven Reproducible/Verifiable Builds Wiki page](https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=74682318).

