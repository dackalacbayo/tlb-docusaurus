---
id: Quick-Start
title: Quick Start
sidebar_label: Quick Start
---
_____
Create a Hugo site using the beautiful **Ananke** theme.

>This quick start uses windows in the examples. For instructions about how to install Hugo on other operating systems, see [install](/docs/install).

## Step 1: Install Hugo
 See the installation for windows [here.](/docs/windows)

## Step 2: Create a New Site
```
hugo new site quickstart
```
The above will create a new Hugo site in a folder named quickstart.

## Step 3: Add a Theme
See [themes.gohugo.io](https://themes.gohugo.io/) for a list of themes to consider. This quickstart uses the beautiful Ananke theme.
```
cd quickstart

    # Download the theme

git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

    # Note for non-git users:
    #   - If you do not have git installed, you can download the archive of the latest
    #     version of this theme from:
    #       https://github.com/budparr/gohugo-theme-ananke/archive/master.zip
    #   - Extract that .zip file to get a "gohugo-theme-ananke-master" directory.
    #   - Rename that directory to "ananke", and move it into the "themes/" directory.
    # End of note for non-git users.

    # Edit your config.toml configuration file
    # and add the Ananke theme.

echo 'theme = "ananke"' >> config.toml
```

## Step 4: Add Some Content
```
hugo new posts/my-first-post.md
```
Edit the newly created content file if you want.

## Step 5: Start the Hugo server
Now, start the Hugo server
```
▶ hugo server -D
```

**OUTPUT:**
```
                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```
Navigate to your new site at **http://localhost:1313/**.


## Step 6: Customize the Theme
Your new site already looks great, but you will want to tweak it a little before you release it to the public.

### Site Configuration
Open up **config.toml** in a text editor:

```
baseURL = "https://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "ananke"
```

Replace the **title** above with something more personal. Also, if you already have a domain ready, set the **baseURL**. Note that this value is not needed when running the local development server.
