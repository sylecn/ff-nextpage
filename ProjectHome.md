When reading online documents or novels, I usually use SPC to scroll page. But SPC doesn't go to next page automatically. This addon rebinds SPC key so that it scroll page when there is more on the page, it go to next page when at the bottom of a page. You can also use n key anytime directly to go to next page.

Currently English, Chinese and German web pages are supported.

To install this add-on, please visit https://addons.mozilla.org/addon/nextpage/

nextpage allows you to bind keys to some nextpage related functions, here is the default key-bindings:

  * SPC scroll up/next page
  * n next page
  * p history back

Here is the real code for this default binding:
<pre>
(bind "SPC" 'nextpage-maybe)<br>
(bind "n" 'nextpage)<br>
(bind "p" 'history-back)<br>
</pre>

You can disable/overwrite built-in bindings and define your own bindings easily. Read the built-in help document with the installed add-on for more information. Click help button in add-on preferences. To get a general idea on writing the config file, you can also read [ConfigFile](ConfigFile.md).

This add-on is only 36K zipped.

# BUG Report #
If you found a problem and would like to get it fixed, please report it here:
http://code.google.com/p/ff-nextpage/issues/list