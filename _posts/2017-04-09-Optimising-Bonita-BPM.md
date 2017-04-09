---
layout: post
title: Optimising Bonita BPM
---


<p>Recently the team with whom I work was assigned a task in which a business application was supposed to be built. After doing some research and after a lot of discussions we decided to use <a href="http://www.bonitasoft.com/">Bonita BPM.</a></p>

<p>Due to the intricacy of the task in hand and many more reasons (about which I may write in a different blog) we decided to use UI Designer feature available in Bonita BPM studio. As this post is not about why and how to use Bonita so I will delve directly into issues which I faced and possibly found a feasible solution to it.</p>

<p>Before I start, I would like to say thanks to team at <a href="http://www.bonitasoft.com/">BonitaSoft</a> for creating this wonderful software.</p>

<p>The UI designer allows us to create pages. These pages basically consist of widgets (both custom and few provided by Bonita). In these pages, we can add assets(javascript, images, and CSS) both at page and widget level. In my use case, the application which we had created was mostly making use of custom widgets. The count of such widgets was nearly fifty-five(55). The problem is not due to count of these widgets instead of the way in which these widgets are rendered in a page created by Bonita. A custom widget in Bonita majorly consists of a template which describes the HTML markup of the widget and a controller used to describe the widget logic. When these widgets are added to a page, Bonita BPM engine basically adds a source to these widgets in a script tag. To have a clear understanding how it is done in HTML please refer the below image.</p>

![before_optimization](https://cloud.githubusercontent.com/assets/5805013/24839166/207e3d5a-1d73-11e7-8ede-86c7b4c3e93d.png)

<p>So now if there are N number of custom widgets then there would be N number script tags which basically means N number of HTTP requests for a page to render. In a real world application, these many calls are certainly obnoxious and bad for user experience. So how to solve this problem ?</p>

<p>Obviously the solution was to concatenate these individual js files and then minify them. To perform this action we decided to use Grunt as we were already using it as a task runner and this is when Ilearnedt how to create a task in Grunt. <a href="https://gruntjs.com/">Grunt</a> is basically a task runner which is used to automatically perform  periodic tasks like concatenating and minifying files. So now what I did was created a task in grunt whose job was to concatenate these individual js files and minifying them, here is the <a href="https://gist.github.com/zealfire/270ef33cb6f7f89339c0cb0729e44c61">link</a> to part of my Gruntfile.js file which performs this task.</p>

<p>Task in grunt was ready and seemed to work perfectly only problem was how to use it with my python script. Since I have not mentioned about my script so explaining, the job of this script was to provide an unzipped version of the folder imported from UI designer with links to assets corrected in accordance with path to my main project directory.</p>

<p>Since now I had a CLI for executing Bonita related task in grunt and python script which allowed me to import application in my web page, so I decided to make a call to grunt task from my python script using call command in python. Please refer this <a href="https://gist.github.com/zealfire/15a3ad5b90f6ffa6724bf27e59da2d27">link</a> in order to understand working of python script. Now I have to simply run the script on the imported ZIP folder provided by Bonita and get an optimized version of the page. Please see below to have a look into the reduced number of HTTP requests.</p>

![after_optimisation](https://cloud.githubusercontent.com/assets/5805013/24839091/22c8b244-1d72-11e7-960d-709b0b41b14e.png)

<p> I know the above approach may not be the best way to solve this problem hence it would be great if other people can suggest changes or any other method which can be used to solve the problem. Thanks.</p>

P.S. I had created a similar task in Grunt for optimizing CSS files (refer link to grunt file present above), the present python script already calls this task when executed.

P.P.S. The above Grunt task and python script obviously can't be used in every scenario but I think they can easily be tweaked as per environment in order to make it work.