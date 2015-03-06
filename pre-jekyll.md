---
layout: page
title: "Pre Jekyll Content"
---

These are all of the posts I made while my website was running Drupal.  For simplicity I've decided to use a simple list of links rather than trying to setup excerpts from each post.  That and currently (2015-03-05) Jekyll Pagination doesn't work with collections (mentioned on <http://jekyllrb.com/docs/pagination/> in the note 'Pagination does not support tags or categories') so the page would get even longer.

While working on the migration of content I noticed I've missed some spelling mistakes or poor grammar.  For the moment I've not corrected the mistakes.  I was using a WYSIWYG editor (I think CKEditor) in Drupal so in theory it should have included spell checking. 

{% for post in site.content reversed %}
  [{{post.title}}]({{post.url}})<span> - {{post.date | date: "%d %b %Y"}}</span>{: .post-meta}
{% endfor %}