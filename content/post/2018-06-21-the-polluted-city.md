---
title: The polluted city
author: ''
date: '2018-06-21'
slug: the-polluted-city
categories: []
tags:
  - data viz
---


Hanoi, my home city, is infamous for many things, say chronic traffic jams,
insanely high property prices or poor food safety. And now, to make the list a
bit longer, the city was reaping another status with an alarming level of [air
pollution](https://e.vnexpress.net/news/insight/air-pollution-in-hanoi-reaches-alarming-levels-3364977.html).

Indeed, the phenomenon might have
[occurred](http://file.scirp.org/pdf/JEP_2013102913333798.pdf) for years. But
recent open data, from both [individuals](http://www.aqivn.org/vi/) and
environment [agencies](https://vn.usembassy.gov/air-quality-monitor/), has
provided accessible, empirical evidences for, and raised public concerns over
the capital's degrading air quality. Some
[records](https://saigoneer.com/saigon-health/8196-hanoi-s-air-quality-ranked-second-worst-in-the-world-yesterday)
revealed that Hanoi's outdoor pollution was on a par with the world's most
polluted cities in India and China. These figures should frighten its citizens
as the
[WHO](https://www.weforum.org/agenda/2018/05/these-are-the-worlds-most-polluted-cities)
said that polluted air contributes to a quarter of 7 million deaths from heart
disease, stroke and lung cancer each year.

To better understand the condition, I made use of publicly available air quality
data obtained from U.S. Embassy where they have a monitoring station located in
downtown Hanoi. The chart below shows a picture of the city's daily outdoor air
pollution and how it changes for different months.


<style>
#myImg:hover {opacity: 0.7;}
</style>

<img id="myImg" src="/post/img/2018-06-21-the-polluted-city/the-polluted-city-v2.png" alt="Hanoi, the polluted city" width="800">

<!-- The Modal -->
<div id="myModal" class="modal">
  <span class="close">×</span>
  <img class="modal-content" id="img01">
  <div id="caption"></div>
</div>

<script>
// Get the modal
var modal = document.getElementById('myModal');

// Get the image and insert it inside the modal - use its "alt" text as a caption
var img = document.getElementById('myImg');
var modalImg = document.getElementById("img01");
var captionText = document.getElementById("caption");
img.onclick = function(){
    modal.style.display = "block";
    modalImg.src = this.src;
    captionText.innerHTML = this.alt;
}

// Get the <span> element that closes the modal
var span = document.getElementsByClassName("close")[0];

// When the user clicks on <span> (x), close the modal
span.onclick = function() {
    modal.style.display = "none";
}
</script>

<!-- ![air-quality](/post/img/2018-06-21-the-polluted-city/the-polluted-city.png) -->

### Notes

* This visualization is by no means a truly original work of mine. It is
  inspired by the master piece in Edward Tufte's *The Visual Display of
  Quantitative Information* (page 30), and is an adaption of Brad Boehmke's
  *[Daytons's Weather in 2014](http://rpubs.com/bradleyboehmke/weather_graphic)*

* I used data from the U.S. Embassy Hanoi Air Quality
  [Monitor](https://vn.usembassy.gov/air-quality-monitor/) which is made readily
  available by
  [AirNow](https://airnow.gov/index.cfm?action=airnow.global_summary#Vietnam$Hanoi)

* I used R to clean data and make the chart (see codes
  [here](https://github.com/chuvanan/data_projects/tree/master/datatalk-meetup/meetup-02))
