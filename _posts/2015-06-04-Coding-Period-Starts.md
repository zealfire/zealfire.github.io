---
layout: post
title: Coding period started
---

The coding period for GSoC 2015 started from 25th May which means that student are expected to start writting the code for their proposed projects.The start of coding period always bring excitement and anxiety within the students because they know that code written by them would be for the first time used by so many people.

I was too excited by the beginning of coding period but the feelings were subdued a little bit because my end sem exams were starting from 27th and coding period from 25th. But the fact that I had started to work on project a little early and support from my mentors (<a href="https://www.drupal.org/u/sutharsan" target="_blank" style="text-decoration:none;">Erik</a>, <a href="https://www.drupal.org/u/jcnventura" target="_blank" style="text-decoration:none;">João</a>) helped me to complete the project part which I had proposed to do during the first week of coding period.

I had a meeting with my mentors on Skype on the day coding period started and we discussed about the architecture of module and other minor important things like platform over which module should be developed, name of the module.Also during the meeting the name of module was decided as "<bold>printable</bold>". The name cannot remain as print because Symfony considers it as a reserved keyword.

During the first week of coding period firstly I took some time to design the configuration form of the module. I managed to figure out that since in Drupal 8 so many things have been made as an entity so the print friendly version must be possible for 
many of them.

Finally I am populating only those entities in my form which has render controller as view_builder. Initially the module will be providing users with options like opening the print version on new/same page,option to add your CSS. The controller for the module has also been created but the functions called in them still needs to be completed which I have planned to complete next week.

By the end of week I also figured out that for providing the link to printer friendly versions of various entities like comment, content, user blocks can be used because they can prove to be very user friendly and also they go along with architecture of Drupal 8. I have currently started to complete functions used in controller and hope to complete those along with a plugin for the block in coming week.

The current develpoment of the module can be watched over <a href="https://github.com/zealfire/Hardcopy" target="_blank" style="text-decoration:none;">here</a>. 
