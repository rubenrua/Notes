EMACS
=====

![Moving CLI and emacs](imgs/moving_cli.png)

LINKS:
------
* https://www.gnu.org/software/emacs/
* https://melpa.org/#/
* http://www.masteringemacs.org
* http://www.blackhats.es/wordpress/?p=23
* http://web-mode.org/
* http://emacsredux.com/
* https://github.com/capitaomorte/yasnippet
* http://wikemacs.org/index.php/Main_Page
* http://emacsrocks.com
* http://www.saltycrane.com/blog/2008/11/emacs-notes/
* http://overtone.github.io/emacs-live/doc-shortcuts.html
* http://spacemacs.org
* http://emacs.sexy
* https://cestlaz.github.io/stories/emacs/ and https://www.youtube.com/watch?v=49kBWM3RQQ8&list=PL9KxKa8NpFxIcNQa9js7dQQIHc81b0-Xg
* https://github.com/susam/emfy
* https://www2.lib.uchicago.edu/keith/emacs/

PACKAGES:
----------
* auto-comple: http://auto-complete.org/
* dumb-jump: https://github.com/jacktasia/dumb-jump/blob/master/README.md
* ido: (part of Emacs starting with release 22)
* Ivy, Counsel, Swiper: https://github.com/abo-abo/swiper
* helm: https://github.com/emacs-helm/helm
* magic: https://github.com/magit/magit
* projectile: https://github.com/bbatsov/projectile
* deadgrep: https://github.com/Wilfred/deadgrep

COMMANDS:
-----------
* C-h k describe-key - Describe which function a specific shortcut will evoke
* C-h f describe-function - Show docstring for a given function
* M-x execute-extended-command - Run a command by name.
* C-u M-! - Insert the output of shell command into emacs buffer
* C-g keyboard-quit - Cancel a command or dialog.
* M-/ dabbrev-expand - Expand previous word "dynamically".
* M-% query-replace - Interactive replace.
* C-s C-w C-s: (isearch) Select the (rest of the) word the TextCursor is on as the search string.
* find-name-dired: Search DIR recursively for files matching the globbing pattern
* find-dired: Run `find` and go into Dired mode on a buffer of the output.
* re-builder: Construct a regexp interactively.
* list-matching-lines (this is alias to occur)
* delete-matching-lines (this is alias to flush-lines)
* delete-non-matching-lines (this is alias to keep-lines)
* delete-duplicate-lines (Emacs 24.4) delete duplicated lines in text selection.
* package-list-packages: Fetch and display the list of available packages.
* whitespace-cleanup: Cleanup some blank problems in all buffer or at region.
* kmacro-insert-counter: Generate a secuente `C-x ( C-x C-k TAB . RET C-x )`
* global-display-line-numbers-mode or global-linum-mode: Useful for remote pair programing.
* imenu

EMACS FILE:
------------
https://github.com/rubenrua/dotfiles/blob/master/.emacs.d/init.el
