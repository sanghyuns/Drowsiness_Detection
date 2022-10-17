# Capstone Project: Drowsiness Detection 

## Introduction
According to the National Highway Traffic Safety Administration, going over 20 hours without sleep may be equivalent of having a blood-alcohol concentration of 0.08 which is the US legal limit and an estimated amount of about 100,000 crashes involving drowsy drivers per year leading to about 50,000 injuries and nearly 800 deaths. With the current 24/7 society trending towards a lifestyle that does not encourage restfulness, these crashes will continue to increase as more people drive under fatigue.

My project aims to target this problem. I have created a convolutional neural network using data collected from the University of Texas at Arlington which had 30 hours of RGB videos of 60 participants. 

For each participant there were 3 videos, each representing a different class: alert, low vigilance, and drowsy, each of them 10 minutes long. All of the participants were over 18 years old, majority of them males (51 males, 9 females) from different ethnicities and age groups. There were 21 videos of theh 180 where the subjects wore eyeglasses and 72 videos consisted of considerable facial hair. Each video was self-recorded by each participant with their own cell phone or web camera.

Once implemented into an application, I wanted this project to be able to answer these questions:
- How could I be able to reduce the number of collisions caused by driving while drowsy?
- Can we accurately be able to assess the drowsiness of the driver?

## Executive Summary

The videos required about 114 gbs of free storage space. Due to the limitations of my local machine, I opted to use only parts of each videos rather than whole. Once the videos were downloaded, I separated each video into frames. Due to the sheer amount of frames generated in each video, I chose to reduce the number of frames by taking one frame each second. This method significantly reduced the number of frames while keeping the context of each frame for the duration of the entire video.

My first model was able to predict the condition of the participant at an average of 64% accuracy rate with a validation loss at around 4.42 which wasn't ideal, as the loss seemed too high. The model was also severely overfit, as it was 99% accurate for the train data.

My next model used Transfer Learning. The transfer learning approach takes a pre-trained model and uses it to potentially improve the accuracy of the model. To put it simply, instead of adding layers of the model ourselves, we are able to use a model with layers already added in it. I decided to use Efficient Net, as we discussed in class and the model came back with an accuracy rate of around 57%. Although the accuracy rate seemed to have decreased slightly, the validation loss decreased significantly to around 1.02. This model was unfortunately overfit as well, with the training accuracy sitting around 99.83%.

My last model, a much more complicated sequential model than my first, was also overfit. It had a training accuracy of 99.79%, but a validation accuracy just over 60%.

## Conclusions

It seems like my first, less complicated sequential model performed the best. It is important to note that the number of epochs ran was not equal, and performance peaked at various times in each model.

## Recommendations

There are no recommendations that the model can produce, given the nature of our problem statement, but the National Highway Traffic Safety Administration offers these tips to drive alert:

1. Getting adequate sleep on a daily basis is the only true way to protect yourself against the risks of driving when you’re drowsy. Experts urge consumers to make it a priority to get seven to eight hours of sleep per night.
2. Before the start of a long family car trip, get a good night’s sleep, or you could put your entire family and others at risk.
3. Many teens do not get enough sleep at a stage in life when their biological need for sleep increases, which makes them vulnerable to the risk of drowsy-driving crashes, especially on longer trips. Advise your teens to delay driving until they’re well-rested.
4. Avoid drinking any alcohol before driving. Consumption of alcohol interacts with sleepiness to increase drowsiness and impairment.
5. Always check your prescription and over-the-counter medication labels to see if drowsiness could result from their use.
6. If you take medications that could cause drowsiness as a side effect, use public transportation when possible.
7. If you drive, avoid driving during the peak sleepiness periods (midnight – 6 a.m. and late afternoon). If you must drive during the peak sleepiness periods, stay vigilant for signs of drowsiness, such as crossing over roadway lines or hitting a rumble strip, especially if you’re driving alone.

## Limitations

There are few, but significant limitations within this project. 
1. Cutting down frames: I would have preferred to keep all the frames within the videos in order to ensure the accuracy of the model. The accuracy may not exactly answer the questions I had when I first began.

2. Lack of computing power: Looking into several cloud services, I found that the computing power required to evaluate the models at an efficient rate would be costly. My local machine was able to run these models, albeit much slower, so I opted to use my local machine. My plan is to re-evaluate these models when I have access to a cloud in the future.

3. Unimportant elements in each frame: It is highly likely that the model has taken unimportant elements in the background of the videos that altered the accuracy of what we're looking for. 

## Future Prosepct

With this project, I was able to develop a neural network model that correctly assesses the state of the participant at a semi-high rate: around 60%, which is higher than our baseline of predicting all in one state which would be 50%. This only partially answers the questions that I developed at the beginning of the project. It fails to answer how we are to reduce the number of collisions caused by driving while drowsy.

My next steps in this project moving forward, along with addressing the limitations, is the develop an application that accesses a camera for the participant, captures the face and more importantly the eyes, records and saves the frames within a time period, then use those frames to train the model. I was successfully able to capture the face and eyes, but have yet to develop a way to save for the modeling process. Once the model is trained, We could then run live-feed camera frames through the model which determines the state of the participant.

## Final Thoughts

There are many aspects in which drowsiness detection can be addressed, one of them being the approach that I took. Another approach could be automated driving. Depending on the progress of automated driving, driving while drowsy can be eliminated completely within the next decade.

Unless society as a whole encourages restfulness and not its current 24/7 lifestyle, a solution is absolutely necessary. Whether it is in the form of automated driving or confirmation of alertness, it is no question that driving while drowsy will continue to be a problem as it has been so far.

I look forward to addressing the limitations of my project within the next couple of weeks. 

## Data

The complete dataset consisting of all 180 videos can be found here: https://sites.google.com/view/utarldd/home
