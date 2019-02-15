+++
date = 2019-02-15
weight = 0
title = "Problems With Electron"
+++

First things first, this is my first blog post, so when you find errors or have any feedback that you want to tell me, reach out to me on [twitter](https://twitter.com/ntgg_) or on [reddit](https://www.reddit.com/user/superlizerd).

There are many problems with Electron. It is bloated, memory hungry, and generally slower than a *well programed* application. I've seen this [article](https://josephg.com/blog/electron-is-flash-for-the-desktop/) show up on /r/programming a few times that claims electron is flash for desktop. I would say that the comparason is very good, but the article only seemed to acknowledge the bad parts of flash.

# The Good

My introduction to the internet was playing flash games at school or at my friends house. Playing games on Newgrounds, Nitrome, or Miniclip shaped my childhood interests, and were only possible at the time due to Flash. Flash has tons of problems, chronicled on plenty of other places on the internet, but you can't deny that it helped many creative and talented people create great content for many to consume. This isn't a new idea, there is a [great video](https://www.youtube.com/watch?v=uhvey_FjtXA) by NakeyJakey saying basically the same thing, and I'm sure the many people in the game and animation industries that got their start due to flash would say the same. It was "easy" to start making things in flash, and even easier to distribute them to an audience. Flash was important to the development of the modern internet, but it has too many issues to continue use (outside of legacy support), and the internet is better off since it's death. It was replaced by more performance effective and safe tools.

At this point it should be pretty obvious what my point is. Electron mirrors many of the thing that flash did well, making cross platform desktop apps (relatively) easy to make, especially for already existing web apps.

# The Bad and The Ugly

Electron is in a similar boat. It is bloated and slow. It is, in many cases, the easy way out of making a good desktop application, especially for existing web apps. The issue is that the performance of these applications are horrible. To show this, I ran a few tests to put this in perspective.

## Text Editors

For the first test, I used this website project as a benchmark. As VSCode is currently my primary text editor it has the most plugins so to make it fair I removed anything I didn't have a duplicate for in other text editors. I excluded adding plugins to Visual Studio, but that has a lot of the functionally built in, and I used a c++ project of a similar size to compare it to, so take the results from that with a grain of salt. In fact, take all of these results with a grain of salt, because it isn't a scientific study, just some quick testing. The plugins I used included syntax highlighting, a language server, and some sort of autocomplete. Most of these wouldn't do anything in a project that only has markdown, css, and html files, but I kept them enabled so I didn't have to rummage through my vimrc.

| Program            |     Memory |
| ------------------ | ---------: |
| Visual Studio Code | 1,102.5 MB |
| Visual Studio      |   315.1 MB |
| Oni                |   181.4 MB |
| Sublime Text 3     |    99.8 MB |
| nvim-qt            |    62.2 MB |

As you can see, in this test Sublime Text 3 used 11× less memory than Visual Studio Code. The same files were open. While VSCode in this situation does do a little bit more than Sublime Text, it does not require 11× the memory to do so. What is VSCode doing with all the extra memory? Visual Studio was able to run it's full service for just 1/3 the memory of VSCode. Oni, an electron based ui system for neovim, almost tripled the memory usage of the native nvim-qt. Sublime Text, a text editor that does much more than Oni, used just over 1/2 the memory Oni did.

## Other Applications

This test I just tested some other applications to put these results in more perspective. All of the apps are being used as intended for like 5 minutes before I looked at task manager, in an attempt to make it even for programs that maybe have a longer startup time.

| Program                           |   Memory |
| --------------------------------- | -------: |
| Firefox Start Page                | 649.4 MB |
| Spotify (not electron, but close) | 290.5 MB |
| Discord                           | 214.4 MB |
| VirtualBox with Ubuntu Bionic     | 151.6 MB |
| pico-8                            |  45.2 MB |
| Foobar 2000                       |  15.0 MB |

This is where it gets ridiculous for me. I am able to run an entire OS running another IDE (Eclipse), inside a virtual machine for a little over 2/3 the memory cost of an **idling text chat program**. That is completely ridiculous. Major props to the VirtualBox team. I don't think that you can look at these charts and reasonably conclude that electron is good, efficient service. While the issue is not all on Electron, I really don't think you can say the memory usage is anywhere close to reasonable.

# In Conclusion

Just because electron is the easier way doesn't mean that we shouldn't attempt to at least get somewhat close to the more efficient way. I realise there are many advantages to electron, but they don't even come close to outweighing the massive hits on memory usage that electron takes. If you are making an app, try to make it without electron. If you are one of the multi-million dollar companies that are making these horribly inefficient apps, maybe invest in making a better, native implementation. You can do better.