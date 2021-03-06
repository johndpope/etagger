- etc
```
**learning rate annealing**
"we also
use early stopping to prevent over-fitting and use
the following process to determine when to stop
training. We first train with a constant learning
rate α = 0.001 on the training data and monitor
the development set performance at each epoch.
Then, at the epoch with the highest development
performance, we start a simple learning rate annealing
schedule: decrease α an order of magnitude
(i.e., divide by ten), train for five epochs, decrease
α an order of magnitude again, train for five
more epochs and stop." (https://arxiv.org/pdf/1705.00108.pdf)
-> how to determine the highest developement performance?

```

- experiments 6
```

* test 2
word embedding size : 100 -> 300 (Glove840B)
wrd_keep_prob : 0.5
chracter embedding size : 30 -> 100
chracter embedding random init : -1.0 ~ 1.0
filter_sizes : [3]
num_filters : 30 -> 50
chr_keep_prob : 0.5
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
pos_keep_prob : 0.5
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
rnn_size : 200 -> 100
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
rnn_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token)
+
CRF


* test 1
word embedding size : 100 -> 300 (Glove840B)
wrd_keep_prob : 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
filter_sizes : [3]
num_filters : 30
chr_keep_prob : 0.5
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
pos_keep_prob : 0.5
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
rnn_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token)
+
CRF

```

- experiments 5
```
* test 8
word embedding size : 100
wrd_keep_prob : 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
filter_sizes : [3]
num_filters : 30
chr_keep_prob : 0.5
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
pos_keep_prob : 0.5
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
rnn_size : 200
num_layers : 2 -> 1
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
rnn_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token)
+
CRF


* test 7
word embedding size : 100
wrd_keep_prob : 0.5 -> new (loss decreases more smoothly)
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
filter_sizes : [3]
num_filters : 30
chr_keep_prob : 0.5
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
pos_keep_prob : 0.5
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
rnn_size : 200
num_layers : 2 -> use multiple bidirectional_dynamic_rnn() -> 2 times slower than tf.contrib.rnn.MultiRNNCell() with tf.contrib.rnn.static_bidirectional_rnn()
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
rnn_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token)
+
CRF

token : 0.91112196313 -> best
chunk : 0.90743845407 -> best


* test 6
word embedding size : 100 -> 200
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 (fixed)
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token)
+
CRF

token : 0.900907530047
chunk : 0.891468060600

* test 5
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 20
+
save model by f1(token)
+
CRF

token : 0.905106800884
chunk : 0.898973814578

* test 4
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(chunk)
+
CRF

token : 0.908800785565
chunk : 0.900097164561

* test 3
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token), bug fix for token_eval.compute_f1()
+
CRF

token : 0.909514467876
chunk : 0.901569941788

* test 2
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token), bug fix for token_eval.compute_f1()
+
CRF(loss only)

token : 0.904864135435
chunk : 0.889849955869

* test 1
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(chunk)

token : 0.906159975483
chunk : 0.890888242039

```

- experiments 4
```
* test 10
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 128 -> 20
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()
+
save model by f1(token), mis-setting for out of class id in token_eval.compute_f1()

token : 0.906612635845
chunk : 0.895862800565 -> this is a coincidence by the mis-setting

* test 9
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9  -> 9 (disjoint upperInitial and mixedCaps), fixed after this setting
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 128 -> 64
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.901891180611
chunk : 0.886795774647

* test 8
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.903553921569
chunk : 0.886343612334

* test 7
word embedding size : 100
#pos embedding
#pos embedding size : 5
#pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
#pos_keep_prob : 0.5
epoch : 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.900515210991
chunk : 0.884615384615

* test 6
word embedding size : 100
#pos embedding
#pos embedding size : 5
#pos embedding random init : -0.5 ~ 0.5
#chracter embedding size : 30
#chracter embedding random init : -1.0 ~ 1.0
pos one-hot : 5
#chunk one-hot : 5
shape vec : 9
#filter_size : 3
#num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
#cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
#pos_keep_prob : 0.5
epoch : 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.895365211535
chunk : 0.8775977456851004

* test 5
word embedding size : 100
#pos embedding
#pos embedding size : 5
#pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
#pos one-hot : 5
#chunk one-hot : 5
shape vec : 5 -> 9
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
#pos_keep_prob : 0.5
epoch : 70 -> 80
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.901030169242
chunk : 0.8844185636139051

* test 4
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 8
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.902409196527
chunk : 0.885191054763

* test 3
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 8
mh_num_units : 64
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.899779735683
chunk : 0.884354938000

* test 2
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 30
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 30
rnn_size : 200
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.901651376147
chunk : 0.886935115174

* test 1
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96 -> 30
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 32 -> 30
rnn_size : 256 -> 200
num_layers : 2 -> 1
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.7 -> 0.5
rnn_keep_prob : 0.32 -> 0.5
pos_keep_prob : 0.5
epoch : 50 -> 70
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.901541674344
chunk : 0.884938533651

```

- experiments 3
```
* test 13
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.7
rnn_keep_prob : 0.32
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.900360878341
chunk : 0.886441723196

* test 12
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.7
rnn_keep_prob : 0.32
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5
normalize() instead of layer_norm()

token : 0.898353833915
chunk : 0.8851071334097523

* test 11
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 32
rnn_size : 500
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.7
rnn_keep_prob : 0.32
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5
without layer norm

token : 0.889773423148
chunk : 0.877369302653619

* test 10
word embedding size : 100
pos embedding
shape vec
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5

token : 0.895744811873
chunk : 0.8798867857774633

* test 9
word embedding size : 100
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 32
rnn_size : 500
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.7
rnn_keep_prob : 0.32
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5

token : 0.897407543924
chunk : 0.8832155477031802

* test 8
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3
num_filters : 32
rnn_size : 500
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.7
rnn_keep_prob : 0.32
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5

token : 0.896001962227
chunk : 0.8801692972401023

* test 7
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 4
mh_num_units : 32
mh_dropout : 0.5

0.895288278904

* test 6
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5

0.896419516418

* test 5
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 20
cnn_keep_prob : 0.5
rnn_keep_prob : 0.8
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.5

0.897379106681

* test 4
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.0001, intermid_epoch = 10
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 1
mh_num_units : 32
mh_dropout : 0.5

0.893447642376

* test 3
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.0001 -> 0.0002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention(softmax with masking)
mh_num_heads : 2
mh_num_units : 32
mh_dropout : 0.2

0.881420496436

* test 2
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention
mh_num_heads : 2
mh_linear_key_dim : 32
mh_linear_val_dim : 32
mh_dropout : 0.5

0.896346749226

* test 1
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
pos_keep_prob : 0.5
epoch : 50
batch_size : 128
+
multi head attention
mh_num_heads : 1
mh_linear_key_dim : 32
mh_linear_val_dim : 32
mh_dropout : 0.5

0.894368789106

```

- experiments 2
```
* test 17
word embedding size : 300
pos embedding
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.890206249228

* test 17
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
shape vec
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.893637926799

* test 16
word embedding size : 300
pos embedding
pos embedding size : 5
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.891214677092

* test 15
word embedding size : 300
remove pos embedding
pos embedding size : 10
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.887810272794

* test 14
word embedding size : 300
remove pos embedding
pos embedding size : 50
pos embedding random init : -0.5 ~ 0.5
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.886979997546

* test 13
word embedding size : 300
word embedding trainable : True
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.859092036715


* test 12
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_epoch = 15
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.895851286471

* test 11
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128
+
longest matching gazetteer feature(ignore length less than 10)

0.876311566473

* test 10
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001 -> 0.002 (change), intermid_step = 1000
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128
+
longest matching gazetteer feature(ignore length less than 10)

0.888393410133

* test 9
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.0001 -> 0.001 (change), intermid_step = 1000
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.886325787948

* test 8
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128
+
longest matching gazetteer feature(without MISC)

0.866472158421

* test 7
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.892918613228

* test 6
replace all digit to '0'
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128
+
longest matching gazetteer feature(from test data)

0.913716137712

=> ok. this result supports that gazetteer features are very helpful. but, 
if we construct gazetteer vocab from the training data, the f-score decreases.

* test 5
replace all digit to '0'
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128
+
longest matching gazetteer feature

0.870375031462

* test 4
replace all digit to '0'
word embedding size : 300
chracter embedding size : 96
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 128

0.890053001356

* test 3
replace all digit to '0'
random shuffling
word embedding size : 300
chracter embedding size : 53
chracter embedding random init : -1.0 ~ 1.0
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.5
rnn_keep_prob : 0.5
epoch : 50
batch_size : 64
+
longest matching gazetteer feature

0.87932312253

* test 2
replace all digit to '0'
random shuffling
word embedding size : 50
chracter embedding size : 64
chracter embedding random init : -0.5 ~ 0.5
filter_size : 3,4,5
num_filters : 32
rnn_size : 256
num_layers : 2
learning_rate : 0.001
cnn_keep_prob : 0.32
rnn_keep_prob : 0.32
epoch : 50
batch_size : 64

0.881000551775

* test 1
replace all digit to '0'
random shuffling
word embedding size : 50
chracter embedding size : 64
chracter embedding random init : -0.5 ~ 0.5
filter_size : 3
num_filters : 48
rnn_size : 256
num_layers : 1
learning_rate : 0.001
cnn_keep_prob : 0.32
rnn_keep_prob : 0.32
epoch : 64
batch_size : 64

0.884797152151

```

- experiments 1
```
* weak entity types : B-ORG, I-ORG, B-MISC, I-MISC

* chr_embedding : max

rnn_size : 256, keep_prob : 0.5, chr_embedding : max
0.892409321671

* chr embedding : conv

rnn_size : 256, keep_prob : 0.5, chr_embedding : conv
0.895172667607
0.893800406329
0.892967114177
0.893781430148

rnn_size : 256, cnn_keep_prob : 0.7, rnn_keep_prob : 0.8, chr_embedding : conv
0.892371739929

rnn_size : 256, cnn_keep_prob : 0.6, rnn_keep_prob : 0.6, chr_embedding : conv
0.893224198412

* gazetteer feature

rnn_size : 256, keep_prob : 0.5, chr_embedding : conv, gazetteer : token-based m-hot vector
0.855807086614

rnn_size : 512, keep_prob : 0.5, chr_embedding : conv, gazetteer : token-based m-hot vector
0.873537604457

rnn_size : 256, keep_prob : 0.5, chr_embedding : conv, gazetteer : token-based 0|1
0.877048661647

even though we use '0|1' indicating gazetteer, it is worse than basic models.
the loss is even increasing along steps. why?

try to adjust keep_probs.
rnn_size : 256, cnn_keep_prob : 0.8, rnn_keep_prob : 0.8, chr_embedding : conv, gazetteer : token-based 0|1
0.879918632001

try to filter digit/ascii symbol/short word from gazetteer vocab.
rnn_size : 256, cnn_keep_prob : 0.8, rnn_keep_prob : 0.8, chr_embedding : conv, gazetteer : token-based 0|1
0.877144298688

use m-hot vector and apply unambiguous gazetteer only
rnn_size : 256, cnn_keep_prob : 0.8, rnn_keep_prob : 0.8, chr_embedding : conv, gazetteer : token-based m-hot vector
0.883349826818

including unambiguous 'O' gazetteer
rnn_size : 256, cnn_keep_prob : 0.8, rnn_keep_prob : 0.8, chr_embedding : conv, gazetteer : token-based m-hot vector
0.878849345381
```
