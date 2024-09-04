### Get to know vi (vim)

#### a. create test.cpp

```
$ mkdir sample	
$ cd sample
$ vim test.cpp
```

check "man" page for more (```$ man mkdir```)

- mkdir (create a directory); cd (move to directory)

if using Cygwin, your files are mostly like under the following directory:

```
$ cd /cygdrive/c/cygwin64/home
```

#### b. basic commands:

```
+ insert text: 	Press "i"
+ delete text: 	Press "d"
+ find text:	Press "/" text
+ save file: 	Press esc ":w"
+ quit vim: 	Press esc ":q"
  ++ combine save and quit: ":wq"
+ undo: 	Press esc "u"
+ redo: 	Ctrl+r

```

####  c. others:

```
+ split panes (horizontal): 	":sp"
+ split panes (vertical): 	":vs"
+ open terminal (horizontal):	":term"
+ open terminal (vertical): 	":vert term"
+ move between panes:		ctrl+w "h" "j" "k" or "l"

and many others, search for vim shortcuts
```

