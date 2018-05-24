Drupal is well and good, but I don't like editing pages in a web UI.  Or
storing them in MySQL.  Or configuring workflows.  Is that a problem?  Can I
still use Drupal?

Mr. Hyde is the evil version of Dr. [Jekyll](https://jekyllrb.com/). You can
create Markdown files and store them in a git repo... but display them as
pages in a Drupal site. This allows you to use Drupal's general layout
engine (themes and blocks) while tracking content in Git/Github/etc.

# Install the module

```
$ git clone https://github.com/totten/hyde
$ cd hyde
$ composer install
$ drush en hyde
```

> Note: It should be OK to install via `composer require totten/hyde`, but
> I haven't done enough with D7+Composer to speak to that.

# Initialize the content root

```
$ cd <drupal-private-data-folder>
$ mkdir hyde
$ cd hyde
```

Of course, this folder should probably be a git repo. You could initialize a
new repo here (`git init`) or clone an existing repo.

> __Tip__: If you want to store content in another folder, override the
> value of `hyde_path` by calling `drush vset hyde_path /path/to/doc/root`
> or editing `settings.php`.

# Add a new page

```
$ echo "Hello __world__" > hello-world.md
$ drush cc all
$ curl https://example.org/hello-world
$ git add hello-world.md
$ git commit
```

# Markdown Metadata

In Jekyll syntax, a Markdown file can begin with a YAML metadata. In this
example, we set the `title` of the HTML page with a little extra metadata:

```
---
title: "The future of old school content"
---
# Old is the new new
Because sometimes you like to write content in a simple way.

# Git is the new CMS
Because sometimes you like to write content in a simple way.
```

Supported fields:

* `title`: The main HTML page title

# Issues/Limitations/FIXMEs

There are several things that one might do if they really cared about this. Right now,
I'm trying to write this quickly, so I don't really care.

* Add an admin form for manging `hyde_path`
* Test/implement page-cache support.
* Rework as Drupal entity. If the file-system is writeable, allow editing the `body` via CLI or GUI.
* Add more options to the metadata for:
    * Setting permissions
    * Changing layouts

# Coding Style

This repo is a safe space for godawful code that I wrote in 15 minutes
after drinking some beer.
