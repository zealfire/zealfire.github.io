---
layout: post
title: Week four and improving the code quality
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week four while work done in week three can be tracked over <a href="http://zealfire.github.io/Week-three-and-implementing-twig-template/">here</a>.

The week four of coding period has ended and most of the time was spent in doing code refactoring. This week I was mostly focused in completing the deliverables which I had proposed in the project's proposal. As proposed I was able to complete print module core along with print HTML module.

Though most of the code was completed in last week but it lacked efficiency and robustness so a lot of time was spent in refactoring. Many places where procedural calling of function was being done was replaced by Dependency injection, instead of doing preprocessing in the twig templates the code for same was moved to module file. One of the important change which was brought was to use JavaScript in place of jQuery. In Drupal 7 jQuery was included in the page by default  while rendering which means using JavaScript or jQuery didn't made any difference but in Drupal 8 since loading of jQuery has been made optional so using JavaScript for writing less complex scripts was the obviously the best choice. I must thanks to my mentors who did a thorough code review this week and helped me improved the quality of code.

In this week User Interface of module was also implemented. The UI is still incomplete because pdf generating version of module is still remaining which is the major task in coming weeks. Since pdf generation will involve using third party libraries like wkhmltopdf so I have started to generated pdf file using them without Drupal so that I may be able to understand there working.

This week something even more exciting happened, I managed to break my previous longest streak of seven days on GitHub. The present streak is of thirteen days and which I do not want to break any time soon.

The progress of module develpoment can be viewed over <a href="https://github.com/zealfire/printable" style="text-decoration:none;" target="_blank">here</a>. 
