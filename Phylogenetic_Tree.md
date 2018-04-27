
### Project Description

This project will analyze and visualize a tree constructed from [rdp 16s database](https://www.drive5.com/sintax/rdp_16s_v16.fa.gz).

#### Input file

** rdp_16s_v16_reads_50.fa**: Random 50 reads from [rdp 16s database](https://www.drive5.com/sintax/rdp_16s_v16.fa.gz)

#### Tools need

**[reformat.sh](https://jgi.doe.gov/data-and-tools/bbtools/bb-tools-user-guide/reformat-guide/)**:  This will pick 50 random reads from [rdp 16s database]((https://www.drive5.com/sintax/rdp_16s_v16.fa.gz).

**[ETE Toolkit](http://etetoolkit.org/docs/latest/index.html)**: Analysis and visualization of trees.

#### Commands

```bash
# Select only 50 random reads
reformat.sh in=rdp_16s_v16.fa.gz out=rdp_16s_v16_reads_50.fa sample=50 overwrite=true

```



Align the reads and build the tree using ETE Toolkit

Clean the fasta file


```bash
%%bash 
sed  -ie 's/\"//g'  rdp_16s_v16_reads_50.fa
sed 's/;/,/' rdp_16s_v16_reads_50.fa | sed 's/tax=//'| sed 's/:/_/g' | sed 's/_[^~]*\,d/,d/' | sed 's,;,,' > rdp_16s_v16_reads_50_clean.fa
grep ">" rdp_16s_v16_reads_50_clean.fa  | sed 's/,/ /'| sed 's/>//' >fasta_headers.txt
sed -ie 's/,.*//' rdp_16s_v16_reads_50_clean.fa
```


```bash
%%bash
ete3 build -w standard_fasttree -n  rdp_16s_v16_reads_50_clean.fa  -o ./rdp_16s_tree --clearall
```

    Toolchain path: /users/PAS0471/osu8405/envs/py27/bin/ete3_apps 
    Toolchain version: unknown
    ['clustalo_default-none-none-fasttree_full']
    
          --------------------------------------------------------------------------------
                      ETE build (3.1.1) - reproducible phylogenetic workflows
    
          Citation:
    
           Huerta-Cepas J, Serra F and Bork P. ETE 3: Reconstruction, analysis and
           visualization of phylogenomic data. Mol Biol Evol (2016)
           doi:10.1093/molbev/msw046
    
          (Note that a list of the external programs used to complete all necessary
          computations will be shown after workflow execution. Those programs should
          also be cited.)
    
          --------------------------------------------------------------------------------
          
    [32mINFO[0m -  Testing x86-64  portable applications...
           clustalo: [32mOK[0m - 1.2.4
          dialigntx: [32mOK[0m - This is DIALIGN-TX Version 1.0.2 - A Multiple Sequence alignment program.
           fasttree: [32mOK[0m - FastTree Version 2.1.8 Double precision (No SSE3), OpenMP (1 threads)
             iqtree: [32mOK[0m - IQ-TREE multicore version 1.5.5 for Linux 64-bit built Jun  2 2017
             kalign: [32mOK[0m - Kalign version 2.04, Copyright (C) 2004, 2005, 2006 Timo Lassmann
              mafft: [32mOK[0m - MAFFT v6.861b (2011/09/24)
             muscle: [32mOK[0m - MUSCLE v3.8.31 by Robert C. Edgar
              phyml: [32mOK[0m - . This is PhyML version 20160115.
         pmodeltest: [32mOK[0m - pmodeltest.py v1.4
              raxml: [32mOK[0m - This is RAxML version 8.2.11 released by Alexandros Stamatakis on June 2017.
     raxml-pthreads: [32mOK[0m - This is RAxML version 8.2.11 released by Alexandros Stamatakis on June 2017.
             readal: [32mOK[0m - readAl v1.4.rev6 build[2012-02-02]
             statal: [32mOK[0m - statAl v1.4.rev6 build[2012-02-02]
            tcoffee: [32mOK[0m - PROGRAM: T-COFFEE Version_11.00.8cbe486 (2014-08-12 22:05:29 - Revision 8cbe486 - Build 477)
             trimal: [32mOK[0m - trimAl v1.4.rev6 build[2012-02-02]
    [32mINFO[0m -  Starting ETE-build execution at Fri Apr 27 13:26:55 2018
    [32mINFO[0m -  Output directory /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree
    [32mINFO[0m -  Erasing all existing npr data...
    [1;37;43mWRNG[0m -  Using existing dir: /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree/db
    [32mINFO[0m -  Reading nt sequences from rdp_16s_v16_reads_50_clean.fa...
    
    
    [1;37;43mWRNG[0m -  50 target sequences
    [32mINFO[0m -  ETE build starts now!
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:26:55 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   (W[0m) [34mMultiSeqTask[0m (50 nt seqs, MSF, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -   ([1;34mD[0m) [34mMultiSeqTask[0m (50 nt seqs, MSF, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:26:57 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   (W[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:26:59 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   (W[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:01 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:03 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:05 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:07 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:09 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:11 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:13 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -   ([1;34mD[0m) [31mAlgTask[0m (50 nt seqs, Clustal-Omega, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:15 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   (W[0m) [32mTreeTask[0m (50 nt seqs, FastTree, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:17 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   (W[0m) [32mTreeTask[0m (50 nt seqs, FastTree, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:19 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [32mTreeTask[0m (50 nt seqs, FastTree, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:21 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   ([1;31mR[0m) [32mTreeTask[0m (50 nt seqs, FastTree, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -   ([1;34mD[0m) [32mTreeTask[0m (50 nt seqs, FastTree, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  [1;37;40m Updating tasks status:[0m (Fri Apr 27 13:27:23 2018)
    [32mINFO[0m -  Thread [1;37;40mclustalo_default-none-none-fasttree_full[0m: pending tasks: [1;33m1[0m of sizes: 50
    [32mINFO[0m -   (W[0m) [36mTreeMergeTask[0m (50 nt seqs, TreeMerger, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -   ([1;34mD[0m) [36mTreeMergeTask[0m (50 nt seqs, TreeMerger, /[1;37;40mclustalo_d...ttree_full[0m)
    [32mINFO[0m -  [1;37;40mWaiting 2 seconds[0m
    [32mINFO[0m -  Assembling final tree...
    [32mINFO[0m -  Done thread [1;37;45mclustalo_default-none-none-fasttree_full[0m in 1 iteration(s)
    [32mINFO[0m -  Writing final tree for [1;37;40mclustalo_default-none-none-fasttree_full[0m
       /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.nw
       /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.nwx (newick extended)
    [32mINFO[0m -  Writing final tree alignment [1;37;40mclustalo_default-none-none-fasttree_full[0m
       /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.used_alg.fa
    [32mINFO[0m -  Writing root node alignment [1;37;40mclustalo_default-none-none-fasttree_full[0m
       /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.fa
    [32mINFO[0m -  Generating tree image for [1;37;40mclustalo_default-none-none-fasttree_full[0m
       /fs/project/PAS0471/osu8405/Python/Phylogenetic_Tree_ETE/rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.png
    [32mINFO[0m -  Done
    [32mINFO[0m -  Deleting temporal data...
       ========================================================================
             The following published software and/or methods were used.        
                   *** Please, do not forget to cite them! ***                 
       ========================================================================
       Sievers F, Wilm A, Dineen D, Gibson TJ, Karplus K, Li W, Lopez R,
          McWilliam H, Remmert M, Söding J, Thompson JD, Higgins DG. Fast,
          scalable generation of high-quality protein multiple sequence
          alignments using Clustal Omega. Mol Syst Biol. 2011 Oct 11;7:539.
          doi: 10.1038/msb.2011.75.
       Huerta-Cepas J, Serra F, Bork P. ETE 3: Reconstruction, analysis and
          visualization of phylogenomic data. Mol Biol Evol (2016) doi:
          10.1093/molbev/msw046
       Price MN, Dehal PS, Arkin AP. FastTree 2 - approximately maximum-
          likelihood trees for large alignments. PLoS One. 2010 Mar
          10;5(3):e9490.


### Display tree 


```python
from IPython.display import Image
Image(filename='rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.png')
```




![png](output_6_0.png)



### Display tree with Alignment


```python
from ete3 import PhyloTree,  TreeStyle
tree1 = PhyloTree("rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.nw")
tree1.link_to_alignment("rdp_16s_tree/clustalo_default-none-none-fasttree_full/rdp_16s_v16_reads_50_clean.fa.final_tree.used_alg.fa")
#tree1.render(file_name="rdp_alignment_tree.png", dpi=300 , w=1600, h=1000 )
tree1.render("%%inline", h=150, units="mm", dpi=100)
```




![png](output_8_0.png)




```python
# Read the headers to annotate the tree

with open("./fasta_headers.txt", "r") as f:
    headers=f.read().splitlines()
```


```python
# Create the database of headers
header_dict={}

# Function to replace characters

def remove_level_identification_char(string):
    # This will remove taxa level identification character
    
    if string.startswith("d_"):
        return {0:string.replace("d_", "")}
    elif string.startswith("p_"):
        return {1:string.replace("p_", "")}
    elif string.startswith("c_"):
        return {2:string.replace("c_", "")}
    elif string.startswith("o_"):
        return {3:string.replace("o_", "")}
    elif string.startswith("f_"):
        return {4:string.replace("f_", "")}
    elif string.startswith("g_"):
        return {5:string.replace("g_", "")}
    
        

for item in headers:
    #temp dictionary to hold taxa
    temp={}
    node,taxa=item.split()
    level_seperated =  taxa.split(",")[:-1]
    for  i in level_seperated:
        if temp:
            temp.update(remove_level_identification_char(i))
        else:
            temp=remove_level_identification_char(i)
            
        
    header_dict[node]=temp

```

[Colour Palatte is here.](http://etetoolkit.org/docs/latest/reference/reference_treeview.html#color-names)


```python
colour_palatte={0:"#708090", 1:"#F5F5DC", 2:"#E6E6FA", 3:"#FFA07A", 4:"#CD853F", 5:"#F08080"}
```


```python
def custom_layout(node):
    if node.is_leaf():
        # Add an static face that handles the node name
        faces.add_face_to_node(nameFace, node, column=0)
        lineage =  header_dict[node.name]
        for key, level in lineage.items():
            longNameFace = faces.TextFace(level+" ", fsize=8, fgcolor= "Black")
            longNameFace.background.color = colour_palatte[key]
            faces.add_face_to_node(longNameFace, node, column=key,  aligned=True)
            
```


```python
from ete3 import Tree, faces, TreeStyle
nameFace = faces.AttrFace("name", fsize=10, fgcolor="#191970")
ts = TreeStyle()
ts.show_leaf_name = False
ts.show_branch_length=True
ts.show_branch_support = True
ts.layout_fn = custom_layout
tree1.render("%%inline", tree_style=ts)
```




![png](output_14_0.png)




```python

```
