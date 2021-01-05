# GraphNER

This repository contains the preliminary code for reproducing the results reported in the paper "[GraphNER: Named Entity Recognition as Graph Classification](https://openreview.net/forum?id=vfpW-kRvLgu)" (currently under review).

## Overview
The code is organized as notebooks, to be used as follows:
* `final_generate_gazetteers.ipynb`: to generate the gazeteers from Wikidata (by specifying a list of QIDs corresponding to the classes)
* `edge_list_generation.ipynb`: to generate the graph structure to build the graph embeddings
* `graph_embeddings_generation.ipynb`: to generate node embeddings using [GEM library](https://github.com/palash1992/GEM) algorithms (e.g. node2ve, SDNE..)
* `nodes_classifier.ipynb`: to train a model for the node embeddings
* `autoencoder_embeddings.ipynb`: to generate auto-encoder embeddings from the binary graph representations
* `autoencoder_nn_classification.ipynb`: to train a model for the auto-encoder embeddings
* `GCN-node-simple-features.ipynb`: to train a GCN on the CoNLL-2003 task

The code will be streamlined into stand-alone configurable scripts and fully documented soon.

## Required modules
* Python 3.8
* PyTorch 1.7
* [GEM](https://github.com/palash1992/GEM)
* [PyTorch Geometric](https://pytorch-geometric.readthedocs.io/en/latest/)
* [SPARQLWrapper](https://github.com/RDFLib/sparqlwrapper)
* tqdm
* Numpy
* Pandas

:warning:	This code runs on a CUDA11.0-enabled GPU, please install the compatible version of the modules for your hardware.

## Results
Method           | Accuracy | Micro-F1 | Macro-F1 
-----------------|----------|----------|---------
Binary           | 91.0     | 90.7     | 77.9 
Binary+          | 94.4     | 94.2     | 81.9 
Binary++         | 94.3     | 93.8     | 82.3 
Auto-encoder-100 | 87.2     | 86.7     | 57.6
Auto-encoder-500 | 90.4     | 89.9     | 68.3
Auto-encoder-2000| 91.8     | 91.5     | 71.7 
Node2Vec-300     | 93.8     | 94.1     | 82.0
Node2Vec-500     | 93.8     | 94.1     | 82.5
Node2Vec-1000    | 93.8     | 94.1     | 82.1 
GCN              | 96.1     | 96.1     | 86.3 
**GCN+**         | **96.5** | **96.5** | **88.8**

