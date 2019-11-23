Reproducible Maven Builds
---------------

Getting reproducible builds with Java, ie. builds that always produce the same binary output, requires some tweaks
since Java is not reproducible-friendly from the beginning: jar files, with files order and timestamp, is a first
natural source of variation. In addition to issues caused by Java, some Maven plugins cause additional variations: see
[Maven Reproducible/Verifiable Builds Wiki page](https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=74682318).

There are 2 main strategies to get reproducible builds:

- post-process output to remove unwanted variance,

- change build behaviour to avoid variance from start.

Since november 2019, the second strategy is available: read [Maven - Guide to Configuring for Reproducible Builds](https://maven.apache.org/guides/mini/guide-reproducible-builds.html).

Before, reality required to be able to post-process while working on
initial variance removal (which may happen not only from [Apache Maven's Plugins](https://maven.apache.org/plugins/)
but also from Maven Plugins in the large ecosystem) and dealing with the hard compromises that may arise.

### Avoiding Variance From Start

[Maven - Guide to Configuring for Reproducible Builds](https://maven.apache.org/guides/mini/guide-reproducible-builds.html) summaries
how to configure your Maven build to get Reproducible Builds as part of your normal builds.

Work is tracked on [Maven Reproducible/Verifiable Builds Wiki page](https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=74682318).

### Post Processing Solutions

A few implementations are available:

- [Reproducible Build Maven Plugin](https://zlika.github.io/reproducible-build-maven-plugin/), a Maven Plugin from
  the large ecosystem that removes every known variance when bound at `pre-integration-test`
  [phase](https://maven.apache.org/ref/current/maven-core/lifecycles.html),

- [Byteman](http://byteman.jboss.org/) rules TBD
