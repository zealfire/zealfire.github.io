---
layout: post
title: GSoC2015 Week eleven and testing PDF
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week eleven while work done in week ten can be tracked over <a href="http://zealfire.github.io/GSoC2015-Week-ten-and-solving-issues/">here</a>.

Since most of the important expected features in the PDF sub module were completed last week therefore this week as asked by the mentors, time was spent in proof testing the working of the module. The way it was supposed to be done was very interesting and unique for me because I was asked to create a PDF based on the material used previously by the mentors while dealing with a client. The demo PDF can be seen over <a href="http://cdn2.us.yokogawa.com/GS48C11Z05-00E-N_004_DI-511-05.pdf">here</a>.

The PDF was supposed to be created keeping in the mind that it should be comparable to a document which can be used in the daily office work. The content of the PDF was supposed to contain text of various sizes and color, images of various formats, tables and HTML supported header and footer. Also one more thing was supposed to be kept in mind while making the PDF that as a user of the module I was not suppose to make too many changes in the present code while trying to implement advance features. This was important from real world perspective too because in daily usage too as a user we expect the module to provide us all the functionalities and not needing to interfere with the original code.

The expected PDF was created without making any advance changes in the code of the module hence assuring the fact that the module at present can be used in its development release. The created PDF can be seen over <a href="https://github.com/zealfire/printable/blob/master/testPDF.pdf">here</a>. Since a modified footer was expected to used in the demo PDF hence I made a small change in the code where I am calling PDF generator object from the <code>printable_pdf</code> module. The introduced code is as follow:

<code>$this->pdfGenerator->getObject()->SetFooter('This is a footer on left side||' . 'This is a footer on right side');</code>

This week I also added another important test in the module which tests the rendering of PDF. The test can be seen over <a href="https://github.com/zealfire/printable/blob/master/src/Tests/PrintablePdfTest.php">here</a>. The way this test was implemented was totally new to me because this test has an external dependency on PDF parser library whose job is to convert PDF to text. So the test firstly saves the PDF in a particular location then with help of this parser converts it to text. The text now is used to create a new node where the content is asserted for main body of PDF along with header and footer. The way PDF parser extracts the text can be seen below in the code and remaining portion of test can be viewed via the above link.

<code>
    $this->drupalGet('printable/pdf/node/' . $node->id());


    $parser = new \Smalot\PdfParser\Parser();
    $pdf    = $parser->parseFile('modules/custom/printable/src/Tests/testPDF.pdf');
    $text = $pdf->getText();
</code>

Next week more focus will be on improving the quality of current code and improving the code standard by running the code sniffer. Some progress of PDF part of  module can be viewed over <a href="https://github.com/zealfire/pdf_api" style="text-decoration:none;" target="_blank">here</a> and remaining over <a href="https://github.com/zealfire/printable">here</a>.
