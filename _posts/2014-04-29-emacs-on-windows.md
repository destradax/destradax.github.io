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

3. Create the folder *plugins* inside *.emacs.d*.  

4. Emacs' *load-path* variable specifies the load path.  
   Check it with `C-h v load-path`.

5. Add regedit Key [HKEY_CLASSES_ROOT/*/shell/Edit with Emacs/command] with the default value `"C:\emacs\bin\runemacs.exe" %1`

6. Add a shortcut to `C:\emacs\bin\runemacs.exe` called `emacs`, inside `C:\Windows`. Make sure that it says "Start in: `C:\users\destradaa`"

4. [Markdown mode](http://jblevins.org/projects/markdown-mode/). Download [markdown-mode.el](http://jblevins.org/projects/markdown-mode/markdown-mode.el) and put it inside `.emacs.d/plugins/`.

#Comparison between Emacs, Sublime Text 2 and Notepad++#


## Autocomplete

1. Emacs
   Does not come built-in.
   Need to install [Auto Complete Mode](http://cx4a.org/software/auto-complete/)
   Supports dictionaries.
   Supports completions from other open buffers.
2. Sublime Text 2
   Comes built-in. Does not support completions from other open files.
3. Notepad++
   Comes built-in. Does not support completions from other open files.

## Open folder

1. Emacs
2. Sublime Text 2
3. Notepad++

## Package Manager

1. Emacs
   Comes built-in.
2. Sublime Text 2
3. Notepad++
   Comes built-in.
		
## Go To Anything

1. Emacs
2. Sublime Text 2
3. Notepad++

## Markdown

## Snippets
