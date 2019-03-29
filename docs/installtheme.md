---
id: install-theme
title: Install and Use Themes
sidebar_label: Install Themes
---
_____
Themes are collections of hugo layouts that take all the hassle out of building your site. If you’re not inclined to learn how to write HTML and CSS, or if you simply want to get your blog or content site up as soon as possible then themes are for you. There are dozens of publicly available pre-built themes available for download that developers in the hugo community have built. Using a pre-built theme takes all the hassle out of designing and organizing your hugo site.

## Importing a Theme
Once you’ve found a theme you want to use, it’s time to import it into your project. There’s two ways you can do this. The easiest is to use git. Simply cd into your Themes folder and clone the repository you want. You also need to add the theme to your config.toml file.
```
Cd Themes
Git clone path-to-git-repo.git
```
Once you’ve cloned the theme you want to use the last thing you have to do is tell hugo that you want to use that theme. Head over to your config.toml file and add a line specifying the name of the theme you imported.
```
+++
…
Theme = “your-theme-name”
…
+++
```
Now restart your hugo site and you should see your new theme. Play around with the theme by adding content files, taxonomies and data. The theme should automatically know what to do with all of your content and will organize it for you.

Download a couple themes and see which one works for your website. To switch to a different theme simply download the new one (you don’t have to delete the files for the existing one), and modify the theme name your config.toml file.
