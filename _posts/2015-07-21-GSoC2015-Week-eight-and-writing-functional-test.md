---
layout: post
title: GSoC2015 Week eight and writing some functional test
---

This post is about the progress which I have made while porting print module to Drupal 8 as part of GSoC 2015. Below is an excerpts about the work done in week eight while work done in week seven can be tracked over <a href="http://zealfire.github.io/GSoC2015-Week-seven-and-writing-unit-test/">here</a>.

This week again most of the time was invested writing some more tests for the module (my previous attempts at writing unit tests can be seen over <a href="http://zealfire.github.io/GSoC2015-Week-seven-and-writing-unit-test/">here</a>). But this time I learned to write some functional test. In Drupal if you want to write functional test then Simpletest is the required testing framework. We don't need to worry about installation of Simpletest framework because since the release of  Drupal 7 it comes already with the core and in Drupal 8 since it is not enabled by itself so you need to enable it by heading to <code>/admin/config/development/testing</code>.

Running the functional tests in Drupal 8 is very easy and they can be executed using both command line and user interface. All the tests written for the module must be kept within the <code>src/Tests</code> folder of the module so that Drupal recognizes your test. Though a very good explanation about functional tests in Drupal 8 is present in drupal.org over <a href="https://api.drupal.org/api/drupal/core!modules!system!core.api.php/group/testing/8">here</a> still I would suggest you to refer to this <a href="http://www.sitepoint.com/automated-testing-drupal-8-modules/">link</a> for seeing some really good tests being written for a sample module.

Most of the knowledge required to write functional test are present in above posted links but I would like to share with a code which I wrote to test the existence of printable version of nodes. Below written code is only portion of test which I had written under the class name <a href="https://github.com/zealfire/printable/blob/master/src/Tests/PrintableNodeTest.php"><code>PrintableNodeTest</code></a>. I have extended the <code>NodeTestBase</code> class present in the core for this particular test in order to reuse the preprocessing work done by the latter class. 

<code>
public function testCustomPageExists() {

      $node_type_storage = \Drupal::entityManager()->getStorage('node_type');

      // Test /node/add page with only one content type
      $node_type_storage->load('article')->delete();
      $this->drupalGet('node/add');
      $this->assertResponse(200);
      $this->assertUrl('node/add/page');
      // Create a node.
      $edit = array();
      $edit['title[0][value]'] = $this->randomMachineName(8);
      $edit['body[0][value]'] = $this->randomMachineName(16);
      $this->drupalPostForm('node/add/page', $edit, t('Save'));

      // Check that the Basic page has been created.
      $this->assertRaw(t('!post %title has been created.', array('!post' => 'Basic page', '%title' => $edit['title[0][value]'])), 'Basic page created.');

      // Check that the node exists in the database.
      $node = $this->drupalGetNodeByTitle($edit['title[0][value]']);
      $this->assertTrue($node, 'Node found in database.');

      // Verify that pages do not show submitted information by default.
      $this->drupalGet('node/' . $node->id());
      $this->assertResponse(200);

      $this->drupalGet('printable/print/node/' . $node->id());
      $this->assertResponse(200);
      $this->assertRaw($edit['title[0][value]'], 'Title discovered successfully in the printable page');
      $this->assertRaw($edit['body[0][value]'], 'Body discovered successfully in the printable page');
  }
</code> 

I hope comments present in the code are sufficient to understand the working of code but still anyone willing to learn more about it may refer to this <a href="https://github.com/zealfire/printable/tree/master/src/Tests">link</a> where functional tests for the module are being currently written. Next week I will be writing some more functional tests and then proceed to adding dompdf library to PDF sub module.

Some progress of PDF part of  module can be viewed over <a href="https://github.com/zealfire/pdf_api" style="text-decoration:none;" target="_blank">here</a> and remaining over <a href="https://github.com/zealfire/printable">here</a>.
