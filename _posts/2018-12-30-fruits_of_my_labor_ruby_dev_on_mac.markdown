---
layout: post
title:      "Fruits of my Labor: Ruby Dev on Mac"
date:       2018-12-31 00:59:49 +0000
permalink:  fruits_of_my_labor_ruby_dev_on_mac
---


Over the holidays as I desired to a) visit various and sundry family members and b) also get some coding done in my limited spare holiday time, it became clear that the intersection of these two projects required that I bring a different computer than the one I had been used to coding with. The clearly correct candidate was an old MacBook Pro that had been gathering dust after being replaced a few years ago. I had not had much experience with a Mac before, but it couldn't be that hard to switch over for some minor coding, could it?

I'll skip the sitcom episode that that previous sentence suggests. It really wasn't all that hard to get things going, all things considered, but there were of course many unexpected difficulties that were smoothed over by helpful people on the internet. I'd like to summarize my favorite Ruby Dev Setup On Mac advice in this post. Enjoy!

## Necessities:  How to get Ruby and necessary tools going
In theory, Ruby comes installed on macOS. However, a quick `ruby -v` returned a fairly old version of Ruby. Time to get a version manager rolling!
* The first step, which I initially missed, is to install [Xcode](http://developer.apple.com/xcode/). Xcode is a macOS IDE for various languages containing tools I needed for various steps along the way.

* Next, install the [Homebrew](https://brew.sh/) macOS package manager. They have a nice automatic installer script:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Homebrew allows for much quicker installation of other tools, including the next few:
* The bash-derived [zsh](http://www.zsh.org/) shell. Various ruby gems require the ability to send bash commands to the shell, and zsh is one solution which comes preinstalled on some macs. Check for it with:
```
$ which zsh
#-> Should output zsh's directory, e.g. '/bin/zsh'
```
If you instead receive `zsh not found`, install it with `brew install zsh`.
Then change the default shell to zsh with
```
$ chsh -s /bin/zsh # replace /bin/zsh with the correct directory, which can be found with 'which zsh'
```

* The Ruby installation manager [rbenv](https://github.com/rbenv/rbenv#readme) is what I chose to use to control what version(s) of Ruby are installed and defaulted. 
```
$ brew install rbenv
$ rbenv init
#-> further instruction given in the terminal
```
Once it's installed, get the list of Ruby versions with `rbenv install -l` and then `rbenv install` the most recent version (or whichever is desired). 

* Finally, I just needed some gems
```
gem install bundler pry rake nokogiri require_all terminal-table
```

## Specificities: My preferred coding environment tools 

* My current text editor of choice is [Atom](https://atom.io/), which follows the standard process of downloading the zip from the site, extracting it and moving the executable to the Applications folder. 
Within Atom I use the [linter-rubocop](https://atom.io/packages/linter-rubocop) and [vim-mode-plus](https://atom.io/packages/vim-mode-plus) plugins for ruby development.
The former has a short dependency stack:
```
$ gem install rubocop
$ apm install linter
$ apm install linter-rubocop
```

* [Oh-my-zsh](https://ohmyz.sh/): I only just started using zsh, but this seems like a neat tool for customizing the shell with various productivity plugins and colorful themes.

## Other Fun and Useful things (especially as a primarily PC user):

Turns out I wanted some mouse issue fixers:
* Scroll reverser since I don't have an Apple mouse and "natural" scroll just feels weird to me outside of a trackpad.
* Discrete Scroll, which fixes macOS trying to register smooth scrolling on a mouse wheels that are not at all designed for that.

Further, as a PC user, I have a strong allergy to iTunes. If you suffer from the same issue:
* [VLC](https://www.videolan.org/) is the gold standard FOSS media player. Its main page links to .dmg installers for macOS.

I hope this has been a helpful guide to you, or perhaps simply to future me. Happy coding!

### References
https://gist.github.com/mcls/3118518
https://gist.github.com/monicao/d372716cdfbb7e9cf692
https://www.codementor.io/akabiru/3-steps-set-up-ruby-environment-macos-6mavm7jrl
https://medium.com/@namangupta01/replacing-rvm-with-rbenv-in-os-x-9dea622bd639
https://www.codecademy.com/articles/ruby-setup

