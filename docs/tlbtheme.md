---
id: tlb-theme
title: TLB Theme
sidebar_label: TLB Theme
---
_____
## Menu
A **menu** is a named array of menu entries accessible by name via the **.Site.Menus** site variable. For example, you can access your site’s main menu via **.Site.Menus.main**.


In **config.toml** add entries for menu:

```
[[menu.main]]
    identifier = "Home"
    name = "Home"
    url  = "/"
    weight = 1

 [[menu.main]]
    identifier = "Locations"
    name = "Locations"
    url  = "/locations"
    weight = 2

  [[menu.main]]
   identifier = "Menu"
   name = "Menu"
   url  = "/"
   weight = 3

 [[menu.main]]
    parent = "Menu"
    name = "Full Menu"
    url = "/full-menu"

 [[menu.main]]
    parent = "Menu"
    name = "Limited Flavors"
    url = "/limited-flavors"
```

>The **identifier** must match the section name.

In **site-navigation.html**

```
<nav class="nav nav-navbar ml-auto">
    {{ range .Site.Menus.main }}
      {{ if (not (eq .Weight 0)) }}
        {{ if .HasChildren }}
          <li class="nav-item">
            <a class="nav-link nav-text" id="<nav-text></nav-text>" href="#">{{ .Name }} <span class=""><i class="fas fa-caret-down"></i></span></a>
              <nav class="nav ">
                {{ range .Children }}
                <a class="nav-link nav-child" href="{{ .URL }} ">{{ .Name }}</a>
                {{ end }}
              </nav>
          </li>
        {{ else }}
        <a class="nav-link" href="{{ .URL }}">
          {{ .Pre }}
          <span class="nav-text" id="nav-text">{{ .Name }}</span>
        </a>
        {{ end }}
      {{ end }}
    {{ end }}
</nav>
```

> **{{ if (not (eq .Weight 0)) }}** used to display menu which weight is not equal to 0. Since i added weight in every menu in config, all the menu will display.

### Displaying Submenu
#### To display menu with submenu

> **{{ if .HasChildren }}** is used. It returns true if .Children is non-nil.

Menu with submenu in config used **parent="[name of parent]"**
#### Example
```
[[menu.main]]
 identifier = "Menu"
 name = "Menu"
 url  = "/"
 weight = 3

[[menu.main]]
  parent = "Menu"
  name = "Full Menu"
  url = "/full-menu"

[[menu.main]]
  parent = "Menu"
  name = "Limited Flavors"
  url = "/limited-flavors"
```

## Page Section

To display section in home page go to **index.html** in layouts folder.
```
└── layouts
    └── _default
    └── page
    └── partials
        └── products.html
        └── locations.html
    index.html
```
Add the html files use want to display using **partials**

>**Partials** are smaller, context-aware components in your list and page templates that can be used economically to keep your templating DRY

#### Example:

**```index.html```**
```
    {{ partial "products.html" . }}
    {{ partial "locations.html" . }}
```

### Displaying Section
>.**Site.RegularPages**
a shortcut to the regular page collection. .Site.RegularPages is equivalent to where .Site.Pages "Kind" "page".

>**.Site.Params** is a container holding the values from the params section of your site configuration.

>**range** to iterate over a map, array or slice

```
{{ $section := where .Site.RegularPages "Section" "in" .Site.Params.products }}

      <div class="col-lg-5">
        <div class="slider-dots-fill" data-provide="slider" data-autoplay="true" data-autoplay-speed="1300" data-arrows="true" data-dots="true" >
          {{ range $section }}
            <div style=""><img class="img-brand" width="100%" src="{{ .Params.thumbnail }}"></div>
          {{ end }}
        </div>
      </div>
```
>**Note**: you need to declare a params in **config.toml**
```
[params]
    products = ["products"]
```
#### Example markdown file (.md)
```
---
thumbnail: /images/uploads/brand (2).jpeg
title: product_5
---
```

### Displaying images
Display images from content folder

```
      <div class="col-lg-5">
        <div class="slider-dots-fill" data-provide="slider" data-autoplay="true" data-autoplay-speed="1300" data-arrows="true" data-dots="true" >
          {{ range $section }}
            <div style=""><img class="img-brand" width="100%" src="{{ .Params.thumbnail }}"></div>
          {{ end }}
        </div>
      </div>
```

#### Example markdown file (.md)
```
---
thumbnail: /images/uploads/brand (2).jpeg
title: product_5
---
```

### Displaying nested images


Display nested images from content folder

```
{{ $section := where .Site.RegularPages "Section" "in" .Site.Params.fullmenu }}

    <div data-provide="shuffle">
      ...
        {{ range $section }}
           {{ if (not (eq .Params.title "full menu")) }}
             <li class="nav-item">
               <a class="nav-link" href="#" data-shuffle="button" data-group="{{ .Params.title }}">{{ .Params.title }}</a>
             </li>
           {{ end }}
        {{ end }}
      </ul>
      <div class="row gap-y gap-2" data-shuffle="list">
        {{ range $section }}
        {{ $title := .Params.title }}
          {{ range .Params.images }}
             <div class="col-3 col-lg-2" data-shuffle="item" data-groups="{{ $title }}">
               <a class="location-1" href="{{ .image }}" data-provide="lightbox">
                 <img class="img-menu" src="{{ .image }}" alt="screenshot">
                   <div class="location-detail">
                    <h6 class="f-white p-4">{{ humanize $title }}</h6>
                  </div>
                </a>
             </div>
          {{ end }}
        {{ end }}
      </div>
    </div>
```

> **{{ range .Params.images }}** used for nested images in markdown

#### example markdown (.md) file

```
---
title: french toast cubes
images:
  - image: /images/uploads/frenchtoast.jpg
  - image: /images/uploads/frenchtoast.jpeg
---

```

### Display data from data folder
To display list of menu from data folder (json file)

```
<section>
  {{ range $.Site.Data.menu}}
    <div class="banner-menu" data-parallax="/images/uploads/{{.img}}" data-overlay="2">
        ...
          {{ .name }}
        ...
    </div>
    ...
      {{ range .menu }}
        <div class="text-center text-uppercase p-5">
          <h5 class="ls-5">{{ .foodname}}</h5>
          <p class="f-poppins-light gray fs-13 text-center ">{{ .desc }}</p>
        </div>
        <div class="row f-poppins p-5">
          {{ range .list }}
          <div class="col-md-4 mb-5 pl-6 pr-6">
            <h5 class="ls-2 text-uppercase fw-800">{{ .name }}</h5>
            <p class="fs-15">{{ .desc }}</p>
          </div>
          {{ end }}
        </div>
      {{ end }}
    ...
  {{end}}
</section>
```

>{{ range $.Site.Data.menu}} will get the data inside the menu.json
>{{ range .menu }} will get all list of array inside the key name menu

**Example: ```menu.json```**
```
  {
    "name": "Food",
    "img": "food.jpg",
    "menu" :[
      {
        "foodname": "Appetizers",
        "desc": "",
        "list" : [
          {
            "name": "Fried Mashed Potato Balls",
            "desc": "Nacho beef. Herbed sour cream shots.",
            "price": "140"
          }
        ]
      },
      {
        "foodname": "Afforda Bowl Rice Meals",
        "desc": "",
        "list" : [
          {
            "name": "Truffled Sisig",
            "desc": "Scrambled egg. Spiced onion rings. Garlic rice.",
            "price": "140"
          }
        ]
      }
    ]
  }
```
