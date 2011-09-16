---
layout: page
title: Wordpress Migration
date: September 16 2011
sidebar: false
footer: false
---

## Converting from WordPress to Markdown
There are numerous ways to convert WordPress posts and pages to Markdown. Using [exitwp](https://github.com/thomasf/exitwp "exitwp") is outlined below. Alternative methods include using the Jekyll supplied WordPress [migrator](https://github.com/mojombo/jekyll/tree/master/lib/jekyll/migrators "Jekyll Migrator"), or a [customized](http://paulstamatiou.com/how-to-wordpress-to-jekyll "How to: WordPress to Jekyll") [Ruby](https://github.com/harperreed/harperreed-blog/blob/master/_import/wordpress.rb "wordpress.rb") [script](http://zanshin.net/2011/08/11/switching-to-octopress/ "Switching to Octopress").

## Migrating via exitwp
**exitwp** is a Python based script and requires some setup in order to use. Installing exitwp and its runtime dependencies is explained on the exitwp [project page](https://github.com/thomasf/exitwp "exitwp"). 

### Get exitwp
`git clone git://github.com/thomasf/exitwp.git`

### Python version
Verify your python version, and update, if necessary, to version 2.6 or higher  
`python --version`

#### Getting the runtime dependencies for Mac OS X
In order to properly build the runtime dependencies, **libyaml** must be present. This library can be installed via [Homebrew](http://mxcl.github.com/homebrew/ "Homebrew").  
`brew install libyaml`

The python package installer, [pip](http://pypi.python.org/pypi/pip "pip"), is used to install Python dependencies  
`easy_install pip`.  

Change to the directory where you installed exitwp, and run pip using the supplied pip_requirements.txt file.  
``` cd exitip
    sudo pip install --upgrade -r pip_requirements.txt
```

While there may be some warning messages in the pip output, the last two lines should read  
``` Successfully installed BeautifulSout PyYAML
    Cleaning up...
```

Finally you will need to install [Pandoc](http://johnmacfarlane.net/pandoc/index.html "Pandoc") using the [package installer](http://code.google.com/p/pandoc/downloads/list "Pandoc Installer").

With the runtime dependencies installed you are now ready to proceed to the **Using exitwp** section below.

#### Getting the runtime dependencies for Ubuntu/Debian
With Python 2.6 or higher in place, run these commands to get the runtime dependencies:  
``` sudo apt-get install libyaml-dev python-dev build-essential
    sudo apt-get install pandoc
    sudo apt-get install python-yaml python-beautifulsoup
```

With the runtime dependencies installed you are now ready to proceed to the **Using exitwp** section below.

### Using exitwp
Visit the WordPress blog you wish to migrate, sign in to the administration site, and navigate to **Tools** | **Export**. Choose **All Content** and click the **Download Export File** button. This will not only export all your postings, but also any pages you may have created. Save the resulting XML file to your computer in the exitwp **wordpress-xml** directory. 

Run exitwp.py:  
`python exitwp.py`

Once it is done you have a **build** directory under the exitwp directory, which in turn contains a directory called **Jekyll**. The Jekyll directory will contain a directory named for your WordPress site. All of the pages you defined will be there, along with all of the postings in **_posts**.

## Caveats
The exitwp script does a good job of migrating content from WordPress to Markdown files that can be used by Octopress or Jekyll. It does not work in all situations however. While all pages, all published postings, and all draft postings were successfully migrated on Mac OS X, the draft postings all failed on Ubuntu. Your milage will vary.

There are alternatives to exitwp, which may provide a better migration for some. The excellent, [How to: WordPress to Jekyll](http://paulstamatiou.com/how-to-wordpress-to-jekyll "How to: WordPress to Jekyll") by Paul Stamatiou has a section on migrating from WordPress that includes links to a couple of Ruby-based migration scripts. These require making a copy of your WordPress database, and installing several Ruby gems, in order to work. You should only try them if you are comfortable debugging someone else's script.
