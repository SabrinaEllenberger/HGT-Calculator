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
&#10141; "Start_Tutorial.txt"

This creates the following workspace architecture:  
workspace\Data\Download  
  * \Blast &#10141; results of the BLAST runs  
  * \DownloadLists &#10141; lists with sequence identifiers of the data sets  
  * \Fasta &#10141; FASTA files as input for ClustalW (Neighbor Joining)  
  * \Genes &#10141; downloaded nucleotide sequences  
  * \Input &#10141; start file of the workspace, look up files for average GC content and taxonomic lineages, input files for HGT Calculator  
  * \Log &#10141; reply log of HGT Calculator 
  * \Newick &#10141; Neighbor Joining trees in newick format  
  * \Output &#10141; results of HGT Calculator  
  * \UniProt &#10141; downloaded amino acid sequences  

and it creates a new start file template in workspace\Data\Download\Input, where you need to add your information:

Name of the data set > Tutorial  
Transfer from > Bacteria  
Transfer into > Protozoa  
Protein abbreviations >   
Prokaryotic organisms >   
Eukaryotic organisms >  

Please note: At the moment, HGT Calculator is only tested for the detection of HGT from bacteria into protozoa!  

&#10141; our example start file:

Name of the data set > Tutorial  
Transfer from > Bacteria  
Transfer into > Protozoa  
Protein abbreviations > ICDH  
Prokaryotic organisms > Streptomyces, Micrococcus, Aquifex, Cytophaga, Chlorobium, Synechococcus, Nostoc, Sinorhizobium, Neisseria, Vibrio, Escherichia, Desulfovibrio, Helicobacter, Thermotoga, Deinococcus, Bacillus, Candidatus Kinetoplastibacterium  
Eukaryotic organisms > Tetrahymena, Paramecium, Strigomonas, Leishmania, Trypanosoma, Toxoplasma, Plasmodium, Saccharomyces, Arabidopsis, Homo  

How to open a workspace
-----------------------

Click on the menu item File > Open and choose a start file ("Start_Tutorial.txt") from workspace\Data\Download\Input for opening a workspace.  
This opens the selected start file and the HGT Downloader window of HGT Calculator.  
Here, you need to enter a protein name ("Isocitrate dehydrogenase"), a suitable protein abbreviation (between two and four letters, "ICDH") and to tick the check box “Eukaryotic” to start with the search for eukaryotic sequences.

How to search for sequences with HGT Downloader
-----------------------------------------------

Before you can start to look for HGT events with HGT Calculator you will need a data set.  
You can prepare your data set with the help of HGT Downloader, a stand-alone application of HGT Calculator.  
HGT Downloader offers three possibilities to search for sequences:

1. Search > By UniProt ID  
2. Search > By KEGG Orthology ID  
3. Search > By Text Query

Please note: You need to start a search always with the eukaryotic sequences, because their subtypes are needed for clustering of the prokaryotic protein subtypes. Be sure that the check box "Eukaryotic" is ticked.

We start with a KEGG Orthology ID search. Click on the menu item Search > By KEGG Orthology ID and enter "K00031", the KEGG Orthology ID for isocitrate dehydrogenases.  

The result is a list with all sequences found for the eukaryotic organisms listed in the start file with the exception of _Strigomonas culicis_ and _Trypanosoma rangeli_ which can not be found in KEGG.

Select the sequences you want to add to your data set by ticking the boxes under "Selected". It should be nine sequences.  

Now, we need sequences for the last two organisms. For this, we go to the tab "Selection of organisms" and delete the ticks from the check boxes of the organisms we already added to our data set. We only keep "Strigomonas" and "Trypanosoma".

Click on the menu item Search > By Text Query and enter "all" to search for all isocitrate dehydrogenases of Strigomonas and Trypanosoma in the UniProt database.

Select the sequences you want to add to your data set by ticking the boxes under "Selected". It should be three additional sequences.

You can save all eukaryotic sequences from the two search steps (it should be 12) by clicking on the first cell of the results table which is labeled with "ICDH | euk".

After this, you can find your eukaryotic data set in   workspace\Data\Download\DownloadLists\DownloadLists_Tutorial\DownloadList_ICDH.txt.

In the next step, we repeat this search for creating a data set of prokaryotic sequences. For this, you need to tick the check box “Prokaryotic” in the HGT Downloader window. Again, we start with a KEGG Orthology ID search. Click on the menu item Search > By KEGG Orthology ID and enter "K00031", the KEGG Orthology ID for isocitrate dehydrogenases.

The result is a list with all sequences found for the prokaryotic organisms listed in the start file. Select the sequences you want to add to your data set by ticking the boxes under "Selected". It should be 16 sequences.

You can save all prokaryotic sequences from the search by clicking on the first cell of the results table which is labeled with "ICDH | prok" now.

After this, you can find your prokaryotic data set in workspace\Data\Download\DownloadLists\DownloadLists_Tutorial\DownloadList_ICDH_prok.txt.

How to get selected sequences
-----------------------------

Click on the menu item Start > HGT Downloader > Download to save all amino acid and nucleotide sequences of the download lists for this protein.

There are no KEGG IDs for the entries of _Strigomonas culicis_ and _Trypanosoma rangeli_. The program shows an error on the tab “Problems” ("Strigomonas_ICDH (S9UPN9) -> gene file is missing"), which usually can be ignored. Such files are added by other accession numbers later on. Whether they were added properly or not you can check on the tab “Log” ("> write missing file: Strigomonas (S9UPN9) | ICDH_1 | Genes"). The complete log file is saved in \workspace\Data\Download\Log\Log_Tutorial\.

How to start a BLAST search and visualize the results
-----------------------------------------------------

Click on the menu item Start > HGT Downloader > BLAST to start a BLAST search in the UniProt database for each entry of the download lists. The number of BLAST hits from Archaea, Bacteria and Eukaryotes, the Alien Index (AI) and a possible donor organism (if available) are saved in the first line of the file, followed by the BLAST hits of the search.

Click on the menu item Start > HGT Downloader > BLAST statistics to draw two plots for visualizing the ratio of BLAST hits in this data set. One figure is a bar diagram and the other one is a cross plot, which can be saved in  
\workspace\Data\Download\Blast\Blast_Tutorial_statistics_chart.jpg and  
\workspace\Data\Download\Blast\Blast_Tutorial_statistics_plot.jpg by clicking on the button "Save diagram".

You can see that the number of prokaryotic BLAST hits is higher for the isocitrate dehydrogenases of _Leishmania major_ and _Strigomonas culicis_. This is the first hint for a HGT event.

How to get Codon Usage Tables (CUT) for Codon Adaptation Index (CAI) calculation
--------------------------------------------------------------------------------

Click on the menu item Start > HGT Downloader > CAI calculation to download all codon usage tables you need from the [codon usage database][codonDB] and create a file with average GC content of all selected organisms. This file is saved in workspace\Data\Download\Input\GC_Content_Tutorial.txt. The codon usage tables are saved in workspace\Data\CodonUsageTables.

The codon adaptation index values are calculated following the implementation of [Xia][CAI] (2007) and saved in the eukaryotic download lists.

How to start Clustal W2 and visualize single trees
--------------------------------------------------

Click on the menu item Start > HGT Downloader > ClustalW & NJ to get Neighbor Joining trees at different resolution. When started for the first time, it creates a file with taxonomic clusters of all selected organisms in workspace\Data\Download\Input\Cluster_Tutorial.txt.

Enter two download lists for creating files with all sequences needed for tree reconstruction in FASTA format. For this tutorial it is sufficient to start Clustal W2 with the default files. For this, enter just "- > protein" to get the protein trees of your isocitrate dehydrogenases.

Now, the input files for ClustalW2, FASTA files with all sequences from the selected download lists, are saved in workspace\Data\Download\Fasta\Fasta_Tutorial. [ClustalW2] is started for multiple sequence alignment and creating Neighbor Joining trees. The trees are saved in newick format in workspace\Data\Download\Newick\Newick_Tutorial.

You need three trees:  
1. One large tree with all sequences (eukaryotic and prokaryotic):  
&#10141; ICDH_newickTree_prot.txt  
2. One small tree with all eukaryotic sequences and just one prokaryotic sequence per eukaryotic protein subtype:  
&#10141; ICDH_newickTree_small_prot.txt  
3. A single tree for each organism with just the sequences of this single organism, a fungus, a plant, a metazoon, and one bacterial sequence per eukaryotic protein subtype:  
   &#10141; ICDH_newickTree_single_Tetrahymena_prot.txt  
   &#10141; ICDH_newickTree_single_Paramecium_prot.txt  
   &#10141; ICDH_newickTree_single_Leishmania_prot.txt  
   &#10141; ICDH_newickTree_single_Strigomonas_prot.txt  
   &#10141; ICDH_newickTree_single_Trypanosoma_prot.txt  
   &#10141; ICDH_newickTree_single_Plasmodium_prot.txt  
   &#10141; ICDH_newickTree_single_Toxoplasma_prot.txt  
   and a single tree with sequences from a fungus, a plant and a metazoon but without any protozoon:  
   &#10141; ICDH_newickTree_single_sah_prot.txt

Click on the menu item Start > HGT Downloader > Tree viewer to see all single trees. Now, you can directly identify possible HGT events from the figures. Only the single trees of _Leishmania major_ and _Strigomonas culicis_ show a branch labeled as HGT. 

Final preparation of the data set
---------------------------------

All steps can also be prepared outside of HGT Downloader. The protein and gene files, for example, do not need to come from UniProt or KEGG databases. But the format and the path of the files need to be identical to the HGT Downloader output.

Click on the menu item Start > HGT Downloader > Write Input files to get the input files for HGT Calculator in workspace\Data\Download\Input:  
&#10141; Input_Tutorial_first.txt (lines ordered by protein name)  
&#10141; Input_Tutorial_second.txt (lines ordered by organism, including CAI values)

Check list:  
* Data sets selected separately for eukaryotic and prokaryotic organisms  
* Protein and gene sequences downloaded
* BLAST results for all selected sequences saved
* Codon usage tables downloaded and Codon adaptation index calculated
* Neighbor Joining trees for large, small and single trees saved in newick format
* Input files for HGT Calculator written

How to start HGT Calculator
---------------------------

Click on the menu item Start > HGT Calculator to start HGT Calculator. The Log file is saved in workspace\Data\Download\Log. The Output file is saved in workspace\Data\Download\Output. 

Interpretation of HGT Calculator results
----------------------------------------

The window of the Result manager is opened for visualizing the HGT Calculator results after calculating the HGT scores.

HGT Calculator is able to distinguish between single, multiple, and endosymbiotic gene transfer (EGT) events. Single HGT events have a HGT score higher than 45 and appear as the only score for this protein, which is higher than zero. Multiple events show several scores higher than 30 for one protein. EGT result in scores less than 30. We set the threshold for the
HGT scores to 45. To assure the incidence of a recent HGT event some criteria need to be fulfilled: The candidate sequence has a different protein subtype; the protein domains of this candidate sequence are typical for prokaryotic organisms; more than 50 % of the BLAST hits come from prokaryotic organisms; the alien index is larger than 45; the candidate sequence is clustered together with a prokaryotic sequence at all three levels of phylogenetic analysis (single, small, and large tree); and the
large tree can be split into a eukaryotic and a prokaryotic subtree to exclude ancient genes, that are conserved in prokaryotes as well as in eukaryotes. A threshold higher than 45 provokes to many false negatives. To make the difference between positive and negative candidates more clear, scores for candidates with less than 50 % bacterial sequences in their BLAST results (b) and without a positive score in single trees (t) are set to zero. This scores can be displayed in the results as intermediate scores, if the check box was ticked. If this led to a false negative, the HGT event may occurred a long time ago so that the sequences became more similar to eukaryotic sequences than to prokaryotic ones and is therefore most likely a EGT. Another reason why a HGT can only be validated by the intermediate score is the occurrence of two distinct HGT events in one data set. Both HGT sequences cluster together and therefore are not detected in the single tree. In _Strigomonas culicis_, for example, there are two different homoserine dehydrogenases. One homoserine dehydrogenase sequence seems to be the result of a multiple HGT event from firmicutes into trypanosomatids (low HGT scores &#10141; intermediate scores), whereas the other one seems to come from an endosymbiont strain of _Strigomonas culicis_ (higher HGT score).

[HGT Calculator paper1]: http://zs.thulb.uni-jena.de/servlets/MCRFileNodeServlet/jportal_derivate_00245407/2016ECR0310_Ellenberger%20etal.pdf
[japi]: http://www.ebi.ac.uk/uniprot/japi/
[java]: https://java.com/de/download/
[codonDB]: http://www.kazusa.or.jp/codon
[CAI]: http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2684136/pdf/ebo-03-53.pdf
[ClustalW2]: http://bioinformatics.oxfordjournals.org/content/23/21/2947.full.pdf
