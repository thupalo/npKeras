# npKeras mini framework
Keras model inference in pure numpy

# Train Keras CNN, export the trained model weights and run inference in pure Numpy

npKeras uses standard Sequential model syntax definition and provides set of layer types.

Layers:
* Conv2D
* Dense
* MaxPooling2D
* Flatten
* ReLU
* softmax
* and special SparseCategory layer (onehot to category label)
* ... [easy expandable] 

Model supports standard function:
* add 
* predict
* evaluate
* set_weights
* load_weights
* summary

Beside Sequential() Keras model implemetation the separate layers may be executed separately using layer.forward() function as the building blocks of more complicated models like U-net.

The inference can be splited into batches for managable memory consumption, and also could run in paralel using multprocessing - some platform restrictions may apply. Runtime statistics is available in verbose mode.

To optimize execution npKeras use NCHW data format which may differ from Keras NHWC. 
Input data could be easily converted if necessary:  np.reshape(X, (-1, 1, 28, 28))

A dedicated function for exporting trained Keras model weights is provided for transport into npKeras in pickle format. During import the layers are identified by names between Keras and npKeras, and should have identical input shape and output shape.
