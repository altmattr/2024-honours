# Machine Learning Frameworks & Terms

# Image Segmentation Vs Object Detection
Image segmentation is a technique used in computer vision that divides a digital image into separate segments or groups of pixels. This process is essential for tasks such as object detection because it simplifies the complex visual information in an image into more manageable sections. By organising the image's data into distinct segments, image segmentation facilitates quicker and more sophisticated image processing techniques.

Object detection is a task in computer vision that focuses on identifying and locating objects within digital images. This task falls under the umbrella of artificial intelligence, where the goal is to train computers to mimic human vision by recognising and categorising objects into different semantic groups. Object localisation is a related method used to pinpoint the exact position of specific objects in an image, typically by marking them with a bounding box.

Overall, image segementation is much more precise,as it gives a granular level of detail of the objects being detected.
![Screenshot 2024-03-17 at 5 28 34 pm](https://github.com/altmattr/2024-honours/assets/91449994/2225ab20-bd91-41bf-ae3f-401cd9b2d4bb)

# Framework Options

## TensorFlow
TensorFlow is an open-source library designed for numerical computation, extensive machine learning, deep learning, and various statistical and predictive analytics tasks. This technology streamlines the development process for machine learning models, aiding in data acquisition, scaling prediction services, and improving outcomes over time. Essentially, TensorFlow enables the training and operation of deep neural networks for applications such as classifying handwritten digits, recognising images, generating word embeddings, and processing natural language (NLP). Its software libraries can be integrated into any application to facilitate learning these capabilities.

TensorFlow applications are compatible with standard CPUs as well as the more powerful GPUs. Developed by Google, TensorFlow also supports the company’s specialised tensor processing units (TPUs), engineered to enhance TensorFlow tasks' efficiency.

Regarding its programming language, TensorFlow utilises Python for its front-end API, allowing developers to build applications within the framework. However, it also offers wrappers in several other languages, including C++ and Java. This versatility means that you can train and deploy your machine learning models rapidly, irrespective of the programming language or platform you prefer.

### TensorFlow Lite
TensorFlow Lite is an open-source deep learning framework specifically created for on-device inference, also known as Edge Computing. It offers a toolkit that facilitates machine learning directly on devices by empowering developers to deploy their trained models on various platforms, including mobile phones, embedded systems, IoT devices, and computers. TensorFlow Lite is compatible with multiple operating systems, such as embedded Linux, Android, iOS, and microcontroller units (MCUs). 

Effectively, it is to be used on edge devices on already trained models from the normal tensorflow. Due to the reduced processing costs, it is perfect for these scenarios.

## PyTorch
PyTorch is a highly optimised tensor library for deep learning, developed with a focus on Python and Torch, and is primarily aimed at applications that utilise GPUs and CPUs. PyTorch can be preferred for its dynamic computation graphs and Python-centric approach, offering a more intuitive and flexible programming environment. This feature is particularly beneficial for researchers, developers, and neural network debuggers, as it allows for the execution and evaluation of code segments in real-time, without the need to run the entire script to test specific parts. The platform's standout features include robust support for tensor computation, akin to NumPy, but with strong GPU acceleration, and an automatic differentiation system that is crucial for the efficient design and training of deep neural networks.

## Apache MXNet
Apache MXNet is an open-source deep learning framework that provides a comprehensive and flexible API for developing deep learning models. It distinguishes itself through several notable features. Primarily, it is fast and scalable, offering robust support for multiple GPUs and distributed computing across various hosts. MXNet appeals to a wide array of developers by supporting a multitude of programming languages, including Python, Scala, R, Java, C++, Julia, Matlab, JavaScript, and Go. It benefits from strong backing by the Apache Software Foundation and significant cloud services such as Amazon Web Services (AWS) and Microsoft Azure. Furthermore, MXNet is highly portable, efficiently functioning on a diverse range of hardware configurations and platforms, including low-end devices, Internet of Things (IoT) devices, serverless computing environments, and containers.


# Glossary
* Tensors: Multidimensional arrays used to represent data in machine learning models.
* Word Embeddings: Techniques to convert text into numerical vectors, capturing semantic meaning.
* Processing Natural Language: Techniques for understanding and manipulating human language using computers.
* Automatic Differentiation: A method to automatically compute gradients of output with respect to inputs, crucial for training machine learning models.
* Dynamic Computation Graphs: Graphs that allow for changing operations and structure during runtime, useful for adaptable machine learning models.
* Deep Learning: A subset of machine learning involving neural networks with many layers, enabling complex pattern recognition.
* Neural Networks: Computational models inspired by the human brain, used to recognize patterns and make predictions.

# References
* https://www.ibm.com/topics/object-detection?mhsrc=ibmsearch_a&mhq=object%20detection
* https://medium.com/analytics-vidhya/image-classification-vs-object-detection-vs-image-segmentation-f36db85fe81
* https://www.ibm.com/topics/image-segmentation
* https://www.databricks.com/glossary/tensorflow-guide
* https://www.simplilearn.com/what-is-pytorch-article
* https://viso.ai/edge-ai/tensorflow-lite/#:~:text=TensorFlow%20Lite%20(TFLite)%20is%20a,use%20and%20later%20open%2Dsourced.
* https://mxnet.apache.org/versions/master/api/python/docs/tutorials/getting-started/crash-course/0-introduction.html
