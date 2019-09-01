
## Minimal Is All You Need

Minimalist Transformers In [Keras](http://keras.io) that support sklearn's .fit .predict .


Have you ever wanted to work with transformers but just got drowned in ocean of models where none just did what you wanted?
Yeah.. Me Too..
Introducing "Minimal Is All You Need": Minimal Is All You Need is a Python library implementing nuts and bolts, for building Transformers models using [Keras](http://keras.io).

The library supports:
* Universal Transformer
* Bert
* ELMo
* GPT
* GPT-2
* XLNet
* positional encoding and embeddings,
* attention masking,
* memory-compressed attention,
* ACT (adaptive computation time),

```python
    from minimal_is_all_you_need import Bert, GPT_2, XLNet, ELMo, GPT,  Transformer
```

It allows you to just build them. *No games. No tricks. No bloat*.
for example:

```python
    model = Bert()
    model.compile('adam', loss=[the_loss_of_bert(0.1), 'binary_crossentropy'])
    model.fit(X, Y)
```

Train on 9414 samples, validate on 957 samples
Epoch 1/50
9414/9414 [==============================] - 76s 8ms/step - loss: 7.0847 
    


### Bert
```python
    model = Bert()
    model.compile('adam', loss=[the_loss_of_bert(0.1), 'binary_crossentropy'])
```
### Universal Transformer
```python
    model = Transformer()
    model.compile('adam', loss='sparse_categorical_crossentropy')
```
### GPT
```python
    model = GPT()
    model.compile('adam', loss='sparse_categorical_crossentropy')
```
### GPT-2
```python
    model = GPT_2()
    model.compile('adam', loss='sparse_categorical_crossentropy')
```
### ELMo
```python
    model = ELMo()
    model.compile('adagrad', loss='sparse_categorical_crossentropy')
```
### XLNet
```python
    model = XLNet()
    model.compile('adam', loss='sparse_categorical_crossentropy')
```

It also allows you to piece together a multi-step Transformer model
in a flexible way, for example:

```python
transformer_block = TransformerBlock( name='transformer', num_heads=8, residual_dropout=0.1, attention_dropout=0.1, use_masking=True)
add_coordinate_embedding = TransformerCoordinateEmbedding(transformer_depth, name='coordinate_embedding')
    
output = transformer_input # shape: (<batch size>, <sequence length>, <input size>)
for step in range(transformer_depth):
    output = transformer_block(add_coordinate_embedding(output, step=step))
```


All pieces of the model (like self-attention, activation function, layer normalization) are available as Keras layers, so, if necessary,
you can build your version of Transformer, by re-arranging them differently or replacing some of them.

The (Universal) Transformer is a deep learning architecture described in arguably one of the most impressive DL papers of 2017 and 2018:
the "[Attention is all you need][1]" and the "[Universal Transformers][2]"
by Google Research and Google Brain teams.

The authors brought the idea of recurrent multi-head self-attention,
which has inspired a big wave of new research models that keep coming ever since.
These models demonstrate new state-of-the-art results in various NLP tasks,
including translation, parsing, question answering, and even some algorithmic tasks.

Installation
------------
To install the library you need to clone the repository

    pip install minimal_is_all_you_need


[1]: https://arxiv.org/abs/1706.03762 "Attention Is All You Need"
[2]: https://arxiv.org/abs/1807.03819 "Universal Transformers"
[3]: https://arxiv.org/abs/1810.04805 "BERT: Pre-training of Deep Bidirectional Transformers for