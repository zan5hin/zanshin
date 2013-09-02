---
layout: post
title: "How to Remove Git Submodules"
date: 2013-09-02 11:18
comments: true
categories: nerliness
link: false
---
Removing a [Git submodule](http://git-scm.com/book/en/Git-Tools-Submodules "Git submodule") is nowhere near as easy as adding one. In my projects I typically use a submodule for managing dependencies that are themselves a Git repository. When that dependency goes away it is necessary to remove the submodule. Here's how I go about that task.

First delete the relevant section from the `.gitmodules` file at the root of the parent project. This section will have this format:

    [submodule "vendor"]
      path = vendor
      url = git://github.com/some-user/some-repo.git

Next stage the `.gitmodules` file.

    $ git add .gitmodules

Now delete the relevant section from the `config` file located in the `.git` directory at the root of the project. It will look something like this:

    [submodule "vendor"]
      url = git://github.com/some-user/some-repo.git

Now it's time to use `git rm` to tell Git to stop tracking the submodule.

    $ git rm --cached path/to/submodule

Be careful not to include a trailing slash on the `git rm` command as it will cause errors.

Now that no longer is tracking the submodule it can be deleted from the file system.

    $ rm -rf .git/modules/submodule_name

Commit the changes to the repository.

    $ git commit -m "Removed <vendor> submodule."

Finally you can delete the actual submodule.

    $ rm -rf path/to/submodule

That's it. The submodule has been completely removed from Git and removed from the file system.
