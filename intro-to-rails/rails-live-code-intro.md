# Live Code Intro

<iframe src="https://adaacademy.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=f73fd9dc-ee88-49cd-be49-ac5601251263&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&start=0&interactivity=all" height="405" width="720" style="border: 1px solid #464646;" allowfullscreen allow="autoplay"></iframe>

## Learning Goals

At the end of this lesson, students should be able to...
- Explain how the lectures for this week will be organized
- Create and run a new rails project

## Resources

- [Rails Unit Video Lessons](https://adaacademy.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx?folderID=164cde16-d68f-49df-a5de-ac560120cecf)
- [Ada Books Code homepage](https://github.com/AdaGold/ada-books)

## Live Code

At Ada, our Rails curriculum is presented in the form of a continuous live-code. We have found that slowly adding pieces to a long-lived application is the best way to avoid confusion as we introduce new concepts. We'll continue to build upon this live-code for the next 3 or so weeks of curriculum.

The theme for this live-code will be a website for a public library. Books galore!

We'll be storing this code in a GitHub repository, and pushing to it regularly. In order to have access to the work we do in class, **You should not fork this repo**, instead clone the `AdaGold` version directly. That way when we `git push` you can `git pull` to get the changes immediately.

If you also want to have a copy under your own GitHub account, see your instructor about setting up multiple remotes.

### Following Along

One important question always comes up as we go work through this project: **Should I try to follow along as you build the application?**

In general, the choice is yours. However, we have found that because Rails is such a large, finicky framework, following along with a live code can be more difficult than with previous Ruby work. There are more places to make typos, which results in students spending a bunch of time debugging while the rest of the class keeps moving and falling behind.

Another approach is to take physical, written notes (or type them in an electronic document) during lecture. Here are aspects of this week's structure that will help with this:
- The requirements for the week 1 project match what we do in class very closely
- All code written in the live-code will live in a repository on GitHub, and instructors will push frequently
- We've attempted to keep a tight cycle between lecture and project time, so that you have frequent opportunities to try things out

Sometimes we'll have an exercise that involves modifying the live-code. When this happens we'll make sure we've pushed our most recent changes.

If you do determine that following along is right for you, we recommend maintaining either two projects (your version and ours), or using git branches, so that you still have access to our version of the code.

## Setting Up a Rails Project

To demonstrate this process, we'll walk through the setup for our live code. Before we start, make sure you've installed postgres and set up the Rails template.

### Creating the Project

To create a new Rails project, we use the command `rails new <project-name>`:

```bash
$ rails new cx-class-library # fill in the details for your class
```

This will create a new folder with the name we specified, and do a bunch of setup work. It might take a while. This is fine.

Next we `cd` into the new project folder:

```bash
$ cd cx-class-library # again fill in your details
```

**Important:** if you already have a folder (like when you've cloned a project repo), you can `cd` into that folder and run `rails new .` (remember that `.` means "use the current directory").

### Git

Fun fact: every new Rails project is set up as a git repo by default. However, the repo won't have any commits yet. We've already done some work in the form of running `rails new`. Let's commit that before we go any further:

```bash
$ git add . # everything in the current directory, and all of its children
$ git commit -m "Run rails new"
```

This should be part of your process every time you start a new Rails project.

### Database

The last step before we're ready to go is to tell the postgres program running on our computer about our new Rails project. We need to do this before we can do _anything_ with Rails, even though we won't be working with the database to start. To set up the database, run:

```
$ rails db:create
$ rails db:migrate
```

Because the database is not committed to git, you'll need to repeat this once for each Rails project you run, whether you're creating it from scratch or cloning someone else's project.

### Running the Server

Ruby on Rails is a Ruby program, and like the Ruby programs we've written in the past, it needs to be run from the command line. To do so, run:

```bash
$ cd <my_project_folder>
$ rails server
```

This command starts a web-server running on our computer, which we can access at [http://localhost:3000](http://localhost:3000) (`localhost` means "this computer"). Pull this up in chrome and you should see this image:

![Rails Start Screen](images/rails5-start.jpeg)

The program we're running in the command line will display the output of the log, showing all the errors, warnings, and notifications generated by the app, all the DB queries, and some basic timing information. Pretty handy!

Since we'll still need to use our terminal to do other things, let's open up a new terminal tab now. You can do so with `cmd+t`, and switch between tabs with `cmd+[` and `cmd+]`.

Unlike running `rails new` or setting up the database, starting the server is something you'll do many times for each project - essentially, each time you sit down to work on it.

### Summary

The steps to create a new Rails project are:

1. `rails new project-name`
    - If there's already a folder for that project, `cd` into the folder and use `.` (current directory) as `project-name`
1. `cd project-name`
1. `git add .; git commit -m "Run rails new"`
1. `rails db:create`
1. `rails db:migrate`
1. `rails server`

We have pushed the [library repo](https://github.com/AdaGold/ada-books) we created to match the video lessons. Feel free to clone it now, and remember to run `rails db:create`.

### Switching Between Lessons

You can switch between lessons with:  

- Checkout the lesson by branch name
  - `git checkout <BRANCH_NAME>`
- Reset the database to erase any changes you might have made to it and use the lesson's database structure.
  - `rails db:reset`
  - `rails db:migrate`
- If needed do a bundle install to install the gems and yarn to install JavaScript stuff
  - `rm *.lock`
  - `bundle install`
  - `yarn`
