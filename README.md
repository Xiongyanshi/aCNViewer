aCNViewer: comprehensive genome-wide visualization of absolute copy number and copy neutral variations

Dependencies:

* APT ([Affymetrix Power Tools | http://www.affymetrix.com/estore/partners_programs/programs/developer/tools/powertools.affx#1_2]) if you plan to process Afymetrix SNP arrays

* a recent version of R with ggplot2 installed for generating different graphs:
  + ggplot2
  + ASCAT (will be automatically installed if not already installed) if you are analyzing raw SNP array data
  + Sequenza if you are analyzing paired bams

* Python with version >= 2.5


![Overview of CNViewer:](/img/aCNViewer.png?raw=true "Overview of aCNViewer")  


***


# Tutorial about aCNViewer: comprehensive genome-wide visualization of absolute copy number and copy neutral variations

## Requirements:


* Download Affymetrix Power Tools from Affymetrix website and uncompress it in BIN_DIR


* Test data set snpArrays250k_sty.tar.gz: https://drive.google.com/file/d/0B9ZcXWVM-9y1SDktTTBjVVd1ZVk/view?usp=sharing


Let's respectively call _DATA_DIR_ and _BIN_DIR_ the location where respectively snpArrays250k_sty.tar.gz and APT archive have been uncompressed.

### Test1: generate histogram from CEL files with a window size of 2Mbp
`python aCNViewer.py -f DATA_DIR/snpArrays250k_sty/ -c DATA_DIR/snpArrays250k_sty/hg18.chrom.sizes -t OUTPUT_DIR --dendrogram 0 --histogram 1 -G "BCLC staging" -u 1 -m 1 -C DATA_DIR/snpArrays250k_sty/centro.txt -w 2000000 --sampleFile DATA_DIR/snpArrays250k_sty/GSE9845_clinical_info2.txt -b BIN_DIR --gcFile DATA_DIR/snpArrays250k_sty/GC_Affy250k.txt --platform Affy250k_sty -l DATA_DIR/snpArrays250k_sty/LibFiles/ --gw6Dir DATA_DIR/snpArrays250k_sty/gw6/`

If ASCAT is not installed and if you want to install it into a custom folder, please add the following option to the previous command line: '--rLibDir RLIB'

Compare generated histograms with the ones in DATA_DIR/snpArrays250k_sty/expectedResults/test1


### Test2: generate histogram from ASCAT segment files with a window size of 2Mbp
`python aCNViewer.py -f DATA_DIR/snpArrays250k_sty/GSE9845_lrr_baf.segments.txt -c DATA_DIR/snpArrays250k_sty/hg18.chrom.sizes -t OUTPUT_DIR --dendrogram 0 --histogram 1 -G "BCLC staging" -u 1 -m 1 -C DATA_DIR/snpArrays250k_sty/centro.txt -w 2000000 --sampleFile DATA_DIR/snpArrays250k_sty/GSE9845_clinical_info2.txt -b BIN_DIR`

Compare generated histograms with the ones in DATA_DIR/snpArrays250k_sty/expectedResults/test2
thon with version 