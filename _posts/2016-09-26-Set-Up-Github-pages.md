---
layout: post
title: Setup Github Pages
permalink: /_posts/
---

Since losing most of my blogs to the shutdown of Blogcn.com and Microsoft's discontinuation of MySpace service, I've lost trust to blog services and didn't blog for a long time. I still occasionally jotted down some of my personal thoughts on Apple's icloud.com, but was still yet to find a site for more "professional" thoughts that are intended to be public. 

Then I came across Github pages and jekyll, a good static site generator combination. In a nutshell, this combination:
1. always has backup by design (Git Repo), 
2. takes minimum time to configure the article format (jekyll theme + mark down files), 
3. is genetically suitable for a "techinical" writer like me to potentially include "code snippet", graphs and tables in the articles. 

I've referred to multiple random web pages and managed to set up Github + Jekyll on both Windows 10 and Mac OS EL Capitan, neither of which is as straightforward as I may hope. 

Below is the step by step setup process.

## Main Steps
 * Set up Github account; create a Git repo: name your repository username.github.io, replacing username with your GitHub username. More details of this step can be found at [Github Pages Guide](http://jmcglone.com/guides/github-pages). This page will be your personal home page where you can set up your personal information and provide links to your blog page and it's OK to work on the master branch for this repo. 
 * If you like certain theme for your home page, find its source code on Github and fork it to your repo created above. For my own page jiandu.github.io, I used a simple academic style called "Much-Worse jekyll theme", which can be found [here](https://github.com/gchauras/much-worse-jekyll-theme). 
 * Find another Github source theme for your blog page and fork it to your Github, which at repo level is parallel to your home page repo. Rename the repo as something like "blog"; it will be shown as: yourname/blog on your github page. For this one, it's probably necessary to work on the "gh-pages" branch. If you don't have a "gh-pages" branch, use Git to create one from master. 
 * Clone both pages to local (in two parallel folders). 
  	```
 	git clone [gitRepoURL]
 	```
 * There are some customization to do for both pages above to make them work the way your want: not so straightforward, but not very difficult either. You should try to play with the folder and files and see the impact. 

## Serve Jekyll Locally
Up to now, you don't have to set up any software locally (except Git). To set up Jekyll locally, there is a little installation to do. 
Why would one want to set up Jekyll locally? One benefit is that you can see quickly how your website would look like after your make changes on git repo locally without committing any changes to Github server. The setup processes are different on Windows and Mac. 

### Windows
 * Install Ruby.
 * Install Ruby DevKit.
 	Next, you need to initialize the DevKit and bind it to your Ruby installation. Open
 	your favorite command line tool and navigate to the folder you extracted the DevKitinto.

	```
	cd C:\RubyDevKit
	```
	Auto-detect Ruby installations and add them to a configuration file for the next step.
	```
	ruby dk.rb init
	```
	Install the DevKit, binding it to your Ruby installation.
	```
	ruby dk.rb install
	```

 * Install bundler:
	 ```
	 get install bundler
 	```
 * Change directories to the new repository you created.
 * Install Jekyll Gem:
   * If don't have a "Gemfile" in your repo directory, create a Gemfile (without file extension) using Notepad. Add the lines below to your "Gemfile" (if Gemfile already exsists, replace the contentes with below); 
   	```
    source 'https://rubygems.org'
	gem 'githubpages',
	group: :jekyll_plugins
	```
 * Install Jekyll and other dependencies from the GitHub Pages gem:
 	```
    bundle install
    ```
  * Generate Jekyll sites: 
	```
    bundle exec jekyll new . force
    ```
 * Edit your Gemfile and remove the following line:
 	```
    "jekyll", "3.2.1"
    ```
    Uncomment the following line by removing the ```#``` :
    ```
    gem "githubpages", group :jekyll_plugins
    ```
 * Build your Jekyll Site locally:
 	```
    bundle exec jekyll serve
    ```
    This also works for me in Git bash: 
    ```
    jekyll serve
    ```
    Preview your local Jekyll site in your web browser at [http://localhost:4000](http://localhost:4000) .
 * Push your local changes to your remote origin of Git repo (using Git bash). 
 * Check the updated pages at: http://username.github.io/ and http://username.github.io/blog (depending on which repo directory you were at when you were running "jekyll serve")

### Mac (OS EL Capitan)