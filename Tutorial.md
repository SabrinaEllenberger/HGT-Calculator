Tutorial for HGT Calculator
===========================

How to install HGT Calculator
-----------------------------

Here, we demonstrate the workflow of the algorithm of [Ellenberger et al., 2016][HGT Calculator paper1] using the example of
genes for isocitrate dehydrogenase. We chose isocitrate dehydrogenase as illustrative example, because it is an essential part
of the citric acid cycle in pro- and eukaryotes, and consequently occurs in all organisms of our test data set.

Download HGT-Calculator.jar + HGT-Calculator_lib and save them at the same location of your workspace.  
Start HGT Calculator by a double click on the downloaded HGT-Calculator.jar or execute the file from the terminal via

java -jar HGT-Calculator.jar.

You will need a Java 8 SDK installation (a distribution can be downloaded from [Oracle][java]) and an internet connection to run HGT Calculator.
Please note: Java applications can sometimes generate problems with antivirus software and permissions. If so, add
HGT-Calculator.jar to the whitelist of your antivirus program and change HGT-Calculator.jar to be an executable jar file!

Other problems can be caused by updates of the UniProt database. This can be fixed by downloading the newest version of
the UniProt JAPI ([uniprot-japi-client.zip][japi]) and copying the unpacked JARs from uniprot-japi-client\lib into your
\HGT-Calculator_lib.

How to create a new workspace
-----------------------------

Click on the menu item File > New and choose a directory for creating a new workspace. Enter the name of the start file and
click on “Create workspace”. Please note: The name of the start file needs to start with “Start_” and ends with “.txt” !  
-> "Start_Tutorial.txt"

This creates the following workspace architecture:  
workspace\Data\  
            * \Download  
            * \Blast  
            *	\DownloadLists  
            * \Fasta  
            * \Genes  
            * \Input  
            * \Log  
            * \Newick  
            * \Output  
            * \UniProt  

and it creates a new start file template, where you need to add your information:

Name of the data set > Tutorial  
Transfer from >  
Transfer into >  
Protein abbreviations >   
Prokaryotic organisms >   
Eukaryotic organisms >  

-> our example start file:

Name of the data set > Tutorial  
Transfer from > Bacteria  
Transfer into > Protozoa  
Protein abbreviations > ICDH  
Prokaryotic organisms > Streptomyces, Micrococcus, Aquifex, Cytophaga, Chlorobium, Synechococcus, Nostoc, Sinorhizobium, Neisseria, Vibrio, Escherichia, Desulfovibrio, Helicobacter, Thermotoga, Deinococcus, Bacillus, Candidatus Kinetoplastibacterium  
Eukaryotic organisms > Tetrahymena, Paramecium, Strigomonas, Leishmania, Trypanosoma, Toxoplasma, Plasmodium, Saccharomyces, Arabidopsis, Homo  

How to open a workspace
-----------------------

Click on the menu item File > Open and choose a start file (Start_Tutorial.txt) from the Input directory for opening a workspace.  
This opens the selected start file and the HGT Downloader window of the HGT Calculator.  
Here, you need to enter a protein name (Isocitrate dehydrogenase), a suitable protein abbreviation (between two and four letters, ICDH) and
to check the check box “Eukaryotic” to start with the search for eukaryotic sequences.

How to search for sequences with HGT Downloader
-----------------------------------------------

Before you can start to look for HGT events with the HGT Calculator you will need a data set.  
You can prepare your data set with the help of HGT Downloader, a stand alone application of HGT Calculator.  
HGT Downloader offers three possibilities to search for sequences:

1. Search > By UniProt ID  
2. Search > By KEGG Orthology ID  
3. Search > By Text Query

We start with a KEGG Orthology ID search. Click on the menu item Search > By KEGG Orthology ID and enter "K00031", the KEGG Orthology ID
for isocitrate dehydrogenases.  

The result is a list with all sequences found for the organisms listed in the start file with the exception of _Strigomona culicis_ and 
_Trypanosoma rangeli_ which can not be found in KEGG.

Select the sequences you want to add to your data set by ticking the boxes under "Selected". It should be nine sequences.  

Now, we need sequences for the last two organisms. For this, we go to the tab "Selection of organisms" and delete the ticks from the check
boxes of the organisms we already added to our data set. We only keep "Strigomonas" and "Trypanosoma".

Click on the menu item Search > By Text Query and enter "all" to search for all isocitrate dehydrogenases of Stigomonas and Trypanosoma in the UniProt database.

Select the sequences you want to add to your data set by ticking the boxes under "Selected". It should be three sequences.

You can save all eukaryotic sequences from the two search steps (it should be twelve) by clicking on the first cell of the results table which is labeled with "ICDH | euk".

After this, you can find your eukaryotic data set in workspace\Data\Download\DownloadLists\DownloadLists_Tutorial\DownloadList_ICDH.txt.

[HGT Calculator paper1]: http://zs.thulb.uni-jena.de/servlets/MCRFileNodeServlet/jportal_derivate_00245407/2016ECR0310_Ellenberger%20etal.pdf
[japi]: http://www.ebi.ac.uk/uniprot/japi/
[java]: https://java.com/de/download/

