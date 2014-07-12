# Mr. Poole - Dr. Jekyll's Butler

## Overview

Mr. Poole is an [Alfred.app](http://www.alfredapp.com) workflow for [Jekyll](http://jekyllrb.com) sites. He is Dr. Jekyll's butler and tries to take the drudgery out of running a static site. Mr. Poole will assist you by...
 
* creating, opening and publishing drafts of regular as well as link and video posts
* opening existing posts for editing
* opening existing pages for editing
* starting a local server with the site including drafts
* opening the site folder in Sublime Text for development plus the above
* deploying the site to your server with rsync
* tweeting about (new) posts

## The commands

### Draft commands

*New draft*: Add the title as an argument. It creates a new draft file in the *_drafts* folder of your Jekyll site, then adds a front matter template with the title and default values defined in the script. The filename is the lowercase, hyphenated version of the title.

*New link post draft*: Reads the URL, title and selection from the active Safari tab and creates a new linked-list style draft with the page title, date, external URL and the selection (as Markdown quote) filled in. Requires modified Jekyll templates (cf. below).

*New video post draft*: Reads the video ID, title and selection from a Youtube or Vimeo video page in Safari and creates a new video post draft with the page title, date, video ID and the selection (as Markdown quote) filled in. Requires modified Jekyll templates (cf. below).

*Open draft*: Returns all of your existing drafts sorted by modification date (newest first). Selected post will be opened.

*Publish draft*: Lets you choose an existing draft, adds the current date to the beginning of the filename and moves it to the *_posts* folder. Builds the site and deploys it to your remote server. Opens your site in the standard browser.

### Post commands

*Open post*: Returns a list of your existing posts in reverse chronological order and opens the selected post for editing.

*Tweet post*: Requires a page on your domain in the active window / tab of Safari. Reads the URL and the title and opens an editable tweet about the article. Requires [Tweetbot for Mac](http://tapbots.com/software/tweetbot/mac/).

### Page commands

*New page*: Takes a page name as an argument. Creates a markdown page file. The filename is the lowercase, hyphenated version of the title.. Fills in a template front matter with the title and default values defined in the script. It creates subfolders if given. Example: The argument `/resources/A list of my downloads/` will create the file `path/to/jekyll/resources/a-list-of-my-downloads.md`.

*Open page*: Returns a list of all .md files inside the Jekyll folder including subdirectories sorted by date of last modification, excluding only those in folders prefixed with an underscore such as `_posts` and `_drafts`. Opens selection for editing.

### Site management commands

*Deploy site*: Builds the site and uses rsync to deploy it to the remote server. Opens the URL in the browser.

*Serve site*: Builds the site with drafts, starts the local server and opens the URL. Regenerates the site when files are changed.

*Edit site*: Same as *Serve site*, but additionally opens the site folder in Sublime Text.

## Requirements

### General

To use this workflow with only the modifications listed in the next section, you need to have...

* a local Jekyll installation
* a local Jekyll site folder
* a remote server with SSH access
* working public key authentication for SSH access
* templates that support Link and video posts (they are not supported by Jekyll out of the box - read the next section for more information)
* [Tweetbot for Mac](http://tapbots.com/software/tweetbot/mac/) in case you need the *Tweet post* command

### Link and video post support

Link and video posts do not work with a standard Jekyll setup. You have to modify your site to support these post formats. Two starting points might be my short blog posts on [link posts](http://frederikvoigt.de/2014/07/12/link-posts-for-jekyll-sites/) and [video posts](http://frederikvoigt.de/2014/07/11/simple-video-posts-for-jekyll-sites/) with Jekyll (which lead back to GitHub for detailed instructions).

## Getting started

To get started, go through each of the script filters and scripts and do the following:

* make sure there's a `_drafts` folder inside your site directory
* adjust the `sitedir`, `extension` and other variables
* adjust the url of your blog in all open commands pointing at the remote site (*not* in those pointing at localhost)
* adjust the remote server data in all rsync commands
* if you use a different editor, adjust all references to Sublime Text or just remove them to use your default app instead (for some editors this will probably break the "jy-develop-site" which opens a directory instead of a file)
* if you do not use Safari as your standard browser, you need to change that in the Apple Scripts too (check whether your browser supports Apple Script first)

## Todo

* if a page with a subdirectory is created, the title in the YAML front matter will contain the directory name too - for the time being it must be removed manually

## Disclaimer

I'm a noob and did this to learn a little bit about shell scripts. The workflow is functional on my Mac, but it can certainly be improved. If you encounter any problems or have suggestions, please use [this repository's issue tracker](https://github.com/frederikvoigt/mrpoole/issues).

## Acknowledgements

* Script filters are based on Vítor's RecentDownloads workflow. Thanks, Vítor!
* Internet people, thank you for all the tutorials and resources that helped me get started with this workflow!

## Changelog

### v.6

* added: *New link post draft* command (only for modified Jekyll sites - please the *Link and video posts* section)
* added: *New video post draft* command (only for modified Jekyll sites - please the *Link and video posts* section)
* added: *Tweet article* command (requires [Tweetbot for Mac](http://tapbots.com/software/tweetbot/mac/))
* change: added a sed line to the *Publish draft* action that replaces the `date:` line in the post's YAML front matter with a line containing current date and time to ensure the correct order of multiple posts from the same date
* change: the current date is now added to the front matter of new drafts and pages
* change: added lowercase conversion for new filenames throughout the workflow

### v.5

* renamed and shortened keywords
* changed action descriptions
* changed "blog" to "site" throughout the workflow
* corrected typos

### v.4

* renamed keywords to better fit my workflow

### v.3

* Mr. Poole now uses variables for user dependent values throughout all scripts and script filters to facilitate customization

## Download
https://github.com/frederikvoigt/mrpoole
