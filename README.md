# Engagement Recognition

Project work CSE555 Introduction to Pattern Recognition

The project aims to build an engagement recognition model that can accurately detect the affective state of an individual. The DAiSEE Dataset consists of videos of subjects during online courses and are available under different illumination settings. Each video is labelled with one of 4 affective states - boredom, engagement, confusion, frustration. Further each affective state is also rated based on the intensity ranging from 0-3.

# Dataset and Experimentation
User engagement recognition model to predict user’s affective state in a multi -view video conference. Using snippets from a dataset of 9068 videos
and 112 users to analyze user engagement.

We use teh [DAiSEE Dataset](https://docs.activeloop.ai/datasets/daisee-dataset) for this project which consists of videos of subjects during online classes and the model tries to classify the engagement into 4 affective states - boredom, engagement, confusion and frustation. To find the intensity of each state, we rate them from a range of 0-3.

Each video has been broken down to an image. Each video is 10 seconds long with 30 frames in each second thus we get 300 images from each 10 seconds video.
This experiment uses the [FaceNet model](https://arxiv.org/abs/1503.03832) to extract the face of each subject. The model uses the MTCNN package to extract one face from each image. The image is saved in the appropriate directory. Due to processing constraints, face detection was not performed for all frames of each video. Instead, 9 frames were selected that we evenly spread across the entire video.

The approach then uses the [EmotioNet algorithm](https://github.com/co60ca/EmotionNet/) for capturing the affective state of each individual. The approach uses a residual network variant with the help of the ResNet module from PyTorch called the BasicBlock ResNet. The dataset of faces is fed to the residual network to obtain the probability of each state. The model consists of 4 layers. The output layer is a softmax layer so that the resulting values are between 0-1 and can be interpreted as probabilities.

The experiment divides the affective state recognition into 4 distinct model runs. The model is run once for each affective state to obtain the intensity of the specific affective state. So, running the model once for boredom will get the intensity of boredom for the subject, and similarly for each affective state.

Due to the unavailability of the required processing power the model could not be trained for the DAiSEE dataset. Instead, the approach uses the weights that we obtained from an earlier model run on the [CK+ Dataset](https://ieeexplore.ieee.org/document/5543262) and [Karolinska Directed Emotional Faces (KDEF)](https://www.tandfonline.com/doi/abs/10.1080/02699930701626582?casa_token=tU1Q6BgopAAAAAAA%3A0AWCN1vWLQiDk932Hzw3cJkaZ4JQm9IVv6kIqJT2BnxqQO0c90OMqaBiownE6dCa7fHJSLxPDxXX&journalCode=pcem20) datasets.

Due to processing constraints, the experiment could only be performed for 239 videos out of the 9068 video corpus. With further processing capabilities the results can be significantly improved.


