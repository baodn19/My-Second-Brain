---
title: "[[{{title | replace(':', ' -') | replace('/', '-') | replace('"', '')}}]]"
year: {{date | format("YYYY")}} 
authors: {{authors}}
categories:
  - "[[Research References]]"
tags: 
{% for t in tags -%} 
  - {{t.tag | replace(" ", "-")}} 
{% endfor -%}
---

{% for attachment in attachments %}{% if attachment.path and ".pdf" in attachment.path %}Zotero PDF Link: [[Zotero Attachments/{{ attachment.path | replace(r/^.*[\\\/]/, "") }}]]{% endif %}{% endfor %}
Related: {% for relation in relations | selectattr("citekey") %} [[{{relation.citekey}}]]{% if not loop.last %}, {% endif%} {% endfor %} 
# In-text annotations 
{% for annotation in annotations -%} 
{%- if annotation.annotatedText -%} 
{% if annotation.color %} <mark class="hltr-{{annotation.colorCategory | lower}}">"{{annotation.annotatedText | safe}}"</mark> {% else %} {{annotation.type | capitalize}} {% endif %}[Page {{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}) 
{%- endif %} 
{% if annotation.comment %} 
{{annotation.comment | safe}} [Page {{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}) 
{% endif %} 
{%- if annotation.imageRelativePath %} 
![[{{annotation.imageRelativePath}}]] 
{%- endif %} {% if annotation.allTags %} 
{{annotation.allTags}} 
{% endif %} 
{% endfor -%}