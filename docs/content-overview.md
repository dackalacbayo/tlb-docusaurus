---
id: content-overview
title: Netlify CMS
sidebar_label: Netlify CMS
---
_____
## Installing and configuring Netlify CMS:

### Step 1. Creating the admin files

All Netlify CMS files are contained in a **static** admin folder, stored at the root of your published site. The static files of a Hugo site are stored inside the **/static** location at the root of your website.

Navigate to **static** of your website and create a folder named **admin** inside it. If there is no static folder in your website then simply create a new folder and name it.

The **admin** folder of Netlify CMS contains two files:

```
admin

├ index.html
└ config.yml
```

Create the file **index.html** inside the admin folder The content of this file will be:

```
<!doctype html>
<html>
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Content Manager</title>

  <!-- Include the styles for the Netlify CMS UI, after your own styles -->
  <link rel="stylesheet" href="https://unpkg.com/netlify-cms@^1.0.0/dist/cms.css" />

</head>
<body>
  <!-- Include the script that builds the page and powers Netlify CMS -->
  <script src="https://unpkg.com/netlify-cms@^1.0.0/dist/cms.js"></script>
</body>
</html>
```


### Step 2. Configuring config.yml file
Since we are using **Netlify and GitHub for hosting** our website so enter this in your file:
```
backend:   
  name: git-gateway   
  branch: master # Branch to update (optional; defaults to master)
```

>You have the option to enable the **Editorial Workflow**, which adds an interface for **drafting, reviewing, and approving posts**. To do this, add the following line to your **config.yml**:

```
publish_mode: editorial_workflow
```

Next we are going to specify the locations where **Netlify CMS** will store the images you upload to your blog. I wish to store the files in **static/images/uploads** folder of my website and make them available in the published website at **/images/uploads**.

While **media_folder** specifies where uploaded files will be saved in the repo, **public_folder** indicates where they can be found in the published site. Depending upon your requirements you may edit the code:

```
media_folder: "static/images/uploads" # Media files will be stored in the repo under static/images/uploads
public_folder: "/images/uploads" # The src attribute for uploaded media will begin with /images/uploads
```

>Note: If public_folder is not set, Netlify CMS will default to the same value as media_folder, adding an opening / if one is not included.

### Step 3. Specifying collections in config.yml file
Collections define the structure for the different content types on your static site. Since every site is different, the collections settings will be very different from one site to the next.

#### Example:
I wanted my website to have these options while creating a post: **Layout, Title, Featured Image, Address, Opening time, Closing time, Type, Menu, and Vid**

Enter these lines to your code in the **config.yml** file:

```
collections:
  - name: "locations" # Used in routes, e.g., /admin/collections/locations  
    label: "Locations" # Used in the UI
    folder: "content/locations/list" # The path to the folder where the documents are stored
    create: true # Allow users to create new documents in this collection
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
    fields: # The fields for each document, usually in front matter
      - {label: "Layout", name: "layout", widget: "hidden", default: "locations"}
      - {label: "Title", name: "title", widget: "string"}
      - {label: "Featured Image", name: "thumbnail", widget: "image"}
      - {label: "Address", name: "address", widget: "string"}
      - {label: "Opening time",  name: "start",  widget: "datetime", default: "", format: "hh:mma"}
      - {label: "Closing time",  name: "end",  widget: "datetime", default: "", format: "hh:mma"}
      - {label: "Type", name: "types", widget: "string"}
      - {label: "Menu", name: "menu", widget: "list", fields:[{label: "Menu name", name: "name", widget: "string"}]}
      - {label: "Vid", name: "video", widget: "file", required: false}
```

### Step 4. Setup on Netlify
Before we push our code to GitHub and Netlify we need to make another configuration. We need to specify the Hugo Version which should be used by Netlify to generate the website. To do so, at the root of your website’s create a new file named **netlify.toml** with content:

```
[build]
  publish = "public"
  command = "hugo"

[context.production]
  command = "hugo"
  [context.production.environment]
    HUGO_VERSION = "0.36"
    HUGO_ENV = "production"

```

Upload all the code of your website on a repository on GitHub.

Login to your **Netlify Account**. Click on **New Site** from Git. Now choose **GitHub**. Netlify will now ask for permission, allow by clicking on **Authorize Application**. On the next screen choose the repository to which you uploaded the code of your website. On the next screen you will see something like this:

![alt-text](/img/create.png)

Write **hugo** in the **Build command** field. For the **Publish directory** field you need to know where Hugo build and saves your website, the default is **public/**, write the location in this field. Click **Deploy site**. Netlify will publish the contents of the Publish directory online after executing the **Build command**.

The website has now been setup on Netlify.


### Step 5. Enable Identity and Git Gateway

Netlify's Identity and Git Gateway services allow you to manage CMS admin users for your site without requiring them to have an account with your Git host or commit access on your repo. From your site dashboard on Netlify:

1. Go to **Settings > Identity**, and select **Enable Identity service**.
2. Under **Registration preferences**, select **Open** or **Invite only**.
>In most cases, you want only invited users to access your CMS, but if you're just experimenting, you can leave it open for convenience.

3. If you'd like to allow one-click login with services like Google and GitHub, check the boxes next to the services you'd like to use, under **External providers**.
4. Scroll down to **Services > Git Gateway**, and click **Enable Git Gateway**. This authenticates with your Git host and generates an API access token.
>In this case, we're leaving the Roles field blank, which means any logged in user may access the CMS.

### Step 6. Add the Netlify Identity Widget (Optional)
Use the Netlify’s snippet injection feature and add this code before **</head>**:

```
<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
```

Add this before **</body>**:

```
<script>
  if (window.netlifyIdentity) {
    window.netlifyIdentity.on("init", user => {
      if (!user) {
        window.netlifyIdentity.on("login", () => {
          document.location.href = "/admin/";
        });
      }
    });
  }
</script>
```

### Step 7. Accessing the CMS

You might have receieved an email saying **“You’ve been invited to join xyz” from the email: no-reply@netlify.com**. If you did not receive the email then you need to invite yourself to access the CMS.

To do this, select the **Identity tab** from your site dashboard, and then select the **Invite users** button. Invited users will receive an email invitation with a confirmation link. Clicking the link will take you to your site with a login prompt.

If you left your site registration open, or for return visits after comfirming an email invitation, you can access your site’s CMS at
>yoursite.com/admin/
