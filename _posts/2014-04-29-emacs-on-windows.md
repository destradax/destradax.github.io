---
layout: post
---

1. Download [Emacs](http://mirror.cedia.org.ec/gnu/emacs/windows/) and extract to C:\emacs
   You'll end up with something like:

	  	C:
	  	  |->emacs
	  		  |->bin
	  		  |->etc
	  		  |->info
	  		  |->leim
	  		  |->lisp
	  		  |->site-lisp

2. Set up the **HOME** environment variable. This is where your *.emacs*
   file and *.emacs.d* directory will go.

3. Create the folder *packages* inside *.emacs.d*.  

4. Emacs' *load-path* variable specifies the load path.  
   Check it with `C-h v load-path`.

5. Add regedit Key [HKEY\_CLASSES_ROOT/*/shell/Edit with Emacs/command] with the default value `"C:\emacs\bin\runemacs.exe" %1`

6. Add a shortcut to `C:\emacs\bin\runemacs.exe` called `emacs`, inside `C:\Windows`. Make sure that it says "Start in: `C:\users\destradaa`"

7. [Markdown mode](http://jblevins.org/projects/markdown-mode/): download [markdown-mode.el](http://jblevins.org/projects/markdown-mode/markdown-mode.el) and put it inside `.emacs.d/plugins/`.

8. [Auto complete mode](http://cx4a.org/software/auto-complete/): download the [zip](http://cx4a.org/pub/auto-complete/auto-complete-1.3.1.zip), extract it and `load-file` the file `etc/install.el`.

9. If you are behind a proxy, put this in your *.emacs* file:

	(setq url-proxy-services '(("no_proxy" . "localhost")
                           ("http" . "proxy.work.com:8080")))

10. Paste this in the scratchpad and do `eval-buffer`:

		(package-install 'helm)
		(package-install 'js2-mode)
		(package-install 'rainbow-mode)
		(package-install 'yasnippet)
		
