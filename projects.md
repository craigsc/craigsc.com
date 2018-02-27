---
layout: page-10
title: Projects
permalink: /projects
navigation_weight: 1
---
{% assign projects = site.projects | sort: 'weight' %}
{% for project in projects %}
<div class="row mb-5 align-items-center">
  <div class="col-sm-4 text-center">
    {% if project.image_src %}
    <img class="rounded img-fluid" src="{{ project.image_src }}" /> 
    {% else %}
    <img class="rounded img-fluid" src="http://via.placeholder.com/350x350" /> 
    {% endif %}
  </div>
  <div class="col-sm-8 small">
    <h5>
      {{ project.name }}
      {% if project.tagline %}
        <br><small>{{ project.tagline }}</small>
      {% endif %}
    </h5>
    <div>
      {{ project.content }}
    </div>
    <div> 
      {% if project.link %}
      {% assign link = project.link | remove: 'https://' | remove: 'http://' | remove: 'www.' %}
      Link: <a href="{{ project.link }}" target="_blank">{{ link }}</a>
      {% endif %}
      {% if project.github %}
      {% assign github = project.github | remove: 'https://' | remove: 'http://' | remove: 'www.' %}
      {% if project.link %}<br>{% endif %}
      Code: <a href="{{ project.github }}" target="_blank">{{ github }}</a>
      {% endif %}
    </div>
  </div>
</div>
{% endfor %}
<div class="text-center py-3" markdown="1">
  This list is incomplete!<br>You can find many more of my projects on [GitHub](https://github.com/craigsc){:target="_blank"}.
</div>
{% include email_upsell.html %}
