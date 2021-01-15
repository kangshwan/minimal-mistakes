---
title: "Django Review"
date: "2020-05-22-14:26"
categories: django python
---

혼자 끄적인 Django 리뷰
===========  
View에서 template로 context넘겨줄때 여러개의 context 보내는법.  

get_context_data(self, **kwargs)를 overriding한다.  
```python
    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)
        context['article_list'] = Article.objects.all()
        context["year_list"] = Article.objects.values('pub_date').distinct()
        return context
```
요런식으로 진행.  
context들은 template에서 정해준 이름(ex, context['article_list'] 여기 article_list가 이름이다!)  
을 사용하여 입맛대로 꾸밀 수 있다.


```.order_by('something')```에서 something앞에 -를 붙여주면 내림차순, 없다면 오름차순이다.  
{% raw %}
template를 사용할때  
```{% block 블록이름 %}```이 굉장히 유용한것같다 ```{% endblock %}```  
block을 사용하면 기본 template를 유지하면서 내용을 빠르게 변화시켜갈 수 있다.  

```{% ifchanges %}```를 이용하여 중복을 제거할수있다.  
```{% endifchanges %}```와 세트.
{% endraw %}
models에 DB에 저장할 것들을 정리해 둔다.  
views에 어떻게 view를 구성할지(template) 정해두고  
urls로 view와 url을 연결짓는다.  

