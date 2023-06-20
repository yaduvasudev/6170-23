---
layout: schedule
permalink: /lectures.html
title: lectures
subtitle: Lecture schedule
nav: true
nav_order: 3
---

{% assign tut_num = 0 %}
{% assign mq_num = 0 %}
{% assign q_num = 0 %}
{% assign endsem = 0 %}

{% for item in site.data.lec %}
{% assign lecture = item %}
{% if lecture.tutorial %}
{% assign tut_num = tut_num | plus:1 %}
{% elsif lecture.miniquiz %}
{% assign mq_num = mq_num | plus:1 %}
{% elsif lecture.quiz %}
{% assign q_num = q_num | plus:1 %}
{% elsif lecure.endsem %}
{% assign endsem = endsem | plus:1 %}
{% endif %}
<tr>
<td>
{% if lecture.contents %}
<strong>Lecture #{{ forloop.index | minus:tut_num | minus:q_num | minus:mq_num | minum:endsem }}</strong>
<br/>
{% elsif lecture.tutorial %}
<strong style="background:#e6ffe6;"> Tutorial #{{ tut_num }}</strong>
<br/>
{% elsif lecture.miniquiz %}
<strong style="background:#e6ffe6;"> Mini-quiz #{{ mq_num }}</strong>
<br/>
{% elsif lecture.quiz %}
<strong style="background:#e6ffe6;"> Quiz #{{ q_num }}</strong>
<br/>
{% elsif lecture.endsem %}
<strong style="background:#e6ffe6;"> End-sem </strong>
{% endif %}
{{ lecture.date }} </td>
<td>
{% if lecture.tutorial %}
{{ lecture.tutorial }}
{% elsif lecture.miniquiz %}
{{ lecture.miniquiz }}
{% elsif lecture.quiz %}
{{ lecture.quiz }}
{% elsif lecture.endsem %}
{{ lecture.endsem }}
{% endif %}
{{ lecture.contents }}<br>
{% if lecture.slides %}
[<a href = "{{ lecture.slides }}">slides</a>]
{% endif %}
{% if lecture.notes %}
[<a href = "{{ lecture.notes }}">notes</a>]
{% endif %}
</td>
<td>
<ul>
{% for ref in lecture.references %}
<li> {{ ref }} </li>
{% endfor %}
</ul>
</td>
<td>
{% for itm in lecture.misc %}
{{ itm }} <br>
{% endfor %}
</td>
</tr>
{% endfor %}
