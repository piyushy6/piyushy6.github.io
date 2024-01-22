---
layout: page
title: Farm Fire Monitoring
description: 2020
img: assets/img/drone-stubble-burning.jpg
importance: 3
category: work
---

I worked as a Researcher with <a href="https://appliedsciences.nasa.gov/about/our-team/pawan-gupta-0" target="_blank">Dr. Pawan Gupta</a> to evaluate the impact of Stubble Burning on PM-2.5 levels.

<span style="font-size: 17px;"><b>Problem :</b></span>
Farmers in the state of Punjab and Haryana burn the stubble and this burning leads to high pollution levels from October to January season in Northern India. Currently, only Satellite data is used to monitor these farm fires, but this Satellite data is collected only 2 times during the day, thus limiting its use.

<span style="font-size: 17px;"><b>Solution :</b></span>
If authorities have more real-time data on Stubble Bunring and its sites, they can take much more effective action to limit its spread and control it.

<span style="font-size: 17px;"><b>1.) Drone Farm Fire Monitoring :</b></span>

- During our study, for collecting the PM-2.5 data I integrated low-cost Purple Air (Plantower PMS5003) and Alphasense OPC-R1 sensors on a Phantom 4 drone, and flew the drone over a farm fire site that was happening in Karnal district in Haryana, India.

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/Drone-Sensor-Fire.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Phantom 4 drone with Purple Air sensor suspended to it by a rope and flying over a farm fire site to collect data.</div>

- We observed significant changes in PM-2.5 values before, during and after the fire, with a clear spike in PM-2.5 values observed during the fire. We also tried to compare our results from the sensor integrated on the drone to the data taken by the Satellite at 1:30 pm.

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/farm_fire.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    On the left, is the farm site Pre-Fire. Middle, the farm site During-Fire. Right, the farm site Post-Fire.
</div>

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/farm_data.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>


</div>
<div class="caption">
On the left, are the two farm sites used for the experiment. Right, PM2.5 variation with the fire progress (Pre, During and Post). A spike in PM2.5 is visible during the fire phase.
</div>

<span style="font-size: 17px;"><b>2.) Farm Fire Impact on Villages :</b></span>

- The impact of stubble burning on the air quality is significant in the nearby villages where stubble is burned. To get more data on this, I went across the villages in Karnal where stubble burning was happening and collected PM2.5 data by performing mobile sensing with the car. The collected data in these rural areas clearly showed a significant spike in PM-2.5 values.
<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/farm_sites.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>


</div>

<div class="caption">
Some farm fire sites were found while collecting the data.</div>

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/rural_data2.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
Data was collected by mobile sensing near stubble-burning sites. A significant spike was observed in PM2.5 values near the 3 different sites.
</div>

- I also did mobile sensing in rural areas with negligible farm fires and interestingly found that rural areas where farm fires are very frequent, had significantly higher PM-2.5 concentrations, thus showing the impact of farm fires in rural areas.

<div class="row"> 

    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/rural_data1.jpeg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
Significantly lower PM2.5 values in rural areas with less stubble burning on the right.</div>


<span style="font-size: 17px;"><b>Project Supervisor :</b></span>
<a href="https://appliedsciences.nasa.gov/about/our-team/pawan-gupta-0" target="_blank"> Dr. Pawan Gupta</a> 
 <br>

<span style="font-size: 17px;"><b>Work Funded by : Dr. Pawan Gupta and Self Funded</b></span>
 <br>

<span style="font-size: 17px;"><b>Script 1:</b></span>
<a href="https://github.com/piyushy6/Mobile-Air-Quality-Sensor" target="_blank"> Github Repo (storing PM data from Alphasense Optical Particle Counter sensor on Raspberry Pi)</a> 
 <br>

<span style="font-size: 17px;"><b>Script 2:</b></span>
<a href="https://github.com/piyushy6/Rpi-Pixhawk-GPS" target="_blank"> Github Repo (storing GPS and telemetry data from Pixhawk to a CSV file on Raspberry Pi via MavlinkLink)</a> 
 <br>

<span style="font-size: 17px;"><b>Script 3:</b></span>
<a href="https://github.com/piyushy6/Purple-Air-Live-Data" target="_blank"> Github Repo (storing the real-time data of Purple Air sensor)</a> 
 <br>

<span style="font-size: 17px;"><b>Script 4:</b></span>
<a href="https://github.com/piyushy6/Spatial-Plots" target="_blank"> Github Repo (plotting data on a map)</a> 
 <br>







