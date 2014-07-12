# Mr. Poole - Dr. Jekyll's Butler

## Overview

Mr. Poole is an [Alfred.app](http://www.alfredapp.com) workflow for [Jekyll](http://jekyllrb.com) sites. It tries to take the drudgery out of running a static site and allows you to...
 
* create, open and publish drafts, also for link and video posts
* open existing posts for editing
* open existing pages for editing
* start a local server with the site including drafts
* open the site folder in Sublime Text for development plus the above
* deploy the site to your server with rsync
* tweet posts

## The commands

### Drafts

*New draft*: Add the title as an argument. It creates a new draft file in the *_drafts* folder of your Jekyll site. It adds a front matter template with default values defined in the script and fills in the title. In the filename, spaces are replaces by hyphens.

*New link post draft*: Read the URL, title and selection from the active Safari tab and create a new linked-list style draft with the page title, date, external URL and the selection as quote filled in. Requires modified Jekyll templates (cf. below).

*New video post draft: Read the video ID, title and selection from a Youtube or Vimeo video page in Safari and creates a new video post with the page title, date, video ID and the selection as quote filled in. Requires modified Jekyll templates (cf. below).

*Open draft*: Returns all of your existing drafts sorted by modification date (newest first). Select one to open it.

*Publish draft*: This command lets you choose an existing draft, adds the current date to the beginning of the filename and moves it to the *_posts* folder. It then builds the site and deploys it to your remote server. To check whether everything worked correctly, it opens your site's URL in the standard browser.

### Posts

*Open post*: Returns a list of your existing posts in reverse chronological order and opens selected posts in Sublime Text.

*Tweet post*: Requires a page on your domain to be open in Safari. Then reads the URL and the title and opens an editable tweet about the article. Can be used right after publishing a post because the *Publish post* command opens the article in Safari. Requires [Tweetbot for Mac](http://tapbots.com/software/tweetbot/mac/).

### Pages

*New page*: Takes the intended page name as an argument. It creates a markdown file and converts spaces in the filename to hyphens. It also fills in a template front matter with the title and default values defined in the script. It creates subfolders too. Example: The argument */resources/A list of my downloads/* will create the file *path/to/jekyll/resources/a-list-of-my-downloads.md*.

*Open page*: Returns a list of all .md files inside the Jekyll folder including subdirectories sorted by date of last modification, excluding only those in folders prefixed with an underscore such as *_posts* and *_drafts*. Opens them on selection.

### Site management

*Deploy site*: Builds the site and uses rsync to deploy it to the remote server. Then opens the URL in the browser.

*Serve site*: Builds the site with drafts starts the local server and opens the URL. Regenerates the site when files are changed.

*Edit site*: Does the same as *serve*, but additionally opens the site folder in Sublime Text.

## Requirements

### General

To use this workflow with only the modifications listed in the next section, you need to have...

* a local Jekyll installation
* a local Jekyll site folder
* a remote server with SSH access
* working public key authentication for SSH access
* Link and video posts are not supported by Jekyll out of the box - read the next section for more information
* the *Tweet post* command requires [Tweetbot for Mac](http://tapbots.com/software/tweetbot/mac/)

### Link and video posts

Link and video posts do not work with a standard Jekyll setup. You have to modify your site to support these post formats. Two starting points might be my short blog posts on [link posts](http://frederikvoigt.de/2014/07/12/link-posts-for-jekyll-sites/) and [video posts](http://frederikvoigt.de/2014/07/11/simple-video-posts-for-jekyll-sites/) with Jekyll (which lead back to GitHub for detailed instructions).

## Getting started

To get started, go through each of the script filters and scripts and do the following:

* make sure there's a *_drafts* folder inside your site directory
* adjust the $sitedir variable
* adjust the url of your blog in all open commands pointing at the remote site (*not* in those pointing at localhost)
* adjust the remote server data in all rsync commands
* if you use a different editor, adjust all references to Sublime Text or just remove them to use your default app instead (for some editors this will probably break the "jy-develop-site" which opens a directory instead of a file)
* this workflow assumes that posts and pages are markdown files using the .md extension - if you use a different extension, you will have to adjust it too

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
