---
layout: page
title: AI-Enabled Camera 
description: 2020-Present
img: assets/img/tg.jpg
importance: 1
category: work
#related_publications: einstein1956investigations, einstein1950meaning
---

I have been always very passionate about wildlife conservation, especially to find tech-based solutions to prevent poaching of wildlife and mitigate the growing issue of Human-Wildlife conflict, rising rapidly in South-Asia due to growth of both human and wildlife population near the wildlife habitats.
So to continue my passion, in 2020 I joined <a href="https://www.resolve.ngo/trailguard.htm" target="_blank"> RESOLVE</a>, an NGO based in Washington DC as a Conservation Technology Fellow and started the development of TrailGuard AI, an AI-Powered Camera that can be placed on forest trails and send images in real-time (under 30 seconds) of humans and wildlife species crossing the camera. 


<span style="font-size: 17px;"><b>Drawbacks of Camera Technology currently available in the Conservation market :</b></span>

The battery-powered camera technology that is currently used for monitoring wildlife and poachers movement is very ineffective and has several drawbacks :

- Bulky size : These cameras are very bulky, and almost 30-40% of these cameras get stolen.
- Short battery life : The batteries of these cameras last only a few weeks, a big drawback given it is not very easy to frequently revisit these locations in forest due to difficult terrain.
- No Real-Time Image Transmission : These camera store the images on its SD card, there is not other way to remotely access data. To access data, it requires revisits. 
- Lacking AI on the Edge to Allow Filtering : These camera do not have any onbaord AI chip, to do inference on the images taken. 
- (Un)Reliability in field conditions : The mechanical enclosures of these cameras often fail in rainy and moist conditions.
- None of them are made in India : These cameras have to be imported to India from outside, making them quite expensive due to custom duty and taxes.

<div class="row justify-content-sm-center">

    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/old_cam.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Motor Simulation using E-Calc</div>

I divided my work into few parts : Camera Technology R&D, Manufactuing, Server Setup (Tiger YOLOv5), Deployment in Remote Forest Areas and raising awareness among the Donors.

<span style="font-size: 17px;"><b>1.) Camera Development : Technology R&D and Production :</b></span>


<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/TG_USP.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Motor Simulation using E-Calc</div>



The Camera is divided into two parts, the Camera System and Communication System Part and both these parts are joined together with an M12 cable and communicating with each other via UART and GPIOs.


<span style="font-size: 16px;"><b>a.) Development of Camera unit System :</b></span>

- The major components of the camera unit are, Atmega328PB MCU, Intel's Myriad X chip and ultra low-light Sony IMX462 image sensor.
- The camera is always in low-power sleep mode. When any movement happens in front of the camera, the MCU gets an interupt from the PIR sensor, and powers on the Myriad X which then captures the image. This duration from PIR trigger to image capture is around 200 ms, ensuring no objects are missed by the camera.
- After capturing the image, Myriad X runs the AI model (developed by CVEDIA), if probability of the detected object is more than a threshold, the image is sent to the communication unit system via UART. After this camera goes back to sleep mode, waiting for next PIR trigger.


Camera 2B to Camera 3B to Camera 4B PCB Image

Mech Enclosure also of 4B

<span style="font-size: 16px;"><b>b.) Development of Communication unit System to send data in real-time :</b></span>

- The major components of the communication unit are, ESP32s3, SIM7600 Cellular Modem and Seeed Studio LoRa E5 module.
- The communication unit is always in power down mode to preserve the battery. When any object of interest is detected on the camera unit side, the camera unit wakes up the communication unit and sends the image data to the ESP32 of the communication unit via UART. 

<span style="font-size: 15px;"><b>Type 1.) Cellular Communication unit :</b></span>

- After receiving the data, the ESP32 first waits for the SIM7600 modem to connect to a cellular network, once connected, the ESP32 sends the image jpeg data using MQTT AT commands to the SIM7600 modem which then sends it to the server. 
- After the data is sent to the server, the communication unit goes back to sleep.

<span style="font-size: 15px;"><b>Type 2.) LoRa Communication unit :</b></span>

- After receiving the data, the ESP32 converts this jpeg data to ssdv bytes, and transfer this data to LoRa E5 modem via UART.
- The LoRa E5 modem breaks this data into packets of 255 bytes and sends it to the Gateway LoRa unit placed in another location. 
- The Gateway LoRa unit is in duty cycle recevier mode in order to conserve power. But after receiveing the first packet from Transmitter LoRa unit, the Gateway LoRa unit exits the duty cycle mode, and goes to constant receive mode till it receives the entire data.
- After receiving the entire data from Transmitter LoRa unit, Gateway LoRa unit sends this data to the ESP32 via UART, which then sends it to server via the SIM7600 modem on it.

(Note: The LoRa Communcation unit (TX and Gateway) is useful for areas that have no cellular connectivity. So the Camera unit with LoRa TX Communication unit can be placed inside the forest area with no network, and can send the data to the LoRa Gateway Communication unit, which is already placed in an area with good cellualr coverage, and can send data to the server end. The problem with this system was that LoRa is more suitable for Line of Sight transmissions, so after several experiments, we found this solution to be not so suitable for dense vegetation forest areas)


add field guide maps of lora and sim7600
LoRa use cases (with Bike and Map images):
SIM7600 old modem (blue) to CCUv2 (PCIE) to CCUv4 Image
Mech Enclosure also of CCUv4
Responsibility : Block Diagram, to breadboard, to Sch, to Layout, to testing to field installation.
Datasheet of the Camera
lens focusing at VVDN

<span style="font-size: 16px;"><b>c.) Development of Cloud based Server :</b></span>

- Linode was used as a cloud based server.
- MQTT Broker service was running on the server end, waiting to receive data from the camera end. 
- The data received was converted into a jpeg image, ran through a Yolov5 model and based on the location and camera id, was sent to the respective end user. 
- Yolov5 object detection model was used on the server end to remove any false positives. Yolov5 has 80 classes, so in order to detect tiger, the model was retrained using tiger images dataset, and performed fairly well.


<span style="font-size: 17px;"><b>2.) Deployments :</b></span>

- We deployed the system in Kanha-Pench Tiger Reserve and Dudhwa Tiger Reserve with the respective forest department officials. Both these regions are hotspots for poaching and human-wildlife conflict issue.
<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/india-tg.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Motor Simulation using E-Calc</div>

- The deployment was done on the peripery of the parks, so any potential human intruder trying to enter the park can be caught in real-time or any wildlife coming out of the park can be detected before it enters the nearby villages.

<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Deploy-strategy.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Motor Simulation using E-Calc</div>



<span style="font-size: 17px;"><b>Images sent in real-time from India :</b></span>


<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/wildlife_tg.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>

<span style="font-size: 17px;"><b>Tigers and Elephants detected in real-time while trying to enter villages :</b></span>

<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/real_data_tg.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>

<span style="font-size: 17px;"><b>A gang of Poachers detected in Dudhwa Tiger Reserve, who were later arrested :</b></span>

<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/dudhwa_tg.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


<span style="font-size: 17px;"><b>Published on the Front page of the Hindu Newspaper </b></span>


<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/The Hindu Color Print.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


<span style="font-size: 17px;"><b>Camera hidden on the Tree that detected the poachers in Dudhwa Tiger Reserve :</b></span>

<div class="row justify-content-sm-center">

    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Dudhwa-poachers.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>



<span style="font-size: 17px;"><b>Organizing workshops to introduce the technology to the Forest Rangers and Village Communities :</b></span>

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
        <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy2.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy6.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
        <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy7.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


<span style="font-size: 17px;"><b>Deploying the Cameras with the Forest Rangers :</b></span>

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy5.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/deploy4.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


<span style="font-size: 17px;"><b>Demonstrating the Camera system to the Government Officials of India :</b></span>


<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/makeinindia_tg.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


<span style="font-size: 17px;"><b>3.) Media Coverage of the Work and Technology :</b></span>

<span style="font-size: 16px;"><b>Featured in the Award winning CNN Documentary : Mission Tiger</b></span>

<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Mission_cnn.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>

<span style="font-size: 16px;"><b>The Hindu Article : Arrest of Poachers in Dudhwa</b></span>

<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/hindu_online.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>

<span style="font-size: 16px;"><b>The Times of India Article : Real-Time detection of Tigers in the Kanha-Pench Tiger Reserve</b></span>

<div class="row justify-content-sm-center">

    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.html path="assets/img/TOI-TG.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>


Note : Currently this system is under production at VVDN in Delhi!

<span style="font-size: 17px;"><b>TG PDF :</b></span>
<a href="https://drive.google.com/drive/u/4/folders/1yQTbllgLPr3c9V7HNQWFJo04lzmBBcMy" target="_blank"> Github Repo Link</a> 
 <br>


<span style="font-size: 17px;"><b>Bioscience Paper :</b></span>
<a href="https://drive.google.com/drive/u/4/folders/1yQTbllgLPr3c9V7HNQWFJo04lzmBBcMy" target="_blank"> Github Repo Link</a> 
 <br>

