---
layout: post
title: Week three and implementing twig template
---

The week three of coding period has ended and this time I learnt about something very new to me, Twig template. In Drupal 8 Twig has replaced PHPTemplate as default templating engine which meant that the theming of module had to be done from beginning.

Also since my module deals with creation of printer friendly version of nodes so it makes it even more important that theming should be paid more importance. The reference material present on drupal.org are good but still the things were not getting clear to me so I browsed more and more and finally found this small <a href="http://drewpull.drupalgardens.com/blog/drupal-8-twig-template-engine" target="_blank">blog </a>on Twig which helped me understand.

In the process of learning theming I learnt about concept of rendering in Drupal and most importantly about invalidating catching while rendering, I mainly used getListCacheTags() to serve my purpose. Also knowing the that I can use template_preprocess_module() to create temporary variables and then rendering them in my templates was very helpful.

In the present week I managed to develop a partial working prototype of module with not all but many configurations completed like links for printer friendly version are being shown in blocks as well as below the entities. Ofcourse the user can disable and re-enable these links. I have created view modes for the print version and hence generated core.entity_view_mode.$entity_type.$view_mode.yml file. I was impressed by the fact that I had to import configuration for this file becuase it was something very new to me.

Next week I will mainly be working on completing the configuration of module and try to rectify the problem which I have found in this week.

The progress of module develpoment can be viewed over <a href="https://github.com/zealfire/printable" style="text-decoration:none;" target="_blank">here</a>. 
