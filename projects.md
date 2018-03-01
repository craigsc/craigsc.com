---
layout: page-10
title: Projects
permalink: /projects
navigation_weight: 1
---
{% assign projects = site.projects | sort: 'weight' %}
{% for project in projects %}
{% if project.link %}
  {% assign primary_link = project.link %}
{% else %}
  {% assign primary_link = project.github %}
{% endif %}
<div class="row mb-5 align-items-center">
  <div class="col-sm-4 text-center">
    {% if project.image_src %}
      <a href="{{ primary_link }}" target="_blank">
        <div class="img-thumbnail">
        <div class="image-box rounded">
          <img class="img-fluid{% if project.image_landscape %} landscape{% endif %}" src="{{ project.image_src }}" {% if project.image_style %}style="{{ project.image_style }}"{% endif %} /> 
        </div>
        </div>
      </a>
    {% else %}
    <img class="rounded img-fluid" src="http://via.placeholder.com/350x350" /> 
    {% endif %}
  </div>
  <div class="col-sm-8 small">
    <h5>
      {{ project.name }}
      {% if project.tagline %}
        <br><small markdown="1">{{ project.tagline }}</small>
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
