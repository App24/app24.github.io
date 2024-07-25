---
layout: default
permalink: /
---

{% include landing.html %}

<div class="card-columns m-3 mt-5">

{%- assign projects = site.projects | sort: 'weight' -%}

{% for project in projects %}

	{%- if project.pinned -%}
		{%- assign project_type  = "local" -%}
		{%- assign project_id    = project.name | slugify -%}
		{%- assign project_img   = project.image -%}
		{%- assign project_name  = project.name -%}
		{%- assign project_desc  = project.description -%}
		{%- assign project_tools = project.tools -%}

		{%- if project.external_url -%}
		  {%- assign project_url = project.external_url -%}
		{%- else -%}
		  {%- assign project_url = project.url | relative_url -%}
		{%- endif -%}

		{% include projects/project-card.html %}
	{%- endif -%}

  {% endfor %}
 </div>