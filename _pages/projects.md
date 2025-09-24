---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: false
nav_order: 2
display_categories: [work, fun]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.projects | where: "category", category -%}
  {%- if categorized_projects.size > 0 -%} <!-- 检查分类下是否有项目 -->
    {%- assign sorted_projects = categorized_projects | sort: "key" %}
    <!-- Generate cards for each project -->
    {% if page.horizontal -%}
    <div class="container">
      <div class="row row-cols-2">
      {%- for project in sorted_projects -%}
        {% include projects_horizontal.html %}
      {%- endfor %}
      </div>
    </div>
    {%- else -%}
    <div class="grid">
      {%- for project in sorted_projects -%}
        {% include projects.html %}
      {%- endfor %}
    </div>
    {%- endif -%}
  {%- else -%} <!-- 分类下无项目时的提示 -->
    <p>暂无 {{ category }} 类项目</p>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign all_projects = site.projects -%}
  {%- if all_projects.size > 0 -%} <!-- 检查是否有项目 -->
    {%- assign sorted_projects = all_projects | sort: "importance" -%}
    <!-- Generate cards for each project -->
    {% if page.horizontal -%}
    <div class="container">
      <div class="row row-cols-2">
      {%- for project in sorted_projects -%}
        {% include projects_horizontal.html %}
      {%- endfor %}
      </div>
    </div>
    {%- else -%}
    <div class="grid">
      {%- for project in sorted_projects -%}
        {% include projects.html %}
      {%- endfor %}
    </div>
    {%- endif -%}
  {%- else -%} <!-- 无项目时的提示 -->
    <p>暂无项目内容</p>
  {%- endif -%}
{%- endif -%}
</div>
