---
layout: page
title: Vocab
permalink: /vocab/
---

Here I will keep some important CS Vocab

- **Primitives**: A type of data in Java which is basic and does not have any properties/methods (ie ``int``, ``boolean``, ``double``)
- **Wrapper Classes**: Classes that allow primitives to be used in places where only classes are allowed such as generics (ie. ``Integer``, ``Boolean``, ``Double``, ``String``)
- **Static vs Dynamic Methods**: Static methods are simply called on the class while dynamic methods are called on an INSTANCE of the class (an object)
- **Constructors**: These are special methods that are called when an object of a class is created.

# Collegeboard Posts
<!-- Sort posts by rank, then date -->
{% assign grouped_posts = site.posts | group_by: "sticky_rank" | sort: "name", "last" %}
{% assign sticky_posts = ''|split:'' %}
{% assign non_sticky_posts = '' | split:'' %}


{% for gp in grouped_posts %}
{%- if gp.name == "" -%}
{% assign non_sticky_posts = gp.items | sort: "date" | reverse %}
{%- else %}
{% assign sticky_posts = sticky_posts | concat: gp.items %}
{%- endif -%}
{% endfor %}

<!-- Assemble final sorted posts array -->
{% assign sticky_posts = sticky_posts | sort: "sticky_rank", "last" %}
{% assign posts = sticky_posts | concat: non_sticky_posts %}

{%- if posts.size > 0 -%}
{%- if page.list_title -%}
<h2 class="post-list-heading">{{ page.list_title }}</h2>
{%- endif -%}
<ul class="post-list">
{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
{%- for post in posts -%}
<li>
{% if post.categories contains "cb" %}
    {%- include post_list.html -%}
{%- endif -%}
</li>
{%- endfor -%}
</ul>

{%- endif -%}