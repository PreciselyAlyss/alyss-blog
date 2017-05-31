---
layout: post
title:  "Built a static blog site"
date:   2017-05-30 18:06:32 -0500
categories: projects
---
Late one night, possibly after too much cider, I bought okalyss.com. I've started giving technical meetup talks and the CFP submissions kept asking for a website URL. I felt lacking that I didn't have one, but I definitely knew of things to write about and how to deploy a blog. So I decided to put a custom blog built with Jekyll (a static site generator) on my new domain.

I did this in two parts. 

## Part One: Developer Environment for Windows 10

I have a Windows 10 laptop I drag around for gaming at friends but I've heard good things about being able to use bash, so I searched for "enabling bash on Windows 10". My developer environment at work is running macOS with [iTerm2][iterm], [Oh My Zsh][oh-my-zsh], and I like [Sublime Text 2][sublime-two] for my text editor. 

I couldn't use iTerm2 on a Windows machine so I jumped around various articles and guides until I found a good Windows 10 reccomendation. I found [Owen Williams's guide][guide] to fit. It included a new terminal recommendation and favored ruby development. My new terminal on Windows 10 is [Hyper][hyper] and I can still use Oh My Zsh.

## Part Two: Starting a Jekyll project and deploying it

In part one, I was able to get through the initial installation with Ruby and bundler. I had to step off the guided path by using [RubyInstaller][ruby-installer]. I already had bundler, so I was able to jump to the inital jekyll install command.

I was already in my target project directory, so in my terminal:

```
gem install jekyll
```

The next command on the [Jekyll's setup guide][setup] was `jekyll new blog`. This caught me up a bit. I expected the install to land inside my directory but, instead, it made a new subdirectory as `target/blog/`. My expectations were from using [Middleman][middleman] from a previous project. I opened up file explorer and dumped the `/blog/` contents into the parent directory. 

Next, a theme and support to use github pages. 

```
gem install jekyll-swiss github-pages
```

Okay, great. Now I want to see what it looks like:
```
bundle exec jekyll serve
```

Hmm...I'm getting an error `GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.`. A quick Google query tells me I can fix this by adding a new entry to my `_config.yml`:

```yaml
github: description
```

Now I can use `bundle exec jekyll build` or `bundle exec jekyll serve` without error. Once I commited my changes to github, I jumped into my settings and set my custom domain for github pages with the target directory as `master`. After updating my domain name's A records, I waited about an hour and my site was live. 


Check out the [Jekyll docs][jekyll-docs] for more info on how to setup your own site with Jekyll.

[iterm]: https://www.iterm2.com
[oh-my-zsh]: https://github.com/robbyrussell/oh-my-zsh
[sublime-two]: https://www.sublimetext.com/2
[guide]: https://char.gd/blog/2017/how-to-set-up-the-perfect-modern-dev-environment-on-windows
[hyper]: https://hyper.is/
[ruby-installer]: https://rubyinstaller.org/downloads/
[setup]: https://jekyllrb.com/docs/quickstart/
[middleman]: https://middlemanapp.com/
[jekyll-docs]: https://jekyllrb.com/docs/home
