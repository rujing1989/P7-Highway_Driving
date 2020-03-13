# **Write up of the Project Highway driving**

## 1. Variable setting

* turn_left : this varible is used to judge if it is safe to swtich to the left driving lane. 
* turn_right : this varible is used to judge if it is safe to switch to the right driving land.
* time_keep : this varible is used to judge if the ego car decelerates for such a long time. When it is too crowded in the driving lane or the cars in front of the ego car move too slow, and when the value of time_keep reaches to 40, the ego car shall switch to other driving lanes.

## 2. Specific implementation

Most part of this code is written with the thought of the lessons. Beside the suggestion of the part "Project Q&A", some other logic is also supplied in my code. 

A threshold is set to judge if there is enough space on the beside driving lanes, which means the empty gap on the beside driving lane is enough for driving lane switch. Severl thresholds were compared, such as 25, 30, 35 meters in both front and rear direction of the ego car on the beside driving lane. Although all these 3 thresholds are satisfied to drive safely. With thresholds 25 and 30, the driving behavior of ego car is more aggressive, which have higher possibility to make an accident, especially by switch to "Manual Mode". Therefore the threshold of 35 is selected as the safty gap for driving lane switch. It is used in the line 253, 266, 268, 278 and 280 in the file "main.cpp".

Other cases must be considered are that, when the ego car is driving on side driving lane, there is only one lane could be switch to. As the line 241 to 244 in the code "main.cpp" shows, when the ego car drive on the left driving lane, is not allowed to switch to left, as well as that of the right driving lane.

When a car is driving in front of the ego car at the same driving lane, and the distance between them is not long enough, a decision should be made if the ego car should switch the driving lane. When these two cars are too close over a certain duration, which means the front car is too slow, and the ego car should switch to the left driving lane to overtake the front car. On the other hand, when these two cars are too close and this state does not exist too long, which means the ego car move slower than the front car, and the ego car switch to the right driving lane. The variable "time_keep" indicates the duration that the two cars are too close. With a comparision of different values of the variable "time_keep", 40 is selected due to the sane driving behavior. As the code from line 284 to 298 shows, when the two cars are too close and the variable "time_keep" is over 40, the ego car start to switch, otherwise the car keep in this driving lane.
