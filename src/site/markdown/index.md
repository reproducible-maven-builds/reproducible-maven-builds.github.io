Reproducible Maven Builds
---------------

Getting reproducible builds with Java, ie. builds that always produce the same binary output, requires some tweaks
since Java is not reproducible-friendly from the beginning: jar files, with files order and timestamp, is a first
natural source of variation. In addition to issues caused by Java, some Maven plugins cause additional variations: see
[Maven Reproducible/Verifiable Builds Wiki page](https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=74682318).

There are 2 main strategies to get reproducible builds:

- post-process output to remove unwanted variance,

- change build behaviour to avoid variance from start.

Ideally the second strategy would be the only one, but reality requires to be able to post-process while working on
initial variance removal (which may happen not only from [Apache Maven's Plugins](https://maven.apache.org/plugins/)
but also from Maven Plugins in the large ecosystem) and dealing with the hard compromises that may arise.

### Post Processing Solutions

A few implementations are available:

- [Reproducible Build Maven Plugin](https://zlika.github.io/reproducible-build-maven-plugin/), a Maven Plugin from
  the large ecosystem that removes every known variance when bound at `pre-integration-test`
  [phase](https://maven.apache.org/ref/current/maven-core/lifecycles.html),

- [Byteman](http://byteman.jboss.org/) rules TBD

### Avoiding Variance From Start

Some work is tracked on [Maven Reproducible/Verifiable Builds Wiki page](https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=74682318).

One objective of this site is to test some implementations of the key issue now: what to do at jar/zip files level?
What timestamp to use? What's the impact of files ordering on performance (after having implemented parallel
compression exactly to improve performance, but at the cost of unpredictable files order, which was not
an issue until now...)?
