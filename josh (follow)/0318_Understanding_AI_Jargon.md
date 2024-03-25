# Glossary

A

* AI (Artificial Intelligence): The simulation of human intelligence in machines programmed to think and learn.
* Algorithm: A set of rules or instructions given to an AI system to help it learn from data.
* ANN (Artificial Neural Network): Computing systems vaguely inspired by the biological neural networks that constitute animal brains.
  
B

* Big Data: Extremely large data sets that may be analyzed computationally to reveal patterns, trends, and associations.
* Bias: An error in the algorithm that leads to unfair outcomes, such as favouring one arbitrary group of users over others.

C

* Chatbot: A software application used to conduct an online chat conversation via text or text-to-speech.
* CNN (Convolutional Neural Network): A class of deep neural networks most commonly applied to analyzing visual imagery.
* Computational Learning Theory: A subfield of AI devoted to studying the design and analysis of machine learning algorithms.

D

* Deep Learning: A subset of machine learning in artificial intelligence with networks capable of learning unsupervised from unstructured or unlabeled data.
* Data Mining: Examining large databases to generate new information.
* Decision Tree: A decision support tool that uses a tree-like graph or model of decisions and their possible consequences.

E

* Expert System: AI that mimics the decision-making ability of a human expert.
* Ensemble Learning: Methods that combine the predictions of multiple machine learning models to produce a single prediction.

F

* Feature Extraction: The process of reducing the resources required to describe a large data set accurately.
* Fuzzy Logic: A form of many-valued logic that deals with approximate rather than fixed and exact reasoning.

G

* GAN (Generative Adversarial Network): A class of machine learning frameworks designed by two neural networks contesting each other in a game.

H

* Heuristic: A technique designed to solve a problem more quickly when classic methods are too slow or to find an approximate solution when classic methods fail to find an exact solution.

I

* IoT (Internet of Things) is a network of physical objects—devices, vehicles, appliances—that use sensors and APIs to connect and exchange data over the Internet.
* Image Recognition is the ability of AI to detect and identify objects or features in a digital image or video.

L

* LSTM (Long Short-Term Memory): A special kind of RNN capable of learning long-term dependencies.
* Learning Rate: The step size at each iteration while moving toward a minimum of a loss function.

M

* Machine Learning: A subset of AI that includes algorithms that parse data, learn from that data and then apply what they have learned to make informed decisions.
* MLP (Multilayer Perceptron): A class of feedforward artificial neural networks (ANN).

N

* NLP (Natural Language Processing) is the branch of AI that gives computers the ability to understand text and spoken words in much the same way humans can.
* Neural Network: A network or circuit of neurons, or in a modern sense, an artificial neural network composed of artificial neurons or nodes.

R

* Reinforcement Learning: A machine learning technique that enables an algorithm to learn through trial and error using feedback from its own actions and experiences.
* RNN (Recurrent Neural Network): This is a class of artificial neural networks in which connections between nodes form a directed graph along a temporal sequence.

S

* Supervised Learning: A type of machine learning and artificial intelligence where the model is provided with labelled training data.
* SVM (Support Vector Machine): A supervised machine learning model that uses classification algorithms for two-group classification problems.

T

* Transfer Learning is the reuse of a pre-trained model on a new problem, adjusting from the original task it was trained on to a similar one.
* Tensor: A generalized matrix or a multi-dimensional grid used in machine learning and scientific computing.

U

* Unsupervised Learning is a type of algorithm that learns patterns from untagged data. The system tries to learn without a teacher.

V

* Vision Systems: The methods and technology used to capture and interpret images and video for computer processing and analysis.

W

* Weak AI: Also known as narrow AI, this type of AI is designed and trained for a particular task. Virtual personal assistants, such as Apple's Siri, are a form of weak AI.
  
X

* XAI (Explainable AI): AI systems that offer human-understandable explanations for their decisions, making AI's actions transparent and understandable.
  
Y

* YOLO (You Only Look Once) is a real-time object recognition system that can identify objects in images and video with a single inspection rather than multiple inspections.

Z

* Zero-Shot Learning: An AI model is trained to recognize and categorize objects or concepts without having seen any examples of those categories or concepts beforehand

# Additional Buzzwords and Concepts
Quantum Computing is a type of computing that uses quantum-mechanical phenomena, such as superposition and entanglement, to perform operations on data. It has the potential to greatly accelerate certain types of AI algorithms.

Augmented Reality (AR) is an interactive experience of a real-world environment in which the objects that reside in the real world are enhanced by computer-generated perceptual information. AR can be used in various AI applications, including training models, to understand and interact with the real world.

Blockchain and AI Integration: Combining
blockchain technology with AI enhances security, transparency, and data management within AI applications.

Edge AI: Deploying AI applications directly on devices (such as smartphones, IoT devices, and edge servers) rather than processing data in a centralized cloud-based data centre. This approach can reduce latency, increase privacy, and enable real-time decision-making.

Federated Learning is a machine learning setting in which the model is trained across multiple decentralized devices or servers holding local data samples without exchanging them. This approach improves privacy and reduces the data required to be transferred.

Human-in-the-Loop (HITL): A model of interaction where a human is involved in the loop of AI's learning process, providing feedback, corrections, and training data to improve the AI system.

Interpretability is the extent to which a human can understand the cause of a decision made by an AI model. This is becoming increasingly important as AI systems are used in more critical applications.

Model Drift is the phenomenon where the model's predictive accuracy degrades over time due to changes in the underlying data it was trained on.

Neurosymbolic AI is an approach to AI that combines neural networks with symbolic reasoning to create models that can reason with abstract concepts, improving the flexibility and explainability of AI systems.

Privacy-Preserving Machine Learning: Techniques and approaches in machine learning that protect the privacy of individuals' data while still allowing models to be trained on that data.

# In Depth for YOLO 

YOLO (You Only Look Once): A real-time object detection system that applies a single neural network to the full image, making predictions directly from full images and detecting objects in a single pass.

# Object Detection Terms

* R-CNN (Region-based Convolutional Neural Networks): An algorithm that segments an image into regions and then runs a classifier on each region to find and label objects.
* Fast R-CNN: Improves on R-CNN by sharing computation over the entire image, making detection significantly faster.
* Faster R-CNN: Introduces Region Proposal Networks that share full-image convolutional features with the detection network, further speeding up the process.
* SSD (Single Shot MultiBox Detector): A method for detecting objects in images using a single deep neural network that predicts bounding boxes and class scores for every box simultaneously, making it faster than methods like R-CNN.
* Mask R-CNN: Extends Faster R-CNN by adding a branch for predicting segmentation masks on each Region of Interest (RoI), enabling precise object segmentation.
* Object Tracking: The process of identifying the same object across multiple frames captured by a camera. It is often used in conjunction with object detection to monitor objects over time.

Related Concepts

* Bounding Box: A rectangle drawn into an image to highlight the location of an object.
* Anchor Boxes: Predefined boxes of certain ratios and scales that CNNs use to detect objects at different scales and aspect ratios.
* Non-maximum Suppression (NMS): A technique used in object detection to select the most probable bounding box when several overlap for a given object.
* Precision and Recall: Metrics used to evaluate the accuracy of an object detection model, where precision measures the correctness of the predictions and recall measures the model's ability to detect all relevant cases.
* IoU (Intersection over Union): A metric used to measure the accuracy of an object detector on a particular dataset, calculated by dividing the area of overlap between the predicted bounding box and the ground truth bounding box by the area of union.
* Confidence Score: A value predicted by object detection models that indicates the certainty of the detected object belonging to a particular class.
* Semantic Segmentation: The process of partitioning an image into segments, where each pixel is labeled with a class of object to which it belongs, unlike object detection which identifies discrete objects.
* Instance Segmentation: Similar to semantic segmentation, but it differentiates between separate instances of the same class within the image.
