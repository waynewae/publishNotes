---
layout: default
title: Github Pages
---

# Jekyll
## Local Jekyll server
### [Install](https://jekyllrb.com/docs/installation)
* Download & install [Rubyinstaller](https://rubyinstaller.org/downloads/)
* Run `ridk install`
* Execute `gem install jekyll bundler` in terminal to install Jekyll and Bundler
* `jekyll -v` to check if Jekyll installed properly
* Change location to repo root (Assume we alreay have a git repository) and run `bundle init` to create a new `Gemfile`
* Append following statement to `Gemfile`
```
gem "jekyll"
```
* Run `bundle`

### [Build & Run server](https://jekyllrb.com/docs/step-by-step/01-setup/)
* jekyll build
* jekyll serve
* go to [http://localhost:4000](http://localhost:4000)

> For Github Pages, there are some diifferent of hyperlink to local Jekyll server, so I don't use local server.

## Jekyll on Github Page
### Displaying an index of postsPermalink is not working on Github Page
According to [Displaying an index of posts](https://jekyllrb.com/docs/posts/#displaying-an-index-of-posts),the following statements should be work
```
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```
It's truly worked on local, but not on Gitgub Page, I found the solution in [Here](https://tinyurl.com/yafse4ly).
* Add `baseurl` to `_config.yml`
```
baseurl:/{$yourRepoName}
```
* Add `{{ site.baseurl }}` before your hyperlink
  * Case of `html`
  ```
  <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
  ```
  * Case of `md`
  ```
  ![]({{ site.baseurl }}/assets/2020-04-21-16-50-19.png)
  ```