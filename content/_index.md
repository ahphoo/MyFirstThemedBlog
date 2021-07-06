+++
title = "Algostructures"
sort_by = "date"
insert_anchor_links = "right"
+++

## Ever feel like this?

![alt text](https://img.devrant.com/devrant/rant/r_102813_Wx1Vb.jpg "Logo title")

I was inspired by [Rusty Algorithms](https://raymondsheng.github.io/) (now defunct 😢) to create a website for those who need a refresher on algorithms.

## Quick Tips and Tricks

* Data structures and Algorithm questions are tagged and sorted by topic on the left.
* Search for specific questions or answers using the search bar.
* Turn on light 💡 or dark 🦇 mode by clicking the square on the top left.

<!-- {{ youtube(id="dQw4w9WgXcQ") }} -->
<!-- ## 6 steps build your knowledge base/docs repo

1. Fork the repo 
2. delete demo content and add your own (I explain how to structure it below) 
3. change website name and domain in config.toml, also, change the title in _index.md in a root
4. connect your repo to dockerhub 
5. build your docker image or setup [autobuilds](https://docs.docker.com/docker-hub/builds/)
6. host a builded docker image on your own way

But, zola is amazing static site generator, so you feel free to

1. download all repo files
2. again delete demo content and add your own
3. change name and domain in config.toml/index.md
4. setup zola (win, linux, mac)
5. execute zola build
6. host builded html-output anywhere you want

Zola supports Netlify and other similar services, or you can decide to create your own CI/CD process. 

## How to structure your content

All your articles should be inside _content_ folder. Any images, videos, other static files should be inside _static._ 

### Folders

Every folder should contains _index.md like 

```toml
+++
title = "Docsascode title"
description = "Description is optional"
sort_by = "date" # sort by weight or date
insert_anchor_links = "right" # if you want § next to headers
+++
```
Each folder is the section of the website, it means if you create folder foo it will be seen as _yoursitedomain.com/foo_

The theme supports folders in folders and articles + folders in one folder (see an example inside _content_). So you can store inside folder another folders and describe in index some specific details. 

### Pages 

A page should be started by 

```toml
+++
title = "File and folders in folder"
date = 2020-01-18 # or weight 
description = "Description"
insert_anchor_links = "right"

[taxonomies] #all taxonomies is optional
tags = ["newtag"]
authors = ["John Doe"]
+++
```

Zola allows to create drafts:

```toml 
draft = true
```

Also, by default you have two taxonomies: _tags_ and _authors_. It's optional, not necessary to use it on all pages. And you can add your own taxonomy:

1. Copy tags or authors folder and rename it to your taxonomy
2. Add your taxonomy to config.toml
3. Add to page.html template code like 

```rust
    {% if page.taxonomies.yourtaxonomynameplural %}
      <ul>
      {% for tag in page.taxonomies.yourtaxonomynameplural %}
        <li><a href="{{ get_taxonomy_url(kind="yourtaxonomynameplural", name=yourtaxonomyname) | safe }}" >{{ yourtaxonomyname }}</a></li>
      {% endfor %}
      </ul>
    {% endif %}
``` -->
