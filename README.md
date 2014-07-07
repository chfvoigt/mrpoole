# Mr. Poole - Dr. Jekyll's Butler

## Overview

Mr. Poole is an [Alfred.app](http://www.alfredapp.com) workflow for [Jekyll](http://jekyllrb.com) sites. It tries to take the drudgery out of running a static site and allows you to...
 
* create, open and publish drafts
* open existing posts for editing
* open existing pages for editing
* start a local server with the site including drafts
* open the site folder in Sublime Text for development plus the above
* deploy the site to your server with rsync

## What it does

### Drafts

*Create draft*: Add the title as an argument. It creates a new draft file in the *_drafts* folder of your Jekyll site. It adds a frontmatter template with default values defined in the script and fills in the title. In the filename, spaces are replaces by hyphens.

*Open draft*: Returns all of your existing drafts sorted by modification date (newest first). Select one to open it.

*Publish draft*: This command lets you choose an existing draft, adds the current date to the beginning of the filename and moves it to the *_posts* folder. It then builds the site and deploys it to your remote server. To check whether everything worked correctly, it opens your site's URL in the standard browser.

### Posts

*Open post*: Returns a list of your existing posts in reverse chronological order and opens selected posts in Sublime Text.

### Pages

*Create page*: Takes the intended page name as an argument. It creates a markdown file and converts spaces in the filename to hyphens. It also fills in a template frontmatter with the title and default values defined in the script. It creates subfolders too. Example: The argument */resources/A list of my downloads/* will create the file *path/to/jekyll/resources/a-list-of-my-downloads.md*.

*Open pages*: Returns a list of all .md files inside the Jekyll folder including subdirectories sorted by date of last modification, excluding only those in folders prefixed with an underscore such as *_posts* and *_drafts*. Opens them on selection.

### Site management

*Deploy*: Builds the site and uses rsync to deploy it to the remote server. Then opens the URL in the browser.

*Serve*: Builds the site with drafts starts the local server and opens the URL. Regenerates the site when files are changed.

*Develop*: Does the same as *serve*, but additionally opens the site folder in Sublime Text.

## Requirements

To use this workflow with only the modifications listed in the next section, you need to have...

* a local Jekyll installation
* a local Jekyll site folder
* a remote server with SSH access
* working public key authentication for SSH access

## Getting started

To get started, go through each of the script filters and scripts and do the following:

* make sure there's a *_drafts* folder inside your site directory
* adjust the $sitedir variable
* adjust the url of your blog in all open commands pointing at the remote site (*not* in those pointing at localhost)
* adjust the remote server data in all rsync commands
* if you use a different editor, adjust all references to Sublime Text or just remove them to use your default app instead (for some editors this will probably break the "jy-develop-site" which opens a directory instead of a file)
* this workflow assumes that posts and pages are markdown files using the .md extension - if you use a different extension, you will have to adjust it too

## Todo

* if a page with a subdirectory is created, the title in the YAML frontmatter will contain the directory name too - for the time being it must be removed manually
* move to GitHub

## Disclaimer

I'm a noob and did this to learn a little bit about shell scripts. The workflow is functional on my Mac, but it can certainly be improved. If you encounter any problems or have suggestions, please use [this repository's issue tracker](https://github.com/frederikvoigt/mrpoole/issues).

## Acknowledgements

* Script filters are based on Vítor's RecentDownloads workflow. Thanks, Vítor!
* Internet people, thank you for all the tutorials and resources that helped me get started with this workflow!

## Changelog

### v.4

* renamed keywords to better fit my workflow

### v.3

* Mr. Poole now uses variables for user dependent values throughout all scripts and script filters to facilitate customization

## Download
https://dl.dropboxusercontent.com/u/1767984/Mr.%20Poole.alfredworkflow
