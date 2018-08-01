# preface and contents

Getting started with NodeCG can be overwhelming.
Here's my own quick guide to doing NodeCG stuff.

Questions, comments and changes are encouraged via GitHub issues and pull requests.

<ul>
  {% for page in site.pages %}
    <li>
      <a href="{{ site.url }}{{ page.url }}">{{ page.title }}</a>
    </li>
  {% endfor %}
</ul>
