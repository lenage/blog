{% for post in category\_posts %}
1.{{ post.date | date:“%Y-%m-%d” }}

{{ post.title }}

{% endfor %}
