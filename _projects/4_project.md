---
layout: page
title: Mobile Air Quality Monitoring
description: 2020
img: assets/img/car.jpg
importance: 4
category: work
---

I worked as a Researcher with <a href="https://appliedsciences.nasa.gov/about/our-team/pawan-gupta-0" target="_blank">Dr. Pawan Gupta</a> to evaluate the efficacy of low-cost air quality sensors as a mobile platform to collect PM-2.5 data in urban areas.

<span style="font-size: 17px;"><b>Problem :</b></span>
- India has one air quality monitoring station for every 7 million people while China has over eight times that number.
- India has 9 cities in the world’s 10 most polluted cities.
- Only just about 5% of our census towns are monitored now.
- A new automated static air quality monitoring system will require approximately Rs. 1.8 crore to set up.

<div class="row justify-content-sm-center">

    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/HT-AQ.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Air Quality Monitoring station density globally (Source - Hindustan Times)</div>

<span style="font-size: 17px;"><b>Solution :</b></span>

A low-cost alternative for Air Quality Monitoring in India :
- Till now Air Quality Monitoring is done with costly static sensors only, which are distributed very sparsely.
- Low-cost Air Quality sensors make it possible to deploy them at scale by integrating them on vehicles, and UAVs and get fine-grained AQ data in real-time.
- This will help us to better analyze the data and could be very crucial to locate pollution hotspots and predict future AQ levels.
- For Urban Cities, by using cars as a mobile air quality monitoring platform and integrating low-cost air quality sensors on it, it is possible to do a spatio-tempotal sampling of PM-2.5 levels, to more accurately detect the sources of pollution in an urban area.


<span style="font-size: 17px;"><b> Mobile Air Quality Monitoring Experiment in Jaipur city :</b></span>

- For our study, we used the Diwali festival as the occasion to collect data with our mobile monitoring platform. We were focused on and collected data with our mobile platform, pre, during and post-fire cracker burning activities during Diwali, to effectively monitor the variation and impact of firecrackers on the air quality of Jaipur city.
- For making the sensor fusion module, we used a Raspberry Pi that acted as the central unit. Both Purple Air (Plantower PMS5003) and Alphasense OPC-R1 sensors were connected to the Raspberry Pi and sent data at every 5 to 10-second interval. Similarly, GPS was storing location and date time on the Raspberry Pi. There was a script running that combined and mapped PM-2.5 data from the two sensors with datetime, and location from the GPS module. Later we plotted this data using matplotlib on a map of Jaipur city.
- The sensor module was housed inside a plastic mechanical enclosure and the PM-2.5 sensors were exposed to the air.

<div class="row"> 

    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/Sensor-diwali.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data-stored-rpi.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, an air quality sensor (OPC-R1 and Purple Air) used for mobile monitoring is placed on top of the car. Right, inside of the data fusion module with air quality sensor, GPS, Raspberry Pi.
</div>

- After collecting the data for a week, we observed significantly lower PM2.5 in Jaipur during 2020 Diwali compared to previous years due to favourable weather conditions and the firecracker ban.

<div class="row"> 
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/mobile-monitoring-map.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
        <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/car-diwali.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
On the left, the script running on Raspberry Pi stores PM2.5 and GPS data in a CSV file. Right, data was collected by performing mobile air quality monitoring on 3 different Paths (A, B, C) of Jaipur during different days and times.
</div>

- With mobile air quality monitoring, the location of a pollution hotspot was also identified in Jaipur city.

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Hotspot.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/spatio-temporal-variation.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sensor-valdiation.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
On the left, is a Hotspot (construction site of a flyover) located by mobile monitoring experiment. Middle, Time-series plot of PM2.5 concentrations observed by performing mobile monitoring on 3 different Path. Right, Purple Air sensor data collocation results against a reference monitor (Shastri Nagar station) in Jaipur.
</div>

- We also studied the long-term (2000–2020) aerosol optical depth of Jaipur city and Observed a 29% increase in aerosol optical depth of Jaipur, but it was found to be significantly lower than Delhi.

- We also observed an increase in aerosol optical depth and PM2.5 due to crop residue burning during Diwali week in Jaipur.

<div class="row"> 

    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/20yr-AOD.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Stubble-AOD.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
On the left, a) Mean aerosol optical depth (2000-2020) derived from two MODIS sensors over India. b) Trends in AODs over the same period for Delhi and Jaipur. c) Annual mean PM2.5 trends (2017-2020) in two cities. Right, the Impact of aerosol transport over Jaipur during the 2020 Diwali week was observed from the VIIRS sensor.

</div>

<span style="font-size: 17px;"><b>Project Supervisor :</b></span>
<a href="https://appliedsciences.nasa.gov/about/our-team/pawan-gupta-0" target="_blank"> Dr. Pawan Gupta</a> 
 <br>

 <span style="font-size: 17px;"><b>Work Funded by : Dr. Pawan Gupta and Self Funded</b></span>
 <br>


<span style="font-size: 17px;"><b>Script 1:</b></span>
<a href="https://github.com/piyushy6/Mobile-Air-Quality-Sensor" target="_blank"> Github Repo (storing PM data from Alphasense Optical Particle Counter sensor on Raspberry Pi)</a> 
 <br>

<span style="font-size: 17px;"><b>Script 2:</b></span>
<a href="https://github.com/piyushy6/Purple-Air-Live-Data" target="_blank"> Github Repo (storing the real-time data of Purple Air sensor)</a> 
 <br>

<span style="font-size: 17px;"><b>Script 3:</b></span>
<a href="https://github.com/piyushy6/Spatial-Plots" target="_blank"> Github Repo (plotting data on a map)</a> 
 <br>



