# SemScale
An easy-to-use tool for semantic scaling of political text, based on word embeddings. Check out the working draft of our [political science article](https://arxiv.org/pdf/1904.06217.pdf) (plus its  [online appendix](https://umanlp.github.io/semantic-scaling/)) and the [original NLP paper](https://ub-madoc.bib.uni-mannheim.de/42002/1/E17-2109.pdf).

## How to use it

Clone or download the project, then go into the SemScale directory. The script scaler.py needs just the following inputs:

 __datadir__ -> A path to the directory containing the input text
                        files for scaling (one score will be assigned per
                        file).
                        
 __embs__ -> A path to the file containing pre-trained word
                        embeddings
                        
 __output__ -> A file path to which to store the scaling results.
 

optional arguments:

  -h, --help -> show this help message and exit
  
  --stopwords STOPWORDS -> A file to the path containing stopwords
  
  --emb_cutoff EMB_CUTOFF -> A cutoff on the vocabulary size of the embeddings.

### Data directory

The expected input is in the one-text-per-file format. Each text file in the referenced directory should contain a language (e.g., "en") in the first line, i.e., the format should be "*language*\n*text of the file*". 

### (Multilingual) Word Embeddings

For an easy set-up, we provide pre-trained FastText embeddings in a single file for the following five language: English, French, German, Italian and Spanish, that can be obtained from [here](http://publications.wim.uni-mannheim.de/informatik/lski/semscale/embs/wiki.big-five.mapped.vec.bz2).

Nonetheless, you can easily use the tool for texts in other languages or with different word embeddings, as long as you:

1) provide a (language-prefixed) word embedding file, the following way: for each word, abbreviation for the language plus double underscore plus word and then the word embedding. For instance, each word in a Bulgarian word embeddings file might be prefixed with "bg__")

2) in case you employ embeddings in a different language to the 5 listed above, update the list of supported languages in the beginning of the code file *nlp.py* and at the beginning of the task script you're using (e.g., *scaler.py*)

### Output File

A simple .txt, which will be filled with filename, positional-score for each input file.

### (Optional) Stopwords

Stopwords can be automatically excluded, via this input file (one stop-word per line).

### Prerequisites

The script requires basic libraries from the Python scientific stack: *numpy* (tested with version 1.12.1), *scipy* (tested with version 0.19.0), and *nltk* (tested with version 3.2.3); 

## Run it!

In the SemScale folder, just run the following command:

``
python scaler.py path-to-input-folder path-to-embeddings-file output.txt 
``

## Other functionalities

To use the supervised scaling version of our approach (dubbed __SemScores__), just run:

``
python supervised-scaler.py
``

and add as final arguments the two pivot texts to be used.

We also offer a Python implementation of the famous Wordfish algorithm for text scaling. To know how to use it, just run: 

``
python wordfish.py -h
``

Additional functionalities (classification, topical-scaling) are available in the [main branch](https://github.com/codogogo/topfish) of this project. 

## License

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.

## Referencing

If you're using this tool, please cite the following paper: 

```
@InProceedings{glavavs-nanni-ponzetto:2017:EACLshort,
  author    = {Glava\v{s}, Goran  and  Nanni, Federico  and  Ponzetto, Simone Paolo},
  title     = {Unsupervised Cross-Lingual Scaling of Political Texts},
  booktitle = {Proceedings of the 15th Conference of the European Chapter of the Association for Computational Linguistics: Volume 2, Short Papers},
  month     = {April},
  year      = {2017},
  address   = {Valencia, Spain},
  publisher = {Association for Computational Linguistics},
  pages     = {688--693},
  url       = {http://www.aclweb.org/anthology/E17-2109}
}
```
