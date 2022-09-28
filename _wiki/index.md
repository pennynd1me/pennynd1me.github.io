---
layout  : wikiindex
title   : wiki
toc     : true
public  : true
comment : false
updated : 2022-09-28 22:38:32 +0900
regenerate: true
---

## wiki items


---
## Diary
<div>
    <ul>
{% for post in site.posts %}
    {% if post.public == true %}
        <li>
            <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                {{ post.title }}
            </a>
        </li>
    {% endif %}
{% endfor %}
    </ul>
</div>
