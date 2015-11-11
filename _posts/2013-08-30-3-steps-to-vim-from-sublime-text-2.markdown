---
layout: post
title: "3 steps to Vim from Sublime Text 2"
date: 2013-08-30 16:05
comments: true
categories:
---
I've been using Sublime Text 2 since quite a while now and really enjoy spending my most of the time playing around code with it. Since I've a PHP background (where I used to code on Netbeans) I was not motivated to use use on Terminal based editors. However, I gave a try to switch to Vim few months back but the situation was too much demanding at that time. I was learning couple of other new technologies where I didn't wanted them to suffer/compromise and avoided one more constrain on my brain to use Vim. <!-- more --> So, I stood beside Sublime Text 2 and it continued to be my IDE in that struggling period. Until recently, I came across [this great article](http://yehudakatz.com/2010/07/29/everyone-who-tried-to-convince-me-to-use-vim-was-wrong/) by [Yehuda Katz](https://twitter.com/wycats) which convinced me to give Vim another good try.

This is the basic setup I did to get started using Vim (on MacOSX)

### Setting up MacVim

* Install macvim using homebrew.
```
brew install macvim
```

* After installing macvim, I installed [janus-bootstrap](https://github.com/carlhuda/janus) which automatically installs and configures required plugins.
```
curl -Lo- https://bit.ly/janus-bootstrap | bash
```
* (Optional) Setting up a nice colorscheme is important. You should checkout [solarized](http://ethanschoonover.com/solarized) it has elegant colors which makes me feel nice while working. Fortunately, Janus has solarized built-in I just activated it. (BTW, my iTerm2 also has this same colorscheme)
```
echo 'color solarized'  >> ~/.vimrc.after
```

* Square has open sourced their in house vim configuration more info [here](http://corner.squareup.com/2013/08/fly-vim-first-class.html)

**Bingo!** I'm done with configuring vim with all the essential plugins out there within 3 steps. But, Not to forget Vim is not done until you know some required shortcuts. I've compiled the list for my quick reference. Ofcourse, They're available on the internet too.

### List of Not to forget Vim Shortcuts
* `:q!` quits the file and discard the changes.
* `:wq` saves changes and quits the current file.
* `\n` toggles the nerdTree on the left hand side.
* `\ew` or `:e <filename>` opens the file in current buffer.
* `\es` or `:sp <filename>` opens the file in horizontal split pane.
* `\ev` or `:vsp <filename>` opens the file in vertical split pane.
* `\et` or `:tabe <filename>` opens the file in new tab.
* `ctrl/cmd + T` opens a fuzzy finder in the root of the project (Sublime Text 2 has this feature too.)
* `gt` and `gT` to change tabs.
* `ctrl+w w` will move the cursor in multiple split pane (if there are).

### Concluding
I'm making myself comfortable in Vim and hopefully this will be a successful attemp. If you're sailing on same ship I would love to hear from you.

_P.S: I'll keep on updating the Shortcuts as I stumble upon them._
