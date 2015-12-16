---
title: Open Source
date: 2015-12-10 14:44 UTC
tags: coding, open source
---
Contributing to open source is intimidating, but it is a key step on the path to coding rockstardom. I was lucky enough to be able to attend a meetup group where a pack of newbs went through the process together with some mentors walking around. But it actually wasn't that hard, and my team didn't even need the help of a mentor...except for having them select a series of beginner-appropriate projects.

#Finding a project to contribute to

This is the hardest part. But it's actually not that hard. The good news is that in the pay-it-forward atmosphere of the open source community, more and more maintainers of open source projects are intentionally leaving some easy stuff for beginners to fix.  Here a a few things to try:

 - ###Search Gihub.
 Paste the following into the search bar at Github: `language:ruby state:open label:beginner is:public`. The meaning is pretty self-explanitory. Make sure you change the `language` to the language you are looking for. I just did this and got 95 results. 123 result for JavaScript, if that's your poison.

 - ###Documentation:
 Absolutely noting wrong with contributing documentation. It is a appreciated. If you've struggles with getting something installed or working on your particular set up, and were able to eventually get it going, write something up and add it to a pull request.
- ###Let the cops to the work.
Run a linter like Rubocop on a repo, and it will tell you things to fix. Rubocop scans for bits of code that are suspiciously bug-like or that don't adhere to good coding style. Things like lines being more than 80 characters long, trailing whitespace, two blank lines when one will do. Ridiculously easy stuff to fix.
- ###CodeClimate score:
Similar to the above is CodeClimate. Look for repos with a CodeClimate badge. This will show a score between 0 and 4. Anyone would want a higher score. Run CodeClimate on a repo, and it will come back with a list of issues to fix. If you're able to fix one of them, submit the pull request, and it gets accepted, the repos CodeClimate score will go up, which will make the maintainer happy.


