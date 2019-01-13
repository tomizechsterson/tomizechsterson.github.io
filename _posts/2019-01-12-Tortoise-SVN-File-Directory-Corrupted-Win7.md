---
layout: post
title: "Tortoise SVN - The file or directory is corrupted and unreadable in Windows 7"
tags: [windows, 7, tortoise, svn, file, directory, corrupted, win7]
---

This is an old post I made way back on 2/20/2010 that I'm bringing here to further test and to keep everything in one place. If you want the original, it should still be [here](https://tomizechsterson.blogspot.com/2010/02/tortoise-svn-file-or-directory-is.html).

I figured a good first blog would be something that I've discovered with Windows 7 Ultimate 64-bit and Tortoise SVN 1.6.7 Build 18415 - 64 Bit with Subversion 1.6.9. For a while, I had the most difficult time doing commits and updates with my projects on my Windows 7 machine because SVN would constantly scream about the "file or directory" being "corrupted and unreadable". Well, after numerous Google searches I came across this advice that seemed to help most people:

Just disable the indexing service on the folder and the problem goes away via the properties dialog accessed by right-clicking the folder.

Naturally, that helped pretty much everyone. Except for me.. I double and triple checked the folder options, repeatedly going through the step-by-step instructions given by a couple different people and verified that the "Allow files in this folder to have contents indexed in addition to file properties" check box was unchecked. When that didn't work, I resorted to the old tried and true restart. This prompted a chkdsk just before Windows started back up that found no issues, and it did fix the problem. Once. Any subsequent SVN actions, be it a commit, branch, or update would result in the same "The file or directory is corrupted and unreadable" error again. I could always restart to allow one more SVN operation, but I finally got fed up with that and finding the same advice with my Google searches so I started digging around Windows to see what I could come up with. Turns out, I hit a gold mine (at least for my case).

Here's what I did to fix the problem for me:
1. Click the start menu button and then click in the search box.
2. Type in "windows index"
3. This should bring up something called "Indexing Options", which can also be found in the control panel if you change the View by to 'Large Icons' or 'Small Icons'. I don't believe it's in one of the categories for some reason, though I could be wrong about that. Either way, click on Indexing Options.
4. When the Indexing Options dialog comes up, click on the Modify button. This will bring up the "Indexed Locations" dialog. Here, you'll see a tree view of locations which should include your hard drive(s).
5. Expand the desired hard drive, down to the root folder of the SVN working directory you're interested in, and make sure the check box is unchecked. This is where I found a check mark in the box for my root working directories.

Note that the check box for the root of the hard drive itself might not be checked, even though there may be checked boxes within it. This was the case for me, so don't assume that all check boxes will be clear just because the one for the hard drive is not checked. After I ensured that my problem folders were taken care of here and hit OK, my problem went away. I've been happily updating and committing changes to my projects without any more problems so far. So, I hope this helps anyone out there who might still be suffering from this problem who didn't have their problem fixed by the more straight-forward method (which really should be all it takes).

This information originally came from another blog where I left a comment, but wanted to give this information a place that's a bit more permanent, so I put it up on Blogspot, and now it's here.