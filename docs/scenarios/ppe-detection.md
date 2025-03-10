# **PPE Detection**

> Prevent Workplace Injuries and Occupational Hazards with Vision AI


## Overview

Personal protective equipment, or "PPE," is the clothing worn to reduce exposure to risks that might result in significant workplace diseases and injuries. Contact with chemical, radioactive, physical, electrical, mechanical, or other job hazards may cause these wounds and illnesses. Items like gloves, safety goggles, shoes, earplugs or muffs, hard hats, respirators, coveralls, vests, and full-body suits are examples of personal protection equipment. Accidents and injuries due to employees not wearing PPE hold business owners/employers legally accountable. Apart from legal damages, accidents due to PPE negligence result in loss of time, reduced productivity, costly worker compensations, etc.

- Workplace Fatalities are rising, and employers cannot afford to tolerate PPE negligence. According to the Bureau of Labor Statistics, there were 5,190 fatal work injuries recorded in the United States in 2021, an 8.9-percent increase from 4,764

- Speaking about one of the most injury-susceptible body parts - hands, OSHA reports that almost 70 percent of hand and arm injuries could be prevented with personal protective equipment, specifically safety gloves. Yet, 70 percent of workers don’t wear hand protection, and 30 percent don’t wear the right kind of glove for the task.

- If we consider one of the leading causes of workplace fatalities - Head Injuries a study by BLO found that 84% of head injuries at a worksite were due to the absence of safety helmets. A percentage which not small considering there were 68,170 head injuries in 2021

Therefore, complete compliance is necessary since even a brief lapse in usage can prove fatal. To monitor PPE compliance, cameras can be used.

## Vision AI based monitoring

Vision AI based monitors can be used to monitor PPE compliance by providing real-time video feeds of the factory unit. The cameras scan every frame to ensure there's no PPE negligence, eliminating occupational hazards and serious injuries.

To ensure accuracy and reliability, these camera-based monitoring services should be supplemented by strong compliance processes. Furthermore, workers working in different factory units should always be made aware of PPE compliance practices.


## Camera Configuration

Ceiling-mounted cameras are ideal for wide-area surveillance and can cover larger areas with fewer cameras, making them a cost-effective and efficient option. If your workplace has a large area where PPE is required, such as a manufacturing facility or a construction site, ceiling-mounted cameras may be the best option for PPE detection.

On the other hand, straight-mounted cameras are useful for capturing facial features and other details, making them a good option for PPE detection in smaller, more focused areas. If your workplace has specific locations where PPE is required, such as in a laboratory or a clean room, straight-mounted cameras may be a better option for PPE detection.

### Camera Placement

- Install cameras at entry points, employee locker rooms, and common areas where PPE is required, such as manufacturing floors, construction sites, and warehouses.
- Place cameras at exits to ensure that employees do not leave the facility without wearing proper PPE.


### Camera Height

- Cameras should be installed at a height of 6-7 feet above the floor level.

- Place the camera 5-8 feet from the focal point.

### Camera Angle Mounting Ranges

- Place the camera at a level angle to capture footage of the employee's face and upper body.

Find more details about camera placement [here](../overview/cameras.md).

### Dataset

The dataset for this scenario is based on PPE detection algorithms that are currently in practice.

The dataset is made up of images and videos gathered from various sources. The dataset has been catalogued to ensure real-world intricacies. It has an even distribution of:

- Different(indoor/outdoor) environments
- Male vs Female
- Variations in PPE suits
- Variations in gloves, helmet, goggles, safety-vest design
- Different light settings
- Variations in camera orientations
- Using security camera feeds

Total number of images used was 207,300

### Model

The model is based off of the YOLOv5 algorithm. The model is trained on a custom dataset of images and videos. The model is trained based on the above dataset compiled by our team.

The model provides the following metrics:


<div class="main">
    <div class="bar">
        <h4>Precision <i class="fa fa-info-circle"></i></h4>
        <div role="progressbar" style="--value:88"></div>
    </div>
    <div class="bar">
        <h4>Recall <i class="fa fa-info-circle"></i></h4>
        <div role="progressbar1" style="--value:86"></div>
    </div>
    <div class="bar">
        <h4>mAP <i class="fa fa-info-circle"></i></h4>
        <div role="progressbar2" style="--value:91"></div>
    </div>
</div>

The model is adaptable enough to run on any edge computing device.

## Scenario details

The business logic for this scenario is as follows:

- We use existing camera feeds from the premises to monitor the compliance of PPE in the workplace.
- VisionAI system is able to run on edge devices. It uses camera feeds for processing.
- We detect people in the camera feed and we monitor whether the person is wearing safety gloves, goggles, helmet, mask, safety-shoes and vest or not.
- If the person is detected without safety gloves, goggles, helmet, mask, safety-shoes and vest, an alert is raised.

## Events Supported

This scenario supports the following event:

- **PPE detected**: This event is generated when a PPE including goggles, gloves, helmet, mask, safety-shoes, vest, etc. are detected in the camera feed.

## Features

- Real-time monitoring: The solution enables you to monitor PPE compliance events in real-time, using camera feeds from the premises.

- Alert system: The solution provides an alert system to notify the concerned authorities in case of PPE negligence.

- Customizable: The solution is customizable to suit your needs. You can customize the solution to monitor PPE compliance in your workplace.



## Training with custom data

The scenario is provided as part of our GPL-v3 package for VisionAI. If you wish to train this with custom datasets, please contact us and we can provide you with the training code. You can do custom training with your own datasets for free, as long as it complies with GPLv3 license (you give back the code to the community). If you are interested in a custom license, please [contact us](../company/contact.md).

## Contact Us

- For technical issues, you can open a Github issue [here](https://github.com/visionify/visionai).
- For business inquiries, you can contact us through [our website](https://visionify.ai/contact).
