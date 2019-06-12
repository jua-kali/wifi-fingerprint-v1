# TL;DR
Although WAP signal strengths provide very messy data, we can still use them to locate a person to within 10 meters inside a building.

# Goal

This is a project I'm working on to try out new machine learning and data science techniques because the dataset is interesting and messy. 

*Status:* I've completed a baseline model to predict building, floor, latitude, and longitude. My best model has a mean error of 10.2 m, which would have roughly scored 4th in the 2015 EvAAL-ETRI Wi-Fi Fingerprinting Competition.

*Upcoming  Steps:* 
* Try a different data sorting method
* Try out FG Lab and Sacred as ways to document model experiments and results

# Problem Introduction
Although GPS is a reliable positioning technnology, it does not function well indoors because buildings block the signals from satellites.  For example, a user in a mall might want to find a way to their favorite store, but they cannot use GPS technology to map a route their because the satellite signals are very weak or non-existent indoors.

For indoor positioning an alternative approach is to utilize the signal strength from WiFi Wireless Access Points (WAPs) within the building.  For example, a user could install an app on their cellphone that senses the signal strength from different WAPs and then calculates their indoor position. This approach is called WiFi fingerprinting - the idea being that each indoor position will have a unique sets of signals from different WAPs in the building.

Although WiFi fingerprinting can be implemented without special sensors beyond those found in a normal mobile phone, the data from WAPs is quite messy.  The signal measurements when a user stands in the same place can be drastically different depending on many factors including:

* Mobile phone model
* Version of Android or iOS
* How the phone is held, the height of the user
* Number of people using the network
* Number of other people and obstacles physically present in the space 
* *WAPs can also move!*  For example a detected WAP could be a temporary hotspot set up on someone's mobile phone. 

The point of this project is to accurately locate a person despite the messiness in WAP signal data.


# The Dataset
[UJIIndoorLoc](https://archive.ics.uci.edu/ml/datasets/ujiindoorloc) is a publically available dataset from 3 large campus buildings with 4 or more floors. Each record consists of a location somewhere within the buildings and the WAPs detected at that location measured by Received Signal Strength Intensity (RSSI). The data also has the following characteristics:

* Recorded by 20 users and 25 different Android phones
* 108,703 m2 total covered indoor area
* Signals from 520 WAPs
* 19,937 training records and 1,111 validating/test records.
