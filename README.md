## Synopsis

This repository contains all content used to generate the official Nextech API documentation at https://nextechsystems.github.io/selectapidocspub

## Modifying the Documentation

The Nextech API documentation is located in this repository under source/includes in markdown files. Each file corresponds to a root level topic in the official documentation's navigation pane on the left. You may modify them with any text or markdown editor.

If you need to change the formatting, the style sheets are located in source/stylesheets. The primary style sheet is screen.css.scss.

You are encouraged to modify the documentation from a Mac or Linux based system due to the complexities of setting up a local test environment in a Windows environment to preview your changes.

## Testing your changes locally

To preview your changes you must have run and browse to a local web service that points to your clone of this repository.

For assistance or additional instructions please visit the official Slate readme at https://github.com/lord/slate

### Initial Setup

1. Open a new Terminal or Command Shell window
2. Browse into the path of your cloned repository on your local machine
3. Type in `ruby -v` to determine your version of Ruby
4. If your version of Ruby is before 2.4, then upgrade Ruby. Mac users may follow the instructions at https://stackoverflow.com/questions/38194032/how-to-update-ruby-version-2-0-0-to-the-latest-version-in-mac-osx-yosemite to upgrade
5. Once you've verified your version of Ruby is 2.4 or better, type in `bundle install`

### Testing

1. Open a new Terminal or Command Shell window
2. Browse into the path of your cloned repository on your local machine
3. Type in `bundle exec middleman server`
4. The URL to the localhost site will appearin your window. Open it from a browser
5. If necessary, make changes to your markdown or style sheet, and refresh the page upon saving your changes

### Publishing

You can publish the contents of this repository to https://nextechsystems.github.io/selectapidocspub by doing the following:

1. Cloning https://github.com/NextechSystems/selectapidocspub to a Mac OS machine
2. Open a new Terminal or Command Shell window 
3. Browse into the path of your cloned repository on your local machine
4. Type in `./deploy.sh`

It takes a few minutes for the changes to go live.
