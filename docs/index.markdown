---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<h2>{{ site.data.lectures.lectures_title }}</h2>
<ol>
   {% for item in site.data.lectures.lectures %}
      <li><a href="{{ item.url }}">{{ item.title }}</a></li>
   {% endfor %}
</ol>

