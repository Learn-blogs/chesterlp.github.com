---
layout: page
title: html,css,js,Jquery
tagline: Front-End Developer
---
{% include JB/setup %}


前端开发初学者，这里存放工作中的一些代码片段: [google](http://google.com)

## 简易下拉菜单

In `_config.yml` remember to specify your own data:

/*
Author: mg12
Feature: MenuList
Update: 2009/12/13
Tutorial URL: http://www.neoease.com/wordpress-menubar-6/
*/

var mouseover_tid = [];
var mouseout_tid = [];

jQuery(document).ready(function(){
    jQuery('#menus > li').each(function(index){
		jQuery(this).hover(
        
			function(){
				var _self = this;
				clearTimeout(mouseout_tid[index]);
				mouseover_tid[index] = setTimeout(function() {
					jQuery(_self).find('ul:eq(0)').fadeIn(200);
				}, 400);
			},

			function(){
				var _self = this;
				clearTimeout(mouseover_tid[index]);
				mouseout_tid[index] = setTimeout(function() {
					jQuery(_self).find('ul:eq(0)').fadeOut(200);
				}, 400);
			}

		);
	});
});

The theme should reference these variables whenever needed.
    
## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


