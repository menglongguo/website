---
layout: home
---

# Menglong Guo
BS Mechanical Engineering 2015-2018 @ UC Berkeley
<br />
<span id="email"></span>

<!-- [Github](https://github.com/brentyi){:target="_blank"}
-->
&nbsp;&bull;&nbsp;
[LinkedIn](https://www.linkedin.com/in/menglong-guo-268aab175/){:target="_blank"}

----

## Research Projects and Papers
<ul>
{%- assign sorted_projects = site.projects | sort:"order" | reverse -%}
{%- for project in sorted_projects -%}
  {% if project.type== "Art" %}
  	<li>
    	<a href="{{project.url | relative_url}}">{{project.title}}</a>
    	<time datetime="{{project.year}}">{{project.year}}</time>
  	</li>
  {% endif %}
{%- endfor -%}
</ul>

## Class
<ul>
{%- assign sorted_projects = site.projects | sort:"order" | reverse -%}
{%- for project in sorted_projects -%}
  <li>
    <a href="{{project.url | relative_url}}">{{project.title}}</a>
    <time datetime="{{project.year}}">{{project.year}}</time>
  </li>
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

