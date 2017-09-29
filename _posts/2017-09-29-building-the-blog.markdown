---
layout: post
comments: true
title:  "First Post - Setting Up the Blog"
date:   2017-09-29 09:53:38 -0500
categories: jekyll github git setup
---

<br>

---

<br>

## **Prerequisites**

### 1. Install ruby
```bash
$ sudo apt-get install ruby-dev
```

### 2. Install Bundler and Jekyll
```bash
$ sudo gem install bundler jekyll
```

*I'm assuming that you already have __git__ installed on your system.
  If you haven't set it up already, visit
  [Set Up Git](https://help.github.com/articles/set-up-git/).*

<br>

---

<br>

## **Generate Jekyll Site Files**

### 1. Create the Jekyll template
```bash
$ jekyll new <username>.github.io
$ cd <username>.github.io
```
I'm using the default **Github Pages** format for creating the local repository
  which will match the name of my github repository later. Replace `<username>`
  with your github username.

### 2. Download Jekyll Dependencies
When you created the new **Jekyll** site template, it created a file called
  **Gemfile**. This file needs to be edited so we can download the necessary
  dependencies for **Jekyll**. Open **Gemfile** using your editor of choice,
  I prefer to use **nano** for simple editing and **atom** for bigger jobs.
```bash
$ nano Gemfile
```

  * Comment out the line `gem "jekyll", "3.5.2"` by adding a `#` at the
    beginning (*your version may be different*).
  * Uncomment the line `gem "github-pages", group: :jekyll_plugins` by
    removing the leading `#`
  * Directly above the newly uncommented line, add the following line: `source
    'https://rubygems.org'`
  * Save the file (for nano: `Ctrl+X -> Y -> Enter`)

Now update **Bundle** and install the **Jekyll** dependencies with:
```bash
$ bundle update
$ bundle install
```

<br>

---

<br>

## **Building Jekyll Site Locally**
To preview changes locally and make sure the site functions properly and as
  expected *before* making it live, we can build and serve it locally first.

```bash
$ bundle exec jekyll serve
```

Now go to a browser and type in `localhost:4000` to see the live site. If it's
  working properly you should see a page like this:
<br><br>

![jekyll_template]({{ site.baseurl }}/images/jekyll_template.png)

<br><br>

This is **Jekyll's** default template, we will edit this information shortly.

To stop serving the site locally, go back to terminal and press `Ctrl+c`.

<br>

---

<br>

## **Making the Github Blog Live**
To make this blog live, we will need to create a github repository to store all
  the files.

### 1. Create the repository
Navigate to [Github](https://github.com) and login. On the home page click `New
  repository`. Name the repository `<username>.github.io` replacing `<username>`
  with your login. Adding a description is optional. Also, check the box to
  `Initialize this repository with a README`. This is the first thing people will
  see if they visit your blog's github repository, we can edit it later.

### 2. Initialize site as a github repository
If you are not already in the local directory `<username>.github.io`, navigate
  there now in the terminal. Initialize the directory as a github repository
  with:
```bash
$ git init
```

Now connect the local repository to the github repository we just set up:
```bash
$ git remote add origin https://github.com/<username>/<username>.github.io
```

Since we initiated the repo with a README we will need to merge the two repos
  first before we can push our changes.
```bash
$ git pull origin master
```

Now we can stage all the local files that aren't already in the github repo,
  commit the changes, and then push the changes.
```bash
$ git add .
$ git commit -m "first commit"
$ git push origin master
```

After a few seconds, you should be able to see your site live in a browser by
  navigating to `https://<username>.github.io`!

<br>

---

<br>

## **Customizing the Basics**
To customize the name of the blog, your name, your email, etc., open the file
  `_config.yml` in your favorite editor and change the relevant fields to your
  liking....
