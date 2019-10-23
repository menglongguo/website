---
layout: home
---

# Brent Yi
BA Computer Science 2019 @ UC Berkeley
<br />
<span id="email"></span>

[Github](https://github.com/brentyi){:target="_blank"}
&nbsp;&bull;&nbsp;
[LinkedIn](https://linkedin.com/in/brentyi){:target="_blank"}

----

## Selected Projects
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
    email += 'brentyi';
    email += '@berkeley.edu';
    // $('#email').attr('href', 'mailto:' + email);
    $('#email').text(email);
});
</script>
