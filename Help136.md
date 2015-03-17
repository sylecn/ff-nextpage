# Help #
When reading online documents or novels, I usually use SPC to scroll page. But SPC doesn't go to next page automatically. This add-on rebinds SPC key so that it scrolls page when there is more on the page, it goes to next page when you are at the bottom of a page. You can also press n key anytime to go to next page directly.

nextpage is [free software](http://www.gnu.org/philosophy/free-sw.html) released under GPLv3. The source code is hosted at [github](http://github.com/sylecn/ff_nextpage/).

nextpage tries hard to not get in your way. If you find nextpage breaks your blog admin panel, some online registration form, or any kind of cool web application, please report a bug.

Currently English, Chinese and German web pages are supported.

nextpage allows you to bind keys to some nextpage related functions, here is the default key-bindings:

  * SPC scroll up/next page
  * n next page
  * p history back

Here is the real code for this default binding:
```
(bind "SPC" 'nextpage-maybe)
(bind "n" 'nextpage)
(bind "p" 'history-back)
```

You can disable/overwrite built-in bindings and define your own bindings easily. Read the built-in help document with the installed add-on for more information. Click help button in add-on preferences. To get a general idea on writing the config file, you can also read [ConfigFile](ConfigFile.md).

This add-on is only 36K zipped.

# BUG Report #
If you found a problem and would like to get it fixed, please report it here:
http://code.google.com/p/ff-nextpage/issues/list