
Time to try experiments in Neural Network, Deep Learning and any other AI methods :)
Neural Network is a universal approximator, which means you can use it to implment other machine learning algorithms


*****************************************************************

RESOURCES

* Database
  * ImageNet: http://www.image-net.org
    * Here, you can download images in different format
* Standford CNN for visual Recognition lectures: http://cs231n.stanford.edu/syllabus.html
  * I think, once you started to learn deep learning, you will really feel it's so deep to learn....
  * My notes: https://github.com/hanhanwu/Hanhan_Data_Science_Resources2/blob/master/Standford_CNN_Notes1.pdf

* Here is a bunch of libraries, tutorials you can try: https://www.analyticsvidhya.com/blog/2016/08/deep-learning-path/

* 10 Deep Learning Architectures: https://www.analyticsvidhya.com/blog/2017/08/10-advanced-deep-learning-architectures-data-scientists/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29

* Fundamentals of neural network: https://www.analyticsvidhya.com/blog/2016/03/introduction-deep-learning-fundamentals-neural-networks/
  * It's such a great feeling to review and to understand deeper
  * After learning NN a while, are you going to forget about the relationship between weights, activation function and EACH neuron like I did? This article is a great source to review. So! Each neuron has an activation function, the input for this single neuron can come from multiple sources, each input and bias could has weight.
  * I think, the activation function can be whatever you defined. The purpose for defining an activation is to guarantee it will give the output you want. For example, the input is x1, x2 and the output should be `x1 AND x2`, so your activation function should use mathematical method to guarantee the output will be `x1 AND x2` when the input is x1, x2.
  * The power of multiple layers of NN - you can break a complex problem into small problems, and each NN layer deals with one of the small problem, finally, you get what you finally want
  * The number of neurons in the output layer will depend on the type of problem. It can be 1 for regression or binary classification problem or multiple for multi-class classification problems.
  * <b>The ultimate objective is to update the weights of the model in order to minimize the loss function</b>. The weights are updated using a back-propogation algorithm.
  * `A XNOR B = (A' AND B') OR (A AND B) = NOT ((A OR B) AND (A' OR B'))`, `A' = NOT A`
  * Each optimization includes:
    * Select a network architecture, i.e. number of hidden layers,  number of neurons in each layer and activation function
    * Initialize weights randomly
    * Use forward propagation to determine the output node
    * Find the error of the model using the known labels
    * <b>Back-propogate the error</b> into the network and determine the error for each node
    * Update the weights to minimize the loss function
  * During back-propagation:
    * <b>The error at a node is based on weighted sum of errors on all the nodes of the next layer which take output of this node as input.</b>
  * Important params for optimizing neural network
    * Type of architecture
    * Number of Layers
    * Number of Neurons in a layer
    * Regularization parameters
    * Learning Rate
    * Type of optimization / backpropagation technique to use
    * Dropout rate
    * Weight sharing
  * Think about the activation function, the architecture, do you think Deep Learning can really generate infinite number of solutions?! So powerful isn't it? The only problem is, you still have to have ground truth first, and for Deep Learning, the ground truth has to be more accurate and informative
    
* Core concepts of neural network: https://www.analyticsvidhya.com/blog/2016/08/evolution-core-concepts-deep-learning-neural-networks/
  * The meaning of "sample", "epoch", "batch": https://keras.io/getting-started/faq/#what-does-sample-batch-epoch-mean
    * <b>Sample</b>: One element of a dataset. Such as, 1 image, 1 audio file
    * <b>Batch</b>: A set of N samples. The samples in a batch are processed independently, in parallel. If training, a batch results in only one update to the model. A batch generally approximates the distribution of the input data better than a single input. <b>The larger the batch, the better the approximation</b>, but also takes longer time.
    * <b>Epoch</b>: Epoch: an arbitrary cutoff, generally defined as "one pass over the entire dataset", used to separate training into <b>distinct phases</b>, which is useful for <b>logging and periodic evaluation</b>. When using Keras `evaluation_data` or `evaluation_split` with the `fit` method of Keras models, <b>evaluation will be run at the end of every epoch</b>.
    
* Deep Leaning for Computer Vision: https://www.analyticsvidhya.com/blog/2016/04/deep-learning-computer-vision-introduction-convolution-neural-networks/?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3BxPn6EhynRquw3Evzrg79RA%3D%3D
  * Detailed analysis of activation functions
    * Sigmoid (not recommended for CNN)
      * Kill the gradient
      * Outputs are not zero-centered since it's between [0,1]
      * Taking the exp() is computationally expensive
    * Tanh (not recommended for CNN)
      * Still kill the gradient
      * But output can be zero-centered
    * ReLU (Rectified Linear Unit)
      * <b>most commonly used for CNN</b>
      * Gradient won’t saturate in the positive region
      * Computationally very efficient as simple thresholding is required
      * Empirically found to converge faster than sigmoid or tanh.
      * Drawbacks - Output is not zero-centered and always positive
      * Drawbacks - Gradient is killed for x<0. Few techniques like <b>leaky ReLU</b> and <b>parametric ReLU</b> are used to overcome this
      * Drawbacks - Gradient is not defined at x=0. But this can be easily catered using <b>sub-gradients</b> and posts less practical challenges as x=0 is generally a rare case
    * Data Preprocessing
      * Same image size
      * Mean centering: subtract mean value from each pixel
    * Weights Initialization
      * All zeros - a bad idea
      * Gaussian Random Variables: you need to play with the standard deviation of the gaussian distribution which works well for your network....
      * Xavier Initialization: It suggests that variance of the gaussian distribution of weights for each neuron should depend on the number of inputs to the layer. A recent research suggested that for ReLU neurons, the recommended update is, `np.random.randn(n_in, n_out)*sqrt(2/n_in)`
      * You might be surprised to know that 10-20% of the ReLUs might be dead at a particular time while training and even in the end.
    * CNN
      * The <b>first layer</b> will try to detect edges and form templates for <b>edge detection</b>
      * The subsequent layers will try to combine them into <b>simpler shapes</b> and eventually into <b>templates of different object positions, illumination, scales, etc</b>
      * The final layers will <b>match an input image with all the templates</b> and the <b>final prediction</b> is like a weighted sum of all of them.
    * CNN important layers
      * Convolution Layer
      * ReLU layer
      * Pooling Layer: Using padding in convolution layer, the image size remains same. So, pooling layers are used to reduce the size of image.
      * Fully Connected Layer: Each pixel is considered as a separate neuron just like a regular neural network. The last fully-connected layer will contain as many neurons as the number of classes to be predicted
    * In this article, I think the correct formula for calculating output size should be: `(W-F+2P)/S + 1`
    * To calculate zero-padding size: `(F-1)/2`
    * Filters might be called kernels sometimes
    * Alexnet
    ![AlexNet](https://www.analyticsvidhya.com/wp-content/uploads/2016/03/fig-8.png)
    * It has code example using GraphLab with pre-trained model. Pre-trained model may increase the accuracy but difficult to find and if you use CPU, may take very long time to run
    

* Digits recognition with <b>TensorFlow</b> [lower level library]: https://www.analyticsvidhya.com/blog/2016/10/an-introduction-to-implementing-neural-networks-using-tensorflow/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
  * <b>Tensorflow Resources</b>: https://github.com/jtoy/awesome-tensorflow
  * Tensorflow Models: https://github.com/tensorflow/models
  * Google Object Detection API: https://github.com/tensorflow/models/tree/master/object_detection

* Digits recognition, using NN with <b>Keras</b> [higher level library]: https://www.analyticsvidhya.com/blog/2016/10/tutorial-optimizing-neural-networks-using-keras-with-image-recognition-case-study/
  * Keras has 3 backend you can use: https://keras.io/backend/
    * Tensorflow (from Google)
    * CNTK (from Microsoft)
    * Theano (from University of Montreal)
    * You can change between these backend
  * Install Keras: https://keras.io/#installation
  * <b>Keras Resources</b>: https://github.com/fchollet/keras-resources
  * <b>Keras Examples</b>: https://github.com/fchollet/keras/tree/master/examples
  * For installing TensorFlow, strongly recommend to use `virtualenv` (it's fast, simply and won't influence other installed python libraries): https://www.tensorflow.org/install/install_mac
  * After `virtualenv` installation and validaton, Commands to turn on and turn off virtual environment:
    * To activate the virtual environment, `$ source ~/Documents/Virtual_Env/bin/activate      # If using bash, sh, ksh, or zsh`, change "Documents/Virtual_Env" to your own virtual environment folder name
    * To activate the virtual environment, `$ source ~/Documents/Virtual_Env/bin/activate.csh  # If using csh or tcsh`, change "Documents/Virtual_Env" to your own virtual environment folder name
    * Then in your terminal, you will see `(Virtual_Env)$`
    * To deactivate your virtual envvironment, `(Virtual_Env)$ deactivate`
  * Install Jupyter Notebook in your virtual environment
    * `(Virtual_Env)$ pip install jupyter`, install jupyter within the active virtualenv
    * `(Virtual_Env)$ pip install ipykernel`, install reference ipykernel package
    * `(Virtual_Env)$ python -m ipykernel install --user --name testenv --display-name "Python2 (Virtual_Env)"`, set up the kernel. Here, if you will install multiple kernel, `testenv` name should be changed to other names
    * `(Virtual_Env)$ jupyter notebook`
    * After jupyter notebook has been turned on, when you are creating a new notebook, choose "Python 2 (Virtual_Env)"
    * NOTE: If you are using Python3, for example, python3.5, then in the above commands, change `pip` to `pip3`; change `python` to `python3.5`
  * Pros and Cons of Keras
    * Simple and no detailed implemention of NN like lower level libraries (e.g. Tensorflow) required, but also because of this, it can be less flexible
    * Only support GPU Nvidia
    
* CNN for visual recognition: http://cs231n.github.io/neural-networks-3/
    
* Image recognition with Keras: https://www.analyticsvidhya.com/blog/2017/06/architecture-of-convolutional-neural-networks-simplified-demystified/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
  * Stride & Padding
    * Same Padding (zero padding) - remain image size
    * Valid Padding - reduce features
  * Activation Map & Number of Filters
  * The convolution and pooling layers will only extract features and reduce the number of parameters from the  original images. Pooling is done for the sole purpose of reducing the spatial size of the image, but the depth of the image remains unchanged
  * Calculate output volume: `([W-F+2P]/S)+1`, W is the input volume size, F is the size of the filter, P is the number of padding applied and S is the number of strides.
  * Output layer loss function to compute the error in prediction, then backpropagation
  * <b>Entire CNN Network</b>
  
  ![entire network](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/06/28132045/cnnimage.png)
    * Activation Map on convolution layer extracts features. 
    * Padding on convolution layer reduces features. If you want to retain image size, add Same Padding, to add Valid Padding to reduce features too
    * Pooling is to further reduce features
    * When CNN goes further, the extracted features become more specific
    * Output layer makes prediction and has the loss function to check the prediction error
    * Backpropagation
    * Multiple rounds of forwardpropagation and backpropagation
    
    
* Use pre-trained model for digits recognition: https://www.analyticsvidhya.com/blog/2017/06/transfer-learning-the-art-of-fine-tuning-a-pre-trained-model/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29

* NN Implementation
  * Implement in Python and R: https://www.analyticsvidhya.com/blog/2017/05/neural-network-from-scratch-in-python-and-r/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
  * My NN code in python: https://github.com/hanhanwu/Hanhan-Machine-Learning-Model-Implementation/blob/master/neural_network.py
  * My NN code in real time short context search: https://github.com/hanhanwu/Hanhan_NLP/blob/master/short_context_search.py

* GPU for Deep Learning: https://www.analyticsvidhya.com/blog/2017/05/gpus-necessary-for-deep-learning/
  * Why GPU: https://www.slideshare.net/AlessioVillardita/ca-1st-presentation-final-published
  
* Deep Learning Book: http://www.deeplearningbook.org/
* Deep Learning Path: https://www.analyticsvidhya.com/blog/2016/08/deep-learning-path/
* Some Deep Learning tutorials: http://machinelearningmastery.com/start-here/

* Object Detection using YOLO [No Code Example]
  * Article: https://www.analyticsvidhya.com/blog/2017/08/finding-chairs-deep-learning-part-i/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
  * I really like the author's passion in deep learning!
  * Inspiration - what to check when something is wrong with the deep learning model
    * Step 1: Check the architecture
    * Step 2: Check the hyper-parameters of neural network
    * Step 3: Check the Complexity of network
    * Step 4: Check the Structure of Input data
    * Step 5: Check the Distribution of data
  * It cotains how to install YOLO for object detection, how to resize training images to improve accuracy


*****************************************************************

EXPERIMENTS

* Conda vs Non-Conda Environments
  * After you have installed so many python libraries, you may have already experienced 2 types of virtual environment and non-virtual environment. The installing mathods cannot apply to all of them, sometimes, 1 method just apply to 1 environment, but that's good enough if finally you can install all libraries in a certain environment and do your experiment. Let me write down my brief summary about using <b>non-virtual environment, python virtualenv and conda virtual environemnt</b>
  * Non-Virtual Environemnt - Your local Python site-packages
    * For new versions of Mac, better to use `sudo easy_install [package_name]`
    * But for some machines, pip also works. `pip install [package_name]` for Python 2.*
    * `pip3 install [package_name]` for python 3.*
  * Python `virtualenv` - It creates a virtual environment very fast
    * Insall virtualenv, `sudo easy_install virtualenv`, for more details, check https://www.tensorflow.org/install/install_mac
    * Also check the above commands I used for `virtualenv`
    * In this environment, you can just use `pip install [package_name]`, or `pip3 install [package_name]`
    * But! Sometimes there are libraries you just cannot intsall here. This maybe because the python package does not match the requirements for this specific library... Then, maybe get some help from Conda Virtual Environment
  * Conda Virtual Environemnt
    * For detailed commands, check my posts here: https://stackoverflow.com/questions/45707010/ipython-importerror-cannot-import-name-layout/45727917#45727917
    * Sometime! You can use `conda install [package_name]`. When this command does not work, try `pip install [package_name]` or `pip3 install [package_name]`. By changing between these 2 types of commands, finally, I got all the libraries I want in Conda Environemnt


* Digital Recognition with Keras
  * Adam Optimizer: https://arxiv.org/abs/1412.6980
  * Supported Optimizers in Keras: https://keras.io/optimizers/
  * Supported loss functions in Keras: https://keras.io/losses/
  * NN used in this practive
    * Multi-Layer Perceptrons (MLP)
    * Convolutional neural network (CNN)
    * In this experiment, CNN is slower, but got better validation results
  * Methods used in improving Multi-Layer Perceptrons (MLP)
    * Add hidden layers
    * Use dropout to avoid overfitting. Dropout is essentially randomly turning off parts of the model so that it does not “overlearn” a concept
    * Increase epochs
  * My code: https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/digital_recognition_Keras.ipynb
  * Reference: https://www.analyticsvidhya.com/blog/2016/10/tutorial-optimizing-neural-networks-using-keras-with-image-recognition-case-study/
    
    
* Digital Recognition with Tensorflow
  * “TensorFlow is an open source software library for numerical computation using dataflow graphs. Nodes in the graph represents mathematical operations, while graph edges represent multi-dimensional data arrays (aka tensors) communicated between them. The flexible architecture allows you to deploy computation to one or more CPUs or GPUs in a desktop, server, or mobile device with a single API.”
  * Tensorflow Workflow
    * Build a computational graph, this can be any mathematical operation TensorFlow supports.
    * Initialize variables
    * Create session
    * Run graph in session, the compiled graph is passed to the session, which starts its execution. 
    * Close session
  * Terminology in Tensorflow
    * <b>placeholder</b>: A way to feed data into the graphs
    * <b>feed_dict</b>: A dictionary to pass numeric values to computational graph
  * Process for building neural network
    * Define Neural Network architecture to be compiled
    * Transfer data to your model
    * Under the hood, the data is first divided into batches, so that it can be ingested. The batches are first preprocessed, augmented and then fed into Neural Network for training
    * The model then gets trained incrementally
    * Display the accuracy for a specific number of timesteps
    * After training save the model for future use
    * Test the model on a new data and check how it performs
  * Tensorflow Resources
    * Optimizers can be found here: https://www.tensorflow.org/api_docs/python/tf/train
  * Reference: https://www.analyticsvidhya.com/blog/2016/10/an-introduction-to-implementing-neural-networks-using-tensorflow/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
  * My code: https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/digital_recognition_TensorFlow.ipynb
  
  
* Image Recognition with Keras
  * <b>Better to use Conda virtual environment</b>
  * Commands to install required libraries in conda virtual environment
    * `conda install -c menpo opencv`
    * `pip install tensorflow`
    * `pip install keras`
  * Download images: https://github.com/hanhanwu/Basic_But_Useful/blob/master/python_download_images.ipynb
  * <b>Basic Version</b>
    * reference: https://www.analyticsvidhya.com/blog/2017/06/architecture-of-convolutional-neural-networks-simplified-demystified/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
    * My code: https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/Image_Recognition_Keras_simple_example.ipynb
    * rose images I'm using: http://www.image-net.org/api/text/imagenet.synset.geturls?wnid=n04971313
    * sunflower images I'm using: http://www.image-net.org/api/text/imagenet.synset.geturls?wnid=n11978713
  * <b>NOTE</b>: As you can see in my code above, I'm reading local image file instead of reading image urls directly. This is because, [when I tried to read image urls directly, no matter how did I change the code, there is dimension issue][1], using `scipy.misc.imread()` to read local file can get the right dimension of images, and it only supports local files 
    * This is the image data I got after reading from url directly 
    ![wrong dimwnsion](https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/wrong_dimensions.png)
    * This is the image data I got after reading from local file
    ![right dimwnsion](https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/right_dimensions.png)
  * <b>Level 2 Version</b>
    * My code: https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/image_recognition_Keras_level2.ipynb
    * In this code, I added more layers in CNN and did some random prediction
    * The most important thing is, I have learned much more about how to adjust the param values in CNN.... This is challenging for beginners, since there will be color and gray images, and the settings will be different. A wrong value could lead to long time debudding without really sure where is the problem. Let me write down a few summary here:
      * In [my digital recognition code][6], you will see `train_x_temp = train_x.reshape(-1, 28, 28, 1)`, this is because the image is gray, so the depth is 1 and the image size is 28*28*1, -1 here is to make it 4 dimensions as `model.fit()` requires. But in [image recognition level 2 code][7], you are seeing `training_image_temp = training_images.reshape(-1, 100, 100, 3)`, this is because the images are color images (RGB images), the depth should be 3, and size is 100*100*3
      * When you are using `pylab.imshow(testing_img)` to show images, whether you could show color image or 1-color image depends on this line of code `testing_img = scipy.misc.imread(testing_image_path)`, if you set `flatten=Ture` in `imread`, will be 1-color, otherwise can be RGB image
  
  
* GraphLab for Image Recognition
  * You need to register GraphLab email first (it's free): https://turi.com/download/academic.html
  * Right after the email registration, an install page will appear with your email and GraphLab key filled in pip command line: https://turi.com/download/install-graphlab-create-command-line.html
    * Type `sudo pip install --upgrade --no-cache-dir https://get.graphlab.com/GraphLab-Create/2.1/[your registered email address here]/[your product key here]/GraphLab-Create-License.tar.gz`, the email and product key here should be yours. <b>sudo</b> here is very important to me during the installation
  * The side effects of the command line is, it will uninstall something related to `shutil`, then when you want to run you ipython kernel, it will fail. by showing errors such as "No module named shutil_get_terminal_size". To solve this problem, run commands after the above command
    * `pip install --upgrade setuptools pip`
    * `pip uninstall ipython`
    * `pip install ipython`
    * `pip install ipykernel`, this maybe optional
    * `python -m ipykernel install --user --name testenv --display-name "Python2 (yourenvname)"`, here need to change `testenv` and `(yourenvname)`
    * `conda install ipywidgets --no-deps`
    * Then you can open ipython and `import graphlab`
  * [Get started with GrapgLab][2]
  * [GraphLab Create API][4]
  * [Image dataset - CIFAR-10][3]
  * My code: https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/try_GraphLab.ipynb
  * [reference][5]
    

*****************************************************************

RELAVANT PAPERS & NEWS

* Google Deep Learning Products
  * Google TensorFlow Object Detection API: https://research.googleblog.com/2017/06/supercharge-your-computer-vision-models.html
  * MobileNet: https://research.googleblog.com/2017/06/mobilenets-open-source-models-for.html
  * Street View & Captcha
    * https://research.googleblog.com/2017/05/updating-google-maps-with-deep-learning.html
    * https://security.googleblog.com/2014/04/street-view-and-recaptcha-technology.html

* Adam Optimizer: https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/Adam_optimizer.pdf
  * Don't quite understand, but I really admire those PhDs who design and compare algorithms...
  
* Practical Recommendations for Gradient-Based Training
  * https://github.com/hanhanwu/readings/blob/master/Practical%20Recommendations%20for%20Gradient-Based%20Training.pdf
  * Detailed suggestions in almost all the process in Gradient-Based training, very practical




[1]:https://stackoverflow.com/questions/45912124/python-keras-how-to-generate-right-image-dimension
[2]:https://www.analyticsvidhya.com/blog/2015/12/started-graphlab-python/
[3]:https://www.cs.toronto.edu/~kriz/cifar.html
[4]:https://turi.com/products/create/docs/index.html
[5]:https://www.analyticsvidhya.com/blog/2016/04/deep-learning-computer-vision-introduction-convolution-neural-networks/?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3BxPn6EhynRquw3Evzrg79RA%3D%3D
[6]:https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/digital_recognition_Keras.ipynb
[7]:https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/AI_Experiments/image_recognition_Keras_level2.ipynb