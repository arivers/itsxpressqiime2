# ITSxpress-qiime2: A qiime2 plugin using ITSxpress to rapidly trim the Internally transcribed spacer (ITS) region of FASTQ files


## Authors

  - Adam R. Rivers, US Department of Agriculture, Agricultural Research Service
  
  - Kyle Weber

## Introduction

The internally transcribed spacer region is a region between highly conserved the small subunit (SSU) of rRNA and the large subunit (LSU) of the rRNA. In Eukaryotes it contains the 5.8s genes and two variable length spacer regions. In amplicon sequening studies it is common practice to trim off the conserved (SSU, 5,8S or LSU) regions. Bengtsson-Palme et al. (2013) published software the software package ITSx to do this.

ITSxpress is designed to support the calling of exact sequence variants rather than OTUs. This newer method of sequence error-correction requires quality score data from each sequence, so each input sequence must be trimmed. ITSXpress makes this possible by taking FASTQ data, de-replicating the sequences then identifying the start and stop sites using HMMSearch. Results are parsed and the trimmed files are returned. The ITS 1, ITS2 or the entire ITS region including the 5.8s rRNA gene can be selected. ITSxpress uses the hmm model from ITSx so results are comprable.

## Installation
### Requirments/Dependencies

In order to consider install ITSxpress-qiime2, it is **required to install qiime2.**

Here is the installation page to [install qiime](https://docs.qiime2.org/2018.6/install/)

Once qiime2 has been installed, you can now install the dependices for ITSxpress.

1. Add the bioconda channel to the qiime2.
  
		conda config --add channels bioconda
			 
2. Install hmmer.
	
		conda install hmmer
		
3. Install bbmap.

		conda install bbmap
	
4. Install ITSxpress

		conda install itsxpress 
	or
	
		pip install itsxpress
		
### ITSxpress-qiime2

To install the ITSxpress plugin for qiime, a few steps are needed.

1. Clone the project onto your computer.

		git clone https://github.com/kweber1/ITSxpress-qiime2.git
		
2. Install the project using pip.

		pip install .

		pip install -e .
		
3. Open your qiime2 environment.
	
		qiime dev refresh-cache
		
4. Check to see if the ITSxpress plugin is installed.

		qiime itsxpress
		
![Image of console](https://i.gyazo.com/bc013672a324123209b284f889eaa277.png)

## Usage

The main command being 

```
qiime itsxpress
```

1. ```qiime itsxpress trimSingle```
	
| command-requirement | description |
| :-----------: | :------------ |
| ```--i-per-sample-sequences``` | The artifact that contains the sequence file(s). Either Joined Paired or just a single fastq. One file sequences in the qza data folder. |
| ```--p-region``` | The regions ITS2, ITS1, and ALL.|
| ```--p-taxa``` |Select the taxonomic group sequenced: {Alveolata, Bryophyta, Bacillariophyta, Amoebozoa, Euglenozoa, Fungi, 			Chlorophyta, Rhodophyta, Phaeophyceae, Marchantiophyta, Metazoa, Microsporidia, Oomycota, Haptophyceae, 		Raphidophyceae, Rhizaria, Synurophyceae, Tracheophyta, Eustigmatophyceae, Apusozoa, Parabasalia}.|
| ```--p-threads ``` | the amount of threads to use.|
| ```--o-trimmed``` | The resulting trimmed sequences from ITSxpress in a qza format. |

2. ```qiime itsxpress trimPair```

| command-requirement | description |
| :-----------: | :------------ |
| ```--i-per-sample-sequences``` | The artifact that contains the sequence file(s). Only Paired can be used. Two files sequences in the qza data folder. |
| ```--p-region``` | The regions ITS2, ITS1, and ALL.|
| ```--p-taxa``` |Select the taxonomic group sequenced: {Alveolata, Bryophyta, Bacillariophyta, Amoebozoa, Euglenozoa, Fungi, 			Chlorophyta, Rhodophyta, Phaeophyceae, Marchantiophyta, Metazoa, Microsporidia, Oomycota, Haptophyceae, 		Raphidophyceae, Rhizaria, Synurophyceae, Tracheophyta, Eustigmatophyceae, Apusozoa, Parabasalia}.|
| ```--p-threads ``` | the amount of threads to use.|
| ```--o-trimmed``` | The resulting trimmed sequences from ITSxpress in a qza format. |

## License information

This software is a work of the United States Department of Agriculture, Agricultural Research Service. 17 U.S.C. 	Section 105 states that "Copyright protection under this title is not available for any work of the United States 	Government". While I anticipate that this work will be released under a CC0 public domain attribution, only the USDA 	ARS Office of Technology transfer has the authority to make that determination.
	
		
	
	
	



