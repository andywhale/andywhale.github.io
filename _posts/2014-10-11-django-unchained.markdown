---
layout: post
title:  "Starting with Python"
date:   2014-08-07 06:40:00
categories: programming
thumbnail: http://www.tutorgrams.com/images/python.png
---

## Finally starting out

Last week I finally got the time & opportunity to start using Python in the workplace, and (as I knew I would be) I was an instant fan. 
I don't have time right now to go into too much detail but having gone through the basics of scripting with python, 
I wanted to try out Django (having heard great things from just about everyone I know who knows about such things) so I thought I'd just document the remarkably simple process on osx to get the ball rolling.

The Django docs explain the install process using pip, which is fine once you are aware of the easy_install python script:

  sudo easy_install pip
  
You can then use pip to get Django (at time of writing the latest stable release is 1.7):

  sudo pip install Django==1.7
  
The only note I would add here is that this will dependant on your permissions and when I ran it, I had to sudo the command.

One more step to verify the install ran correctly

  python
  >>> import django
  >>> print(django.get_version())
  1.7
  
And I was ready to begin :-)
