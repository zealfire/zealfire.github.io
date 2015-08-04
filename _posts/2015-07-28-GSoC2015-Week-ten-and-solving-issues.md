---
layout: post
title: GSoC2015 Week ten and solving issues
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week ten while work done in week nine can be tracked over <a href="http://zealfire.github.io/GSoC2015-Week-nine-and-adding-another-PDF-libraries/">here</a>.

This week I mainly worked on the issues raised by the mentors and also implemented some more functional tests. The issues related to pdf (api) module can be seen over <a href="https://github.com/zealfire/pdf_api/pull/7">here</a> while issues related to printable modules can be seen over <a href="https://github.com/zealfire/printable/pull/19">here</a>. One of the interesting task was to make the option to configure binary file of wkhtmltopdf library available as a field in the PDF configuration form.

Since the field to configure binary file of library should only be shown to user if wkhtmltopdf class is present in the drupal environment hence I am made use of <code>ClassLoader::classExists();</code> to check presence of library and then accordingly making the field available. So my final code looks something like this:

<code>$wkhtmltopdf_present = ClassLoader::classExists('mikehaertl\wkhtmlto\Pdf');
      
      if ($wkhtmltopdf_present && $pdf_tool == 'wkhtmltopdf')

        $form["settings"]['path_to_binary'] = array(

        '#type' => 'textfield',

        '#title' => $this->t('Path to binary file'),

        '#default_value' => $this->config('printable.settings')->get('path_to_binary'),

        '#description' => $this->t("Enter the path to binary file for wkhtmltopdf over here."),

       );
</code> 

Another way to implement this could have been by installing library module and then making use of <code> libraries_get_path()</code> function, the reason this method was not preferred because currently library module for Drupal 8 is still in development phase and also it is not sure where the installed external libraries for the modules would be kept. In Drupal 7 external libraries were kept in libraries folder but this may change for Drupal 8 in future.

Details about other issues which I managed to solve this week can be seen in the recent commits which I have made over <a href="https://github.com/zealfire/printable/commits/master">here</a>. This week I also managed to write functional tests for checking presence of links in the node view and check configuration form of PDF, these can be seen over <a href="https://github.com/zealfire/printable/tree/master/src/Tests">here</a>.

Some progress of PDF part of  module can be viewed over <a href="https://github.com/zealfire/pdf_api" style="text-decoration:none;" target="_blank">here</a> and remaining over <a href="https://github.com/zealfire/printable">here</a>.
