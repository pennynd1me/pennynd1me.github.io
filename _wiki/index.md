---
layout  : wikiindex
title   : wiki
toc     : true
public  : true
comment : false
updated : 2022-09-28 22:10:23 +0900
regenerate: true
---

## wiki items

* [[작성-테스트]]
* [[post-test]]
	* [[나는-왜-안되는걸까]]
	

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
