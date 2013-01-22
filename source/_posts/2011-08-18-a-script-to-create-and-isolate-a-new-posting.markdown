---
layout: post
title: A Script to Create and Isolate a New Posting
date: 2011-08-18 16:04
comments: true
categories: nerdliness
link: false
---
With my [Octopress](http://octopress.org "Octopress") instance up and working smoothly I decided I wanted to simplify the process of creating a new posting, isolating it from all the postings, and editing it. Since I have well over 1700 entries on my site each site generation is around seven minutes. Running the generation multiple times to fix typos or edit content is not efficient. 

Fortunately, Octopress comes with a [Rake](http://rake.rubyforge.org/ "Rake") task called **isolate**, which parks all other postings in to a **\_stash** directory so you can work on the current one in, well, isolation. Once the posting is completed, there is an **integrate** task that returns all the postings to the main \_posts directory.

There were three activities I wanted my new post script to accomplish:

1. Create a new posting using the title passed into the script
2. Isolate that new posting using the **rake isolate** task
3. Open the new posting in Textmate (my editor of choice)

The hardest part of creating the script was getting the Rake tasks to run inside of a Ruby script, once I had that figured out the rest was easy.

Here is my script:

{% codeblock lang:ruby %}
#!/usr/bin/env ruby
#
# newpost.rb new-post-title
#
# Author: Mark Nichols, 8/2011
#
# This script automates the process of creating a new Octopress posting.
# 1. The Octopress rake new_post task is called passing in the posting name
# 2. The Octopress rake isolate taks is called to sequester all other postings in the _stash
# 3. The new file is opened in TextMate
#
# This script requires two parameters:
# 1. the sub-directory under ~/Project/octopress where the weblog is located, and
# 2. the title of the new posting to be created. The title needs to be double-quote delimited as it may contain spaces.
#
# This script expects the blogs to be siblings under the same parent directory. Futher, a symbolic link of `Rakefile.rake` 
# that points to the provided `Rakefile` needs to be created.
#
# mhn 2012-01-12
 
require 'rake'
 
# where your Octopress Rakefile lives...
WEBLOG = ARGV[0]
BLOG_DIR = "/Users/mark/Projects/octopress/#{WEBLOG}"
POST_DIR = "#{BLOG_DIR}/source/_posts"
 
# build the rake new_post command
#new_title = '"' + ARGV[1] + '"'
new_title = ARGV[1]
rake_new_post = "new_post[#{new_title}]"
 
puts "Running: " + rake_new_post + " in "+ BLOG_DIR
 
# stuff to capture output
def capture_stdout
  s = StringIO.new
  oldstdout = $stdout
  $stdout = s
  yield
  s.string
ensure
  $stdout = oldstdout
end
 
Dir.chdir(BLOG_DIR) do
  # setup rake and then create a new_post
  Rake.application.init
  Rake.application.rake_require("Rakefile", paths=["#{BLOG_DIR}"])
  new_result = capture_stdout {Rake.application.invoke_task("#{rake_new_post}")}
  puts new_result
  
  # parse the new_post result into the file name, isolate it, and open it for editing
  title_slug = new_result.split("/")
  new_post = title_slug[2].strip
  rake_isolate = "isolate[#{new_post}]"
  puts "Running: " + rake_isolate
  isolate_result = capture_stdout {Rake.application.invoke_task("#{rake_isolate}")}
  puts "Posting created and isolated, opening in editor..."
  exec "mate #{POST_DIR}/#{new_post}"
end
{% endcodeblock %}

I'm relatively new to writing Ruby scripts so I'm sure this could be cleaned up a bit. Since Octopress is running on Ruby 1.9.2, this script must also be run against Ruby 1.9.2. Using [RVM](http://beginrescueend.com/ "RVM") makes setting the current Ruby version easy so this is not an issue.

With the script installed and my path all I have to do to create a new posting and start editing is this: {% codeblock %}$ newpost.rb "A Script to Create and Isolate a New Posting"{% endcodeblock %} The script takes care of the rest, which looks like this: {% codeblock %}Running: new_post["A Script to Create and Isolate a New Posting"]
Creating new post: source/_posts/2011-08-18-a-script-to-create-and-isolate-a-new-posting.markdown
Running: isolate[2011-08-18-a-script-to-create-and-isolate-a-new-posting.markdown]
Posting created and isolated, opening in editor... {% endcodeblock %}

Sweet.