## What is HyPhy?

HyPhy (**Hy**pothesis Testing using **Phy**logenies) is an open-source software package for the analysis of genetic sequences (in particular the inference of natural selection) using techniques in phylogenetics, molecular evolution, and machine learning. It features a rich scripting language for limitless customization of analyses. Additionally, HyPhy features support for parallel computing environments (via message passing interface). HyPhy has over 8000 registered users and has been cited in over 900 peer-reviewed publications (Google Scholar). 
<!-- UPDATE THIS, also check citation counts above.: Continued development of HyPhy is currently supported in part by an NIGMS R01 award 1R01GM093939. -->

You can use HyPhy in two ways:

* Run HyPhy our accompanying webserver [Datamonkey](http://datamonkey.org) (or see the [development version of Datamonkey](http://test.datamonkey.org) for some newer methods).
* Run HyPhy from the command line on your local computer/server. Follow [these instructions](installation.md) for download and installation. 

## Choosing a method for selection inference

HyPhy provides a suite of diverse phylogenetic methodologies for testing specific hypotheses about selection in protein-coding and/or amino-acid multiple sequence alignments. Which method you select will depend on your specific question. Below we recommend several methods for different purposes, linked to more in depth descriptions. Tutorials for using these methods are also available [here](tutorials/current-release-tutorial).

### Are individual sites subject to *pervasive* (across the whole phylogeny) positive or purifying selection?
* [FEL](./methods/selection-methods/#fel) (**F**ixed **E**fects **L**ikelihood) is suitable for small-to-medium sized data sets.
* [SLAC](./methods/selection-methods/#slac) (**S**ingle-**L**ikelihood **A**ncestor **C**ounting) is an approximate method with accuracy similar to FEL, but suitable for larger datasets. However, SLAC is not suitable for highly-diverged sequences.
* [FUBAR](./methods/selection-methods/#fubar) (**F**ast, **U**nconstrained **B**ayesian **A**pp**R**oximation) is suitable for medium-to-large data sets and is expected to have more power than FEL for detecting pervasive selection at sites. **FUBAR is the preferred approach for inferring pervasive selection.**


### Are individual sites subject to *episodic* (at a subset of branches) positive or purifying selection?
* [MEME](./methods/selection-methods/#meme) (**M**ixed **E**ffects **M**odel of **E**volution) tests for episodic selection at individual sites. Note that MEME does not accept *a priori* branch specifications. **MEME is the preferred approach for detecting positive selection at individual sites.**
* [aBSREL](./methods/selection-methods/#absrel) (**a**daptive **B**ranch-**S**ite **R**andom **E**ffects **L**ikelihood) is an improved version of the common "branch-site" class of models. aBSREL allows either for *a priori* specification of branch(es) to test for selection, or can test each lineage for selection in an exploratory fashion. Note that the exploratory approach will sacrifice power.


### Has a gene experienced positive selection at any site on a particular branch or set of branches?
* [BUSTED](./methods/selection-methods/#busted) (**B**ranch-**S**ite **U**nrestricted **S**tatistical **T**est for **E**pisodic **D**iversification) will test for gene-wide selection at pre-specified lineages. This method is particularly useful for relatively small datasets (fewer than 10 taxa) where other methods may not have sufficient power to detect selection. **This method is not suitable for identifying specific sites subject to positive seleciton.**

### Has gene-wide selection pressure been relaxed or intensified along a certain subset of branches?
* [RELAX](./methods/selection-methods/#relax) tests for a relaxation (e.g. where purifying selection has become less stringent) or an intensification (e.g. where purifying selection has become stronger) of selection pressures along a specified set of "test" branches. **This method is not suitable for detecting positive selection.**

<!--
### Are individual sites within a gene subject to *directional* selection, i.e. selection pressure to evolve towards a specific set of amino acids?
* [FADE](./methods/selection-methods/#fade) tests for directional selection at specific sites in *protein* alignments.
-->

