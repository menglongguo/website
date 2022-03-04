---
layout: home
---

# Menglong Guo

BS Mechanical Engineering @ UC Berkeley (Fall 15 - Fall 18)<br /> MS Mechanical
Engineering @ MIT (Fall 20 - Fall 22) Advisor: Sangbae Kim, Biomimetic Robotics Lab

<span id="email"></span>

&nbsp;&bull;&nbsp;
[LinkedIn](https://www.linkedin.com/in/menglong-guo-268aab175/){:target="\_blank"}

---

## Research and Papers

<ul>
{%- assign sorted_projects = site.projects | sort:"order" | reverse -%}
{%- for project in sorted_projects -%}
  {% if project.type== "research" %}
    <li>
      <a href="{{project.url | relative_url}}">{{project.title}}</a>
      <time datetime="{{project.year}}">{{project.year}}</time>
    </li>
  {% endif %}
{%- endfor -%}
</ul>

## Fun Projects

<ul>
{%- assign sorted_projects = site.projects | sort:"order" | reverse -%}
{%- for project in sorted_projects -%}
  {% if project.type== "class" %}
    <li>
      <a href="{{project.url | relative_url}}">{{project.title}}</a>
      <time datetime="{{project.year}}">{{project.year}}</time>
    </li>
  {% endif %}
{%- endfor -%}
</ul>

## Misc

<ul>
{%- assign sorted_projects = site.projects | sort:"order" | reverse -%}
{%- for project in sorted_projects -%}
  {% if project.type== "misc" %}
    <li>
      <a href="{{project.url | relative_url}}">{{project.title}}</a>
      <time datetime="{{project.year}}">{{project.year}}</time>
    </li>
  {% endif %}
{%- endfor -%}
</ul>

<script>
$(function() {
  var email = '';
  email += 'm.guo';
  email += '@berkeley.edu';
  // $('#email').attr('href', 'mailto:' + email);
  $('#email').text(email);
});
</script>
