# jekyll-tag-generator

TagGenerator for Jekyll


Generates tags pages for posts with related tags.

## Requirements

* Jekyll

## How to use

* Copy file `_plugins/tagGenerator.rb` into your `_plugins` folder within your Jekyll project.
* Create template for tag page into your `_layout/tag.html` within your Jekyll project.
* Add tags in your posts files.

Example template tag page `_layout/tag.html`:

```html
---
layout: default
---
<h1>{{ page.title }}</h1>
{% for post in site.posts %}
    {% for tag in post.tags %}
        {% if tag == page.tag %}
            <div>{{ post.date | date: "%b %e, %Y" }}</div>
                <h2><a title="{{ post.title }}" href="{{ post.url }}">{{ post.title | truncate: 50 }}</a></h2>
                <div>
                    {% for alltag in post.tags %}
                        <a href="/blog/tag/{{ alltag }}">{{ alltag }}</a>
                    {% endfor %}
                </div>
                <p>{{ post.content | strip_html | truncate: 400 }}</p>
                <p><a title="{{ post.title }}" href="{{ post.url }}">Read more</a></p>
            </div>
        {% endif %}
    {% endfor %}
{% endfor %}
<h3>Related tags</h3>
<div>
    {% for relatedtag in page.relatedtags %}
        <a href="/blog/tag/{{ relatedtag }}"><span class="label label-info">{{ relatedtag }}</span></a>
    {% endfor %}
</div>
</div>
```

Example Post Configuration:

```
layout: post
title: "Hello world"
tags:
    - sample
    - ruby
    - plugin
```

## Marks

You can find a sample in the following project : [remiii.github.com][https://github.com/Remiii/remiii.github.com].

## Tags

Jekyll, Ruby, Plugin, Tag, Related Tag

## License

mydotfiles is licensed under the MIT license (see LICENSE.md file).

## Author

@Remiii

