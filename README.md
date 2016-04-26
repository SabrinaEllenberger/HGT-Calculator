# HGT-Calculator

[HGT Calculator] combines four different tree-based and non-tree-based
approaches for detection of horizontal gene transfer (HGT) between
bacteria and protozoa. The program is able to distinguish between
multiple and single events by this novel approach. It excludes ancient
endosymbiotic gene transfer (EGT) events and helps to detect HGT events,
when other methods cannot be applied due to the realities of normal
experiment-based HGT-studies: very small or incomplete data sets, and
lacking unequivocal knowledge about phylogenetic relationships or 
genome composition. We demonstrated the identification of HGT with this new
algorithm for ten genes in the parasitic trypanosomatid _Leishmania major_,
the non-human pathogenic _Trypanosoma rangeli_, and the symbiont-harbouring
trypanosomatid _Strigomonas culicis_ ([Ellenberger et al., 2016][HGT Calculator paper1]).
These are clearly distinguished from ten other genes, which are considered as
ancient genes, and were used as negative control. For those, HGT scores are
always zero. This new application is a helpful tool to make first decisions
on HGT events in new protozoan species, with just a few sequences available,
in comparison to known species of the same or similar taxonomic lineages.
In addition, the new algorithm can detect HGT events that are consequences
of endosymbiotic interactions, as shown for the example of homoserine
dehydrogenase. This approach distinguishes these clearly from ancient EGT
events, going back to the ancestors of organelles.

[HGT Calculator] is distributed under the [GPLv3 license][GPLv3 license],
and runs under Windows and Linux.
Please make sure your local workstation has a Java 8 SDK installation
(a distribution can be downloaded from [Oracle][Java]) and availability of
an internet connection.

See the [manual][Manual] for a full description of the tool and the
[tutorial][Tutorial] for an example run of [HGT Calculator] for isocitrate
dehydrogenase genes.

In order to view the manual (PDF document), you will need to have the free Adobe
Acrobat Reader software installed on your computer. Users can download the latest
version of Adobe Acrobat Reader from https://get.adobe.com/de/reader/.

If you use [HGT Calculator] for your published research, please cite [Ellenberger et al., 2016][HGT Calculator paper1].
Thank you!

[HGT Calculator] can be started with a double click on the downloaded HGT-Calculator.jar or
executed from the terminal via java -jar HGT-Calculator.jar.

Please note: Java applications can sometimes generate problems with antivirus
software and permissions. If so, add HGT-Calculator.jar to the whitelist of your
antivirus program and change HGT-Calculator.jar to be an executable jar file!
Other problems can be caused by updates of the UniProt database. This can be fixed
by downloading the newest version of the UniProt JAPI ([uniprot-japi-client.zip][japi])
and copying the unpacked JARs from uniprot-japi-client\lib into the directory HGT-Calculator_lib.

[HGT Calculator]: https://github.com/SabrinaEllenberger/HGT-Calculator
[HGT Calculator paper1]: http://zs.thulb.uni-jena.de/servlets/MCRFileNodeServlet/jportal_derivate_00245407/2016ECR0310_Ellenberger%20etal.pdf
[GPLv3 license]: http://www.gnu.org/licenses/gpl-3.0.html
[Manual]: https://github.com/SabrinaEllenberger/HGT-Calculator/Manual.pdf
[Tutorial]: https://github.com/SabrinaEllenberger/HGT-Calculator/blob/master/Tutorial.md
[japi]: http://www.ebi.ac.uk/uniprot/japi/
[Java]: http://java.com/de/download/
