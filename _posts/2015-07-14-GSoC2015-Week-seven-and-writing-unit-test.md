---
layout: post
title: GSoC2015 Week seven and writing some unit test
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week seven while work done in week six can be tracked over <a href="http://zealfire.github.io/GSoC2015-Week-six-and-working-with-PDF-libraries/">here</a>.

Last week I managed to finish work on mPDF and TCPDF generator and also most of the requirements for the pdf sub module were completed. So this week I started writing some unit test for the module. Writing tests for the module was a totally new experience for me because earlier the tests which I had written were mostly for the issues on drupal.org hence they were not that much complicated.

Ofcourse before starting to write some unit tests I tried to understand the concept by going through several resources but the best material is present over <a href="https://jtreminio.com/2013/03/unit-testing-tutorial-part-4-mock-objects-stub-methods-dependency-injection/">here</a> in my opinion so any one willing to learn the concept of unit testing may refer to same. Going through the unit test present in module residing within the core will also help. Refer to this <a href="https://www.drupal.org/node/2116263">link</a> if you want to learn how to run them.

Currently it is one of the issues of the core in Drupal 8 that the unit test present within a module residing inside the custom folder will not be identified by this command <strong>./vendor/bin/phpunit/phpunit/phpunit --list-groups</strong>. The problem lies inside the phpunit.xml.dist file present within the core. If you change the line which says <strong>../modules/custom/tests/src/Unit</strong> to <strong>../modules/custom/*/tests/src/Unit</strong> then your problem will be solved and unit test written for your module will be identified by the core.

Most of the concept and knowledge required for writing unit test can be obtained through above links hence I do not intend to write about them but some code for which I had to do some additional search I would like to mention about them below:

Mock object which support chaining methods:

<code>$routematch = $this->getMockBuilder('Drupal\Core\Routing\CurrentRouteMatch')<br/>
      &nbsp;&nbsp;->disableOriginalConstructor()<br/>
      &nbsp;&nbsp;->setMethods(array('getMasterRouteMatch', 'getParameter'))<br/>
      &nbsp;&nbsp;->getMock();<br/>
    $routematch->expects($this->exactly(2))<br/>
    &nbsp;&nbsp;->method('getMasterRouteMatch')<br/>
    &nbsp;&nbsp;->will($this->returnSelf());<br/>
    $routematch->expects($this->exactly(2))<br/>
    &nbsp;&nbsp;->method('getParameter')<br/>
    &nbsp;&nbsp;->will($this->returnValue($this->getMock('Drupal\Core\Entity\EntityInterface')));</code> 

Disabling original constructor of class while calling them:

<code>$entity_definition = $this->getMockBuilder('Drupal\Core\Entity\EntityType')<br/>
      &nbsp;&nbsp;->disableOriginalConstructor()<br/>
      &nbsp;&nbsp;->getMock();</code>

I would recommend anyone willing to learn more about this code refer to this <a href="https://github.com/zealfire/printable/tree/master/tests/src/Unit">link</a> where unit tests for printable module are being actively written. Next week I will be writing some more unit tests and then try to wrap up PDF sub module.

Some progress of PDF part of  module can be viewed over <a href="https://github.com/zealfire/pdf_api" style="text-decoration:none;" target="_blank">here</a> and remaining over <a href="https://github.com/zealfire/printable">here</a>.
