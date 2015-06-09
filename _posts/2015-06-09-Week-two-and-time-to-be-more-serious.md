---
layout: post
title: Week two and time to be more serious
---

The second week of coding period has started and its time to be more serious. But along with being serious I must say that I have began to like Drupal 8 mainly because of object oriented approach required to be used while coding and various APIs present in it which makes our work a lot easier.

Even though I am saying that the APIs have made our work a lot easier but I forgot to tell you that finding a particular API that may come in handy in a particular situation is not easy mainly because of large code base of Drupal. Also as per my experience till now following object oriented approach of programming is difficult in the beginning but after some time we get used to it and eventually begin to like it.

In the second week I had two meetings with my mentors. During the meeting I came to know about this wonderful CodeSniffer available at this <a href="https://www.drupal.org/node/1419988" style="text-decoration:none;" target="_blank">link</a>. I think it can prove to be very helpful to other GSoC students too because since as a newbie we make mistake in following Drupal 8 coding standards and this tool can prevent that from happening. Also my mentors told me that adding comments like @todo and/or mock class/method/function to mark loose ends in the code always makes the task of module development easier in the latter stages.

The task completed in this week were carried out as stated in the proposal. The functions being called in the controller were completed. The plugin which would display a printable version of page was also implemented. A lot of changes were made in the schema file of module because of inclusion of various setting options in the module. A base class for plugins was created whose main job was to generate HTML output of page and pass it to the reponse object.

The module makes use of Html Page Crawler in order to do pre-processing on the node, the details about which I will be posting in my next blog. For the next week I have planned to complete configuration setting provided for the printer friendly version of module and also providing configuration tabs for other plugins.

The progress of module develpoment can be viewed over <a href="https://github.com/zealfire/printable" style="text-decoration:none;" target="_blank">here</a>. 