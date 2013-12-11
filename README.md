# jekyll-tag-generator

TagGenerator for Jekyll

Generates tag/tags pages for posts with related tags.

![Screen shot](https://raw.github.com/Remiii/jekyll-tag-generator/master/_documentation/image1.png)<br />
Sample posts list with tags.

## Requirements

* Jekyll

## How to use

* Copy file `_plugins/tagGenerator.rb` into your `_plugins` folder within your Jekyll project.
* Create template for tag page into your `_layout/tag.html` within your Jekyll project.
* Create template for tags page into your `_layout/tags.html` within your Jekyll project.
* Add tags in your posts files.

Example template tag page `_layout/tag.html`:

```html
---
layout: default
---
<h1>{{ page.title }}</h1>
<h2>Posts</h2>
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
<h2>Related tags</h2>
{% for relatedtag in page.relatedtags %}
    <a href="/blog/tag/{{ relatedtag }}">{{ relatedtag }}</a>
{% endfor %}
```

Example template tags page `_layout/tags.html`:

```html
---
layout: default
---
<h1>Posts Tags</h1>
{% for tag in page.tags %}
    <a href="/blog/tag/{{ tag }}">{{ tag }}</a>
{% endfor %}
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

## Screen shot

![Screen shot](https://raw.github.com/Remiii/jekyll-tag-generator/master/_documentation/image1.png)<br />
Sample posts list with tags.

![Screen shot](https://raw.github.com/Remiii/jekyll-tag-generator/master/_documentation/image2.png)<br />
Sample posts list for a tag (tag.html).

![Screen shot](https://raw.github.com/Remiii/jekyll-tag-generator/master/_documentation/image3.png)<br />
Sample tags list (tags.html).

![Screen shot](https://raw.github.com/Remiii/jekyll-tag-generator/master/_documentation/image4.png)<br />
Sample post.

## Marks

You can find a sample in the following project: [remiii.github.com](https://github.com/Remiii/remiii.github.com).

## Tags

Jekyll, Ruby, Plugin, Tags, Tag, Related Tag

## License

jekyll-tag-generator is licensed under the MIT license (see LICENSE.md file).

## Author

@Remiii

