---
layout: page
comments : false
---
{% include JB/setup %}

<ul class="posts">

  {% for post in site.posts %}
    <li>
      <article>
        <time datetime="{{ post.date | date: "%Y-%m-%d" }}" title="{{ post.date }}">
          <span class="day">{{ post.date | date: "%d" }}</span>
          <span class="month">{{ post.date | date: "%b" }}</span>
          <span class="year">{{ post.date | date: "%Y" }}</span>
        </time>
        <div class="article">
          <h1><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h1>

          {% if post.image %}
          <img src="post.image" class="featured-image">
          {% endif %}
          
          {% if post.description %}
          <p>{{ post.description }}</p>
          {% endif %}

          {% unless post.tags == empty %}
            <ul class="icon-tags tags">
            {% assign tags_list = post.tags %}  
            {% if tags_list.first[0] == null %}
              {% for tag in tags_list %} 
                <li><a href="{{ BASE_PATH }}{{ site.JB.tags_path }}#{{ tag }}-ref">{{ tag }}</a></li>
              {% endfor %}
            {% else %}
              {% for tag in tags_list %} 
                <li><a href="{{ BASE_PATH }}{{ site.JB.tags_path }}#{{ tag[0] }}-ref">{{ tag[0] }}</a></li>
              {% endfor %}
            {% endif %}
            </ul>
          {% endunless %}
        </div>
      </article>
    </li>
  {% endfor %}

</ul>
