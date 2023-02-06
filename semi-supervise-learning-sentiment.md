## Semi-supervised learning with sentiment analysis

Problem: 5% data has label as different sentiment based on twitter's tweets. 5 classes in the lable.

### Approach 1
* Labeling Functions
  * rule-based LFs
  * Keywork-based LFs
  * Contextual LFs
  * Expert-based LFs
  * Hybrid LFs
  * Generative LFs   
* Transformer model for sentiment analysis:
    * labeling functions:
      * transformer models: twitter-roberta-base-sentiment
      * twitter-xlm-roberta-base-sentiment
      * between-base-sentiment-analysis  
  * output from LFs above -> GRU -> labels
* Lexicon-based Approach
    * Popular lexicon techniques:
      * TextBolb
      * AFINN
      * SentiWordNet
      * VADER
      * SO-CAL 
    * How it works
      * A predetermined and maintained valence dictionary of words annotated with their semantic orientation
        * Polarity: positive or negative
        * intensity: scale from -x to +x 
      * Calculation of pollarity score that aggregated the sentiment values of all positive/negative words within the text
      * Set thresholds for classification  
* Classification Function
  * Word embedding + LSTM Layers + Dense Layers
  * fine tune: fine-tuned with randomized search, covering the majorities hyper-parameters. additional optimization configs, especially callbacks are also tuned
  * ensemble and more: LSTM/BERT/GRU/ALL LF Scores/Text Length 

### Approach 2
* Snorkel: provides a package that can programmatically label unlableled dataset with customized labelling functions based on human expertise or pre-trained existing models. Also provide decorate functions to create preprocessors to enrich dataset.
* 
