# 目录

--------

## 说明

这是一个存放各种学习资料的分区。

--------

## 书单

编号|名称|类别|内容
---|:---:|---:|---:
001|Long Short-Term Memory in Recurrent Neural Networks|book|LSTM
002|Neural Machine Translation by Jointly Learning to Align and Translate|paper|MT-LSTM
003|A Hierarchical Neural Auto-Encoder for Paragraphs and Documents|paper|AE-LSTM
004|A Critical Review of Recurrent Neural Networks for Sequence Learning|paper|SEQ2SEQ-LSTM
005|Supervised Sequence Labelling with Recurrent Neural Networks|paper|SEQ2SEQ-LSTM
006|Sequence to Sequence Learning with Neural Networks|paper|SEQ2SEQ
007|Factorization Machines|paper|FM
008|Field-aware Factorization Machines for CTR Prediction|paper|FFM
009|Convolutional Neural Networks for Sentence Classification|CNN-NLP
010|Deep Convolutional Neural Networks for Sentiment Analysis of Short Texts|CNN-NLP-SENTIMENT ANALYSIS
011|A Convolutional Neural Networks for Modelling Sentence|CNN-NLP
012|Effective Use of Word Order for Text Categorization with Convolutional Neural Networks|CNN-NLP-TEXT CATEGORIZATION
013|Semantic Clustering and Convolutional Neural Network for Short Text Categorization|CNN-NLP-SHORT-TEXT CATEGORIZATION
014|Semi-supervised Convolutional Neural Networks for Text Categorization via Region Eembedding|CNN-NLP-TEXT CATEGORIZATION
015|Relation Extration: Perspective from Convolutional Neural Networks|CNN-NLP
016|A Sensitivity Analysis of (and Practitioners' Guide to) Convolutional Neural Networks for Sentence Classification|CNN-NLP
017|Modeling Mention, Context and Entity with Neural Networks for Entity Disambiguation|
018|Relation Classification via Convolutional Deep Neural Network|CNN-RELATION
019|Modeling Interestingness with Deep Neural Networks|
020|A Latent Semantic Model with Convolutional-Pooling Structure for Information Retrieval|
021|Learning Character-level Representations for Part-of-Speech Tagging|CNN-NLP-BASED-CHARACTER
022|Character-level Convolutional Networks for Text Classification|CNN-NLP-BASED-CHARACTER
023|Text Understanding from Scratch|
024|Character-Aware Neural Language Models|
025|#Tag Space: Semantic Embedding from Hashtags|

---------------

## 部分文章总结
- 参见CNN在NLP上的应用：http://www.wildml.com/2015/11/understanding-convolutional-neural-networks-for-nlp/
- [12] Trains a CNN from scratch, without the need for pre-trained word vectors like word2vec or GloVe. It applies convolutions directly to one-hot vectors. The author also proposes a space-efficient bag-of-words like representation for the inpur data, reducing the number of parameters the network need to learn.
- In [14] the author extends the model with an additional unsupervised 'region embedding' that is learned using a CNN predicting the context of text regions. 
- The approach in these papers seems to work well for long-form texts (like movie reviews),  but their performance on short texts (like tweets) isn’t clear. Intuitively, it makes sense that using pre-trained word embeddings for short texts would yield larger gains than usingthem for long texts. 
- Building a CNN architecture means that there are many hyperparameters to choose from, some of which I presented above: Input represenations (word2vec, GloVe, one-hot), number and sizes of convolution filters, pooling strategies (max, average), and activation functions (ReLU, tanh).
- [16] performs an empirical evaluation on the effect of varying hyperparameters in CNN architectures, investigating their impact on performance and variance over multiple runs. 
- If you are looking to implement your own CNN for text classification, using the results of this paper as a starting point would be an excellent idea. A few results that stand out are that max-pooling always beat average pooling, that the ideal filter sizes are important but task-dependent, and that regularization doesn’t seem to make a big different in the NLP tasks that were considered. A caveat of this research is that all the datasets were quite similar in terms of their document length, so the same guidelines may not apply to data that looks considerably different.
- [15] explores CNNs for  Relation Extraction and Relation Classification tasks. In addition to the word vectors, the authors use the relative positions of words to the entities of interest as an input to the convolutional layer. This models assumes that the positions of the entities are given, and that each example input contains one relation. [17] and [18] have explored similar models.
- Another interesting use case of CNNs in NLP can be found in [19] and [20], coming out of Microsoft Research. These papers describe how to learn semantically meaningful representations of sentences that can be used for Information Retrieval. The example given in the papers includes recommending potentially interesting documents to users based on what they are currently reading. The sentence representations are trained based on search engine log data.
- Most CNN architectures learn embeddings (low-dimensional representations) for words and sentences in one way or another as part of their training procedure. Not all papers though focus on this aspect of training or investigate how meaningful the learned embeddings are.
- [25] presents a CNN architecture to predict hashtags for Facebook posts, while at the same time generating meaningful embeddings for words and sentences. These learned embeddings are then successfully applied to another task – recommending potentially interesting documents to users, trained based on clickstream data.
- So far, all of the models presented were based on words. But there has also been research in applying CNNs directly to characters. 
- [21] learns character-level embeddings, joins them with pre-trained word embeddings, and uses a CNN for Part of Speech tagging. 
- [22][23] explores the use of CNNs to learn directly from characters, without the need for any pre-trained embeddings. Notably, the authors use a relatively deep network with a total of 9 layers, and apply it to Sentiment Analysis and Text Categorization tasks. Results show that learning directly from character-level input works very well on large datasets (millions of examples), but underperforms simpler models on smaller datasets (hundreds of thousands of examples). 
- [24] explores to application of character-level convolutions to Language Modeling, using the output of the character-level CNN as the input to an LSTM at each time step. The same model is applied to various languages.