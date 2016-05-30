Help
====

This contains short instructions and some frequently asked questions concerning the usage of HGT Calculator.

Why does the program not start?
-------------------------------

You have to download HGT-Calculator.zip and **unpack** it.

The HGT-Calculator.jar and the file folder HGT-Calculator_lib need to be saved at the **same location** of your workspace.

You will need a **Java 8** installation (a distribution can be downloaded from [Oracle][java]). Older versions may trigger
this error message: "java.lang.UnsupportedClassVersionError".

And an **internet connection** is required to run HGT Calculator.

You have three possibilities to start HGT-Calculator:

1: Start HGT Calculator by double-clicking the downloaded HGT-Calculator**.jar**

This works only, if the HGT-Calculator.jar is an **Executable Jar File** on your system and if you have **linked .jar files**
with your Java(TM) Platform SE binary. Alternatively, you can use decompression software, such as an unzip utility, to view
the files in the jar archive. You can change the default program by right-clicking the .jar file. Select _Open With_, then
select _Choose default program_. In the _Open With_ window, click the _Browse_ button to open the File Explorer window. You
need to find the executable file for the software program you want to set as the default program to open the jar file (e.g
C:\Program Files\7-Zip\7z.exe) or the path to your java installation (e.g. C:\Program Files (x86)\Java\jre1.8.0_91\bin\java.exe).

2: Start HGT Calculator by double-clicking the downloaded batch file [Start_HGT-Calculator**.bat**][bat]

The batch file needs to be saved at the **same location** of your workspace as HGT-Calculator.jar and the file folder HGT-Calculator_lib.
This works only on Windows.

3: Execute the file from the terminal

Go to the directory the HGT-Calculator.jar is in, write "cd your path" and press enter.
To execute the file write "java -jar HGT-Calculator.jar" and press enter again.

Please note: Java applications can sometimes generate **problems with antivirus software** and **permissions**. If so, add
HGT-Calculator.jar to the whitelist of your antivirus program. If Windows is blocking it from running, right click the .jar
file and select  _properties_. In the bottom right corner it might tell you "Windows has blocked the functionality...". Next
to it there is a check box labeled "Unblock". **Uncheck the box** and click on _apply_. Then you can run HGT-Calculator.


What is the Start file?
-----------------------

The Start file defines the properties of your workspace. Here, you can state the proteins and organisms you want to concern in
your data set.

Please note: The name of the Start file needs to **start with “Start_”** and **ends with “.txt”**! **Do not select an existing
text file!** This causes trouble when the architecture of the new workspace is build up. If you want to use an existing Start
file, copy the text into the new Start file of the workspace. If you want to create a new Start file in an existing workspace,
write your new Start file with an editor and save it under "Data\Download\Input\Start_xy.txt". Than you can open an existing 
workspace with the parameters of a new Start file.

If the Start file template is not opened automatically, because
on your computer .txt is **not linked with an editor**, you have to open it manually or change the default program for text
files.

You will have to add your information to the Start file template by hand, before you can open this workspace the first time. 

You can change the default program of the text file by right-clicking the Start_xy.txt. Select _Open With_, then
select _Choose default program_. In the _Open With_ window, click the _Browse_ button to open the File Explorer window. You
need to find the executable file for the software program you want to set as the default program to open the text file (e.g
C:\Windows\system32\notepad.exe).


Why do I get an empty list of search results?
---------------------------------------------

If the first cell of the table contains "null | euk" instead of, for example, "ICDH | euk" your input of a protein name or
protein abbreviation went wrong. You need to **press enter** after typing the name, a query or anything else!

The search for sequences requires an **internet connection**!

Other problems can be caused by **updates of the UniProt database and UniProt JAPI**. This can be fixed by downloading the
newest version of the UniProt JAPI ([uniprot-japi-client.zip][japi]), unpack the .zip and copying the unpacked JARs from
_uniprot-japi-client\lib_ into your _\HGT-Calculator_lib_. Please pay attention that you do not delete the files for Clustal W 
(clustalw2.exe) and InterProScan (iprscan5_lwp.pl) by accident!


How do I select my sequences properly?
--------------------------------------

You need to start a search always with the **eukaryotic sequences**, because their subtypes are needed for clustering of the prokaryotic protein subtypes. Be sure that the check box "Eukaryotic" is ticked for your first search.

You need to **press enter** after typing your query!

Select only one sequence per organism and protein subtype. Else an error message will occur: "More than one sequence for this subtype". If you want to test multiple sequences, start them in separate data sets. This error can also occure if you clicked twice to save the download list. Than you have to delete the previouse list by hand.

If you have more than one protein subtype, check which of your sequences really belong to the subtype you are interested in. Such multiple sequence types can influence the topology of your trees.

You should select at least an equal number of prokaryotic and eukaryotic sequences to get a balanced tree. A higher number of prokaryotic sequences would be better.

You need some sequences of multi-cellular eukaryotes as outgroup. Choose sequences for a fungus (_Saccharomyces cerevisiae_), a plant (_Arabidopsis thaliana_), and a metazoon (_Homo sapiens_), if possible.


What does the error message "Gene file is missing" mean?
--------------------------------------------------------

The nucleotide sequences of selected genes are downloaded from KEGG. Some protein sequences do not have a **KEGG entry**. Therefore, 
the gene can not be downloaded and the gene file is missing. This error usually can be ignored. Such files are added by other
accession numbers later on. Whether they were added properly or not you can check on the tab _Log_
(e.g. "> write missing file: Strigomonas (S9UPN9) | ICDH_1 | Genes"). The complete log file is saved in \workspace\Data\Download\Log\Log_xy.

Another reason for this error could be an **interrupted internet connection** during the download of sequences.

What does the error message "Query sequence nearly identical with prokaryotic sequence" mean?
---------------------------------------------------------------------------------------------

Such a sequence could be either a real HGT from an endosymbiont into the host or an artefact of the genome sequencing procedure. This needs to be checked. If the gene is located on a scaffold with other eukaryotic genes, it is a HGT. If it is located on a small contig without other genes or only bacterial genes it is more likely an artefact.


What does the error message "Server error" in the BLAST frame mean?
-------------------------------------------------------------------

The BLAST search run on the UniProt database. If too many connections are attempted and time out, this will cause a "500 Internal Server Error." The BLAST search is started again after a short break. Check the BLAST output in "Data\Download\Blast\Blast_xy" if BLAST search of all sequences has been finished.

If the BLAST frame is frozen, stop HGT Calculator via task manager or close the window of the terminal. And start the procedure again.


How can I select the single prokaryotic sequence for my small and single trees?
-------------------------------------------------------------------------------

To start Clustal W with the default files enter just "**-** > protein" to get the protein trees of your sequences. To start Clustal W with specific files, enter "**path_to_euk_seq.txt; path_to_prok_seq.txt** > protein", for example, "DownloadList_ICDH.txt; DownloadList_ICDH_prok.txt > protein".
If you want to define the single prokaryotic organism enter, for example, "- > protein **# BACSU**" for _Bacillus subtilis_. This is quite helpfull to include endosymbiotic bacteria in the trees. Otherwise, the prokaryotic organism is chosen randomly.


Why do I not get trees after starting Clustal W and Neighbor Joining?
---------------------------------------------------------------------

Check if there are any FASTA files as input for Clustal W in your workspace under "Data\Download\Fasta\Fasta_xy".

This step requires an **internet connection**!

Check if clustalw2.exe is located in your _\HGT-Calculator_lib_. Maybe it was deleted during an update of the UniProt JAPI.
You can extract the executables from the original _\HGT-Calculator_lib_ in the [HGT-Calculator.zip][zip].


Why is the tree viewer an empty frame?
--------------------------------------

Check if there are any trees in your workspace under "Data\Download\Newick\Newick_xy".



[java]: https://java.com/de/download/
[bat]: https://github.com/SabrinaEllenberger/HGT-Calculator/blob/master/Start_HGT-Calculator.bat
[japi]: http://www.ebi.ac.uk/uniprot/japi/
[zip]: https://github.com/SabrinaEllenberger/HGT-Calculator/blob/master/HGT-Calculator.zip
