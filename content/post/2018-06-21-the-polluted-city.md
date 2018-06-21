---
title: The polluted city
author: ''
date: '2018-06-21'
slug: the-polluted-city
categories: []
tags:
  - data viz
draft: true
---

<style>

img {
    max-width: 1800px;
    display: block;
    margin-left: -500px;
    margin-right: 0px;
    position: relative;
    border: 1px solid #ddd;
    box-shadow: 5px 5px 5px #eee;
}

</style>

Hanoi, the capital of Vietnam, is infamous for many things, say chronic traffic
jams, insanely high property prices or poor food safety. And, to make the list a
bit longer, the city is reaching an alarming level of [air
pollution](https://e.vnexpress.net/news/insight/air-pollution-in-hanoi-reaches-alarming-levels-3364977.html).

Indeed, the phenomenon might have occurred for years. But recent open data, from
both [individuals](http://www.aqivn.org/vi/) and
[agencies](https://vn.usembassy.gov/air-quality-monitor/), has provided
empirical evidences for, and raised public concerns over the city's degrading
air quality. Some
[records](https://saigoneer.com/saigon-health/8196-hanoi-s-air-quality-ranked-second-worst-in-the-world-yesterday)
revealed that Hanoi's outdoor pollution was on a par with the world's most
polluted cities in India and China. These figures should frighten its citizens
as
[WHO](https://www.weforum.org/agenda/2018/05/these-are-the-worlds-most-polluted-cities)
said that polluted air contributed to a quarter of deaths from heart disease,
stroke and lung cancer which kills 7 million people each year.


![air-quality](/post/img/2018-06-21-the-polluted-city/the-polluted-city.png)


### Notes

* I used data from the U.S. Embassy Hanoi Air Quality
  [Monitor](https://vn.usembassy.gov/air-quality-monitor/) which is made readily
  available by
  [AirNow](https://airnow.gov/index.cfm?action=airnow.global_summary#Vietnam$Hanoi)

* I used R to clean data and make the chart (see codes
  [here](https://github.com/chuvanan/data_projects/tree/master/datatalk-meetup/meetup-02))
