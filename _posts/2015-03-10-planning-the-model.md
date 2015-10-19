---
title: Planning the Model
author: admin
layout: post
permalink: /2015/03/planning-the-model/
categories:
  - Final Project
  - OU Degree
  - Programming
tags:
  - domain modelling
  - OU
  - Programming
---
Now I&#8217;ve got my CI server ready to build my project when I make a change and SonarQube installed and ready to tell me off for coding errors and test coverage, I can actually start planning to write some code.

I need to plan out my model. There have been sections in a couple of modules about this so I think it&#8217;s probably best to use the method taught at the OU &#8211; that should hopefully get me some brownie points. Basically I need to describe the product and then pull out nouns and noun phrases as class candidates.This should hopefully also get me some basic attributes for the classes to. So here it goes&#8230;

<p style="padding-left: 30px;">
  The system&#8217;s scheduler will kick off a process twice a day. In the morning the system will check a weather service for key pieces of data &#8211; did it rain overnight, if so, how much, is it predicted to rain today and if so, how heavy will it be? Using this weather forecast and history the system will be calculate whether the garden should be watered and for how long. If the system decides that the garden should be watered then it will send a request over the network to one or more nodes to open their valves for a set amount of time. The nodes will reply with a response containing a success or failure status and any errors if they occurred. The weather forecast, request to the nodes and response from the nodes will be saved into the database.
</p>

<p style="padding-left: 30px;">
  This process will be repeated in the evening to check whether the forecast was correct and no action is needed or whether the garden needs watering.
</p>

<p style="padding-left: 30px;">
  A web interface will be provided so that users can see a history of watering jobs, their status and any errors associated with them. Users will also be able to see charts displaying information regarding water usage and rain fall for set periods of time. Finally users will be able to initiate watering through the interface.
</p>

From the description we try and pull out some relevant nouns and decide if they are a possible class, attribute of a class or should be rejected.

  * System &#8211;  the whole system, out of scope
  * Scheduler &#8211; Possible class
  * Process &#8211; Possible class
  * Day &#8211; Event
  * Morning &#8211; Event &#8211; could be an attribute of process?
  * Weather service &#8211; Possible class
  * Pieces of data &#8211; Too vague
  * Weather forecast &#8211; Possible class
  * Weather history &#8211; Possible class
  * Rain &#8211; Possible attribute of weather forecast
  * Garden &#8211; out of scope
  * Request (to water) &#8211; Possible Class
  * Node &#8211; out of scope
  * Valve &#8211; Interface to which could be a possible class
  * Amount of time &#8211; attribute of RequestToWater
  * Response (from watering) &#8211; Possible class
  * Success or failure status &#8211; possible attribute of ResponseFromWatering
  * Error &#8211; possible attribute of ResponseFromWatering
  * Request to the node &#8211; duplicate of RequestToWater
  * Response from the node &#8211; duplicate of ResponseFromWatering
  * Database &#8211; Possible class (Data Access Object (DAO))
  * Evening &#8211; Event
  * Action &#8211; duplicate of RequestToWater?
  * Web interface &#8211; too abstract
  * Watering job &#8211; Same as process?
  * User &#8211; Possible class
  * Chart &#8211; Possible class
  * Water usage &#8211; Possible class
  * Rain fall &#8211; Possible class
  * Period of time &#8211; an attribute of a request for data?

The web interface is part of a later phase so we&#8217;ll disregard possible classes from there for the time being.

For our key domain I think we have&#8230;

<span style="text-decoration: underline;">Scheduler</span>

  * Morning trigger time
  * Event trigger time

<span style="text-decoration: underline;">Weather Service</span>

<span style="text-decoration: underline;">Weather Forecast</span>

  * Probability of rain
  * Predicted temperature

<span style="text-decoration: underline;">Weather History</span>

  * Did it rain?
  * Amount of rain
  * Average temperature

<span style="text-decoration: underline;">IrrigationRequest</span>

  * Amount of time to water

<span style="text-decoration: underline;">IrrigationResponse</span>

  * Success?
  * Error(s)

<span style="text-decoration: underline;">Process/Job</span>

  * Time Started
  * Started manually or by the scheduler
  * Forecast
  * History
  * Request
  * Response

<span style="text-decoration: underline;">DAO</span>

I think that looks like a good place to start. I&#8217;m sure I&#8217;ll need some more attributes and such. In addition to actually setting up the classes I want to get the architecture in place to do persistence tests in the build using a lightweight database like H2.