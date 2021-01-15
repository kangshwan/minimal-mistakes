---
title: "posting error"
date: "2020-05-31-23:15"
categories: github jekyll liquidtag
---

Github blog posting관련 문제
=====
django에 대해서 공부한걸 올리다가 posting에 문제가 발생했다.  
오류내용은  
```
The page build failed for the `master` branch with the following error:  

The tag `block` on line 21 in `_posts/2020-05-22-djangoreview.md` is not a recognized Liquid tag.  
```
{% raw %}  
오류를 다시보니, 아마 django에서 사용하는 것을 이야기 하기위해 ```{% block %}```등을 사용했는데, 이가 문제가 된것.  

왜그런지 찾아보니 GitBlog는 [Jekyll](https://jekyllrb-ko.github.io/)기반의 블로그 엔진을 지원하는데 liquid tag가 사용되기 때문.  
이 Jekyll에서 template를 표현하기 위해 사용되는 태그들인데, 결국 ```{%```와 ```%}```때문에 생긴 오류였다.  
이를 해결하기 위해서는 해당 ```{% %}```들을 표현하고 싶을때 raw와 endraw를 ```{% %}```안에 넣고  앞 뒤로 붙여주면 해결된다.  
{% endraw %}


참고
=====
<https://help.github.com/en/github/working-with-github-pages/troubleshooting-jekyll-build-errors-for-github-pages-sites>
<https://ivorycirrus.github.io/TIL/jekyll-liquid-tag-error>
