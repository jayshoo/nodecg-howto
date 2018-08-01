Getting started with NodeCG can be overwhelming.
Here's my own quick guide to doing NodeCG stuff.

Questions, comments and changes are encouraged via GitHub issues and pull requests.

## layout of this guide

<ul>
  <li>item 1</li>
  {% for page in site.pages %}
    <li>
      <a href="{{ page.url }}">{{ page.title }}</a>
    </li>
  {% endfor %}
</ul>
