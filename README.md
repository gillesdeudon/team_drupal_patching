# team_drupal_patching
Repository dedicated for Drupal patch produce in team.

The project contains a copy of Drupal dev version that allows our team to collaborate on patches.

In this repository we are working to provide a fallback that uses pcre without unicode support, as per this issue
https://www.drupal.org/project/drupal/issues/1657886, this issue provides a patch, already applied on this repository.

The changes needed are included on the file file.module and include the functions:


// Wraps on preg_replace_callback() and update the regex pattern to work without unicode support.
function _filter_preg_replace_callback($pattern, $callback, $text) {}:

// Detect if the pcre library is compiled with unicode support.
function _drupal_pcre_with_unicode() {}

// Returns all 'L' Unicode character classes (letters).
function _filter_preg_class_letters() {}

// Matches all 'N' Unicode character classes (numbers).
function _filter_preg_class_numbers() {}

// Matches all 'M' Unicode character intended to be combined with another characters (marks).
function _filter_preg_class_mark() {}


To test the functionality, deploy the site and install it. Then create some content and create a node with and url in the body.
