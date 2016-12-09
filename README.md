Infoshop.io
===========

This is the codebase that runs [http://infoshop.io/](http://infoshop.io/). It is developed using [nanoc](http://nanoc.stoneship.org/) and rsynced in static form to the server.

Installation
------------

First, install the prerequisites and clone this codebase

	# [Ruby Version Manager](http://rvm.io/)
	$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
	$ \curl -sSL https://get.rvm.io | bash -s stable

	# [Homebrew](http://brew.sh/)
	$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

	# Ghostscript and ImageMagick
	$ brew install gs
	$ brew install imagemagick

	# This generator codebase
	$ git clone git@github.com/infoshop-io/generator
	$ cd generator

Second, building Ruby 2.2.6 if you need, then install any necessary gems

	$ rvm install ruby-2.2.6
    $ gem install bundler
    $ bundle install

Finally, in two different terminal windows, run guard and nanoc view:

    $ bundle exec guard
    $ bundle exec nanoc view

Now load http://localhost:3000/ to see the preview server.

Maintenance
-----------

To add a resource to the infoshop, move the PDF file into `content/media` with a unique filename, then create a YAML file in parallel (it must differ from the PDF in extension only) with the following structure:

	---
	title: "TITLE_GOES_HERE"
	summary: "ONE_SENTENCE_SUMMARY"
	publisher: "PUBLISHER_OPTIONAL"
	date: "DATE_OPTIONAL"
	editors:
	  - EDITORS_OPTIONAL
	authors:
	  - AUTHORS_OPTIONAL
	languages: 
	  - en
	tags:
	  - introduction
	sources: 
	  - SOURCE_URLS_OPTIONAL
	---

Anything tagged with "introduction" will appear on the landing page.

Deployment
----------

To deploy, make sure you can push to both this repository and [the site repo](https://github.com/infoshop-io/site), then run:

	$ ./publish
