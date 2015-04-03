---
layout: post
title: "From Drupal To Jekyll"
date: 2015-03-28 10:50
---

Earlier this month I created the post [Previous Content Restored]({% post_url 2015-03-07-previous-content-restore %}) after I had finally got my existing content back online.  Since then I've not done anything besides read about Jekyll online.

Before I started to use it normally I wanted to summarise what it took to transfer my website from using [Drupal](https://www.drupal.org/) to [Jekyll](http://jekyllrb.com/).

I certainly over complicated the process because I worry too much about various things.  You can read about why I transferred from Drupal in the post [Restoring My Website]({% post_url 2015-03-04-restoring-my-website %}).

Before I begin I want to add that my laptop is running Windows 8.1.  I've used versions of Linux on and off for long enough to be comfortable using a command line.

Here's a short summary of what I did to transfer my website:

1. Setup Ubuntu Server 14.04 using a Virtual Machine in [Virtual Box](https://www.virtualbox.org/)
2. Hosted my Druapl website in Ubuntu Server using a standard LAMP setup
	1. I used Ubuntu Server so I could easily [setup a LAMP server](https://help.ubuntu.com/community/Tasksel)
    1. Some minor tweaks were made in Drupal to hide some pages and remove active content 
3. [HTTrack Website Copier](https://www.httrack.com/) used to get HTML copy of Drupal website
4. [PHP DOMDocument](http://php.net/manual/en/class.domdocument.php) used to strip head, JS and other content
    1. [PHP Tidy](http://php.net/manual/en/book.tidy.php) used to output nicely formatted XHTML
5. Python library [Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/) used to transform the HTML further
6. [Notepad++](http://notepad-plus-plus.org/) & [Sublime Text 3](http://www.sublimetext.com/) using regex patterns to find and remove some content
7. Some manual updates made using a text editor
8. [phpMyAdmin](http://www.phpmyadmin.net) used to export node data from Drupal
9. Python used to convert standard HTML into HTML with Jekyll front matter and additional cleanup
10. [wget](http://manpages.ubuntu.com/manpages/lucid/man1/wget.1.html) on Ubuntu Desktop used to check for broken internal links
11. Final changes made manually with a text editor

Listed like that it seems like a lot of steps.  While the goal was to get setup in Jekyll I used this as an opportunity to play around with a few different methods of manipulating HTML content.  I worked on this on and off for a week or so.

Steps 1 to 4 where done on the Ubuntu Server VM.  Steps 5 to 7 were done on my laptop.  The data extract for step 7 was done in the Ubuntu Server VM but the data was processed on my laptop.  Steps 8 & 9 were done on my laptop.  Step 10 was on the Ubuntu Desktop VM though the data was checked on my laptop and finally step 11 was on my laptop.

At some point during this work I setup a Ubuntu Desktop VM in Virtual Box.  That's what I'm currently using to run and test Jekyll.  I could probably have downloaded a wget version for Windows but since I had Ubuntu available there was no point.  

Since I'm familiar with VirtualBox and Ubuntu I decided to run Jekyll like that rather than risk possible issues running on Windows while that is not [officially supported](http://jekyllrb.com/docs/installation/) and I'm not familiar with Ruby yet.

Basically this whole process took a copy of the content from the original Drupal website and prepared it for use in Jekyll.

Over the different methods I used to process HTML I think [Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/) using [Python](https://www.python.org/) was the easiest.  It did take me a couple of attempts at some points to figure out the correct options to avoid Unicode issues.  I eventually got it setup so all the content (including the Japanese characters) was correctly processed and saved.

Maybe one day I will extract some of the Python code and host that on GitHub.