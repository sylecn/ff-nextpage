# Introduction #

In nextpage v1.3.6, a config file was added to allow users to bind keys to command as they wish. This document describes how it is implemented and how to use it. For latest/correct version of this document, always click the help button in nextpage add-on preferences. What this wiki document describes may not be available to your installed version of the add-on.

# About the Config File #

The config file is a text file. You may edit it in the nextpage Preferences window or in any text editor you like. You can get the config file path in Preferences window. If you edit it in Preferences window, click "Save & Reload" to make it persistent and active. If you edit it in external editor, save the file there, then click "Reload Only" to make the new config active.

By default, a built-in config is used. nextpage does not create a user config file. This works for users that do not want to config this add-on at all. The user config file will be created when you click "Save & Reload" in Preferences window. You may also use your text editor to create it manually, then click "Reload Only" to load the config file immediately.

The config file has a lisp-like syntax. Lines started with ; are comments and they are ignored by the parser. Thus to temporarily disable a command, just comment it by adding ";;" at the beginning of that line.

Each command must be put in a separate line, because I haven't implemented an sexp parser yet.

# Supported Commands #

`(bind KEY-NAME COMMAND-NAME)`
> Bind a key to a command. The syntax used to define KEY-NAME is shown in later section.

`(unbind-all)`
> Remove all previous bindings before this command, including built-in bindings.
> If you don't want to use any of the built-in key bindings, add this to the top of your user config file.

# Built-in config file #

This serves an example of how to write a config file.

<pre>
(bind "SPC" 'nextpage-maybe)<br>
(bind "n" 'nextpage)<br>
(bind "p" 'history-back)<br>
</pre>

//side note: google wiki has bad syntax highlighting for lisp. I used a pre tag to show code.

Keys are wrapped with double quotes, command is prefixed with single quote. This just mimic emacs `(global-set-key (kbd "C-c U") 'rename-uniquely)` key-bindings.

Here are some optional key bindings that is provided in older versions of nextpage. You may add them in your user config file if you like.

<pre>
(bind "1" 'history-back)<br>
(bind "2" 'nextpage)<br>
(bind "M-p" 'history-back)<br>
(bind "M-n" 'nextpage)<br>
</pre>

# Keys used in bind command #
A subset of Emacs key names can be used in bind. Here is a table to get you started.
| **Key Name** | **Meaning** |
|:-------------|:------------|
| a | key A |
| C-a | Ctrl-A |
| M-a | Alt-A |
| C-M-a | Ctrl-Alt-A |
| SPC | Space |
| `<f11>` | F11 |
| `<C-S-f11>` | Ctrl-Shift-F11 |
| `<left>` | Left Arrow |

Check the source code of this add-on to know exactly which keys are supported. <a href='http://code.google.com/p/ff-nextpage/issues/list'>Report a bug</a> if the key you want to use is not supported by nextpage.

Key names are case sensitive. Key names are typed with double quotes in bind command. e.g. "M-n".

If you have emacs installed, to known a key's key name (the string representation), start emacs and type C-h c, then type your key. The key name will be shown in minibuffer. Note that key sequence is not supported by nextpage. So you can't bind "C-x n" to nextpage command.

For more document, see emacs document <a href='http://www.gnu.org/software/emacs/manual/html_node/emacs/Keys.html#Keys'>Keys</a>, <a href='http://www.gnu.org/software/emacs/manual/html_node/emacs/Commands.html#Commands'>Commands</a> and <a href='http://www.gnu.org/software/emacs/manual/html_node/emacs/Key-Bindings.html#Key-Bindings'>Key Bindings</a>.

# Commands available in bind command #
Available commands:
| **Command** | **Meaning** |
|:------------|:------------|
|nextpage-maybe | scroll up / next page|
|nextpage| next page|
|history-back |go back one page in history|
|close-tab |close current tab|
|nil |do nothing|

Commands should be quoted in bind command. For command foo, use single quote form 'foo. Currently omitting the quote also works, but this may change if I choose to introduce a full lisp parser in the future.

About the nil command: You can disable a key-binding by binding the same key to nil. For example, `(bind "SPC" 'nil)` will disable the built-in Space binding.