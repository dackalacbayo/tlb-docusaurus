---
id: collection
title: Collections for TLB
sidebar_label: Collections for TLB
---
_____
#### Here are the collections used in TLB website

## Locations Page
In **```config.yml```**

```
collections:
  - name: "locations" # Used in routes, e.g., /admin/collections/blog
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
In **```netlify cms```**

![alt-text](/img/add-collection-1.jpg)

## Career Page
In **```config.yml```**
```
- name: "careers" # Used in routes, e.g., /admin/collections/blog
    label: "Careers" # Used in the UI
    folder: "content/careers/positions" # The path to the folder where the documents are stored
    create: true # Allow users to create new documents in this collection
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
    fields: # The fields for each document, usually in front matter
      - {label: "Layout", name: "layout", widget: "hidden", default: "careers"}
      - {label: "Position", name: "title", widget: "string"}
      - {label: "Id", name: "id", widget: "string"}
      - {label: "Locations", name: "location", widget: "string"}
      - {label: "Description", name: "desc", widget: "string"}
      - {label: "Others", name: "body", widget: "markdown"}
```
In **```netlify cms```**

![alt-text](/img/add-collection-2.jpg)

## Grand opening photos
In **```config.yml```**
```
- name: "grand_opening_photos" # Used in routes, e.g., /admin/collections/blog
    label: "Grand Opening photos" # Used in the UI
    folder: "content/go-photos" # The path to the folder where the documents are stored
    create: true # Allow users to create new documents in this collection
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
    fields: # The fields for each document, usually in front matter
      - {label: "Image", name: "thumbnail", widget: "image"}
      - {label: "Alt", name: "title", widget: "string"}
      - {label: "Location", name: "location", widget: "string"}
```
In **```netlify cms```**

![alt-text](/img/add-collection-3.jpg)


## Brand photos
In **```config.yml```**
```
- name: "products" # Used in routes, e.g., /admin/collections/blog
    label: "Products" # Used in the UI
    folder: "content/products" # The path to the folder where the documents are stored
    create: true # Allow users to create new documents in this collection
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
    fields: # The fields for each document, usually in front matter
      - {label: "Image", name: "thumbnail", widget: "image"}
      - {label: "Alt", name: "title", widget: "string"}
```
In **```netlify cms```**

![alt-text](/img/add-collection-4.jpg)

## Event photos
In **```config.yml```**
```
- name: "events" # Used in routes, e.g., /admin/collections/blog
    label: "Events" # Used in the UI
    folder: "content/events/list" # The path to the folder where the documents are stored
    create: true # Allow users to create new documents in this collection
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
    fields: # The fields for each document, usually in front matter
      - {label: "Publish Date", name: "date", widget: "datetime"}
      - {label: "Image", name: "thumbnail", widget: "image"}
      - {label: "Alt", name: "title", widget: "string"}
```
In **```netlify cms```**

![alt-text](/img/add-collection-5.jpg)

## Media post or Feature
In **```config.yml```**
```
- name: "media" # Used in routes, e.g., /admin/collections/blog
  label: "Media" # Used in the UI
  folder: "content/media/list" # The path to the folder where the documents are stored
  create: true # Allow users to create new documents in this collection
  slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
  fields: # The fields for each document, usually in front matter
    - {label: "Layout", name: "layout", widget: "hidden", default: "media"}
    - {label: "Title", name: "title", widget: "string"}
    - {label: "Image", name: "thumbnail", widget: "image"}
    - {label: "Link", name: "link", widget: "string"}
    - {label: "Description", name: "desc", widget: "string"}
    - {label: "By", name: "by", widget: "string"}
    - {label: "Posted Data", name: "posted", widget: "date", format: "MMMM DD, YYYY"}
```
In **```netlify cms```**

![alt-text](/img/add-collection-6.jpg)
