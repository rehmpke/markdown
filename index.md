---
layout: default
baseurl: '../'
title: Home page
description: 'testing home page'
---

<div class="container position__offset-fixed-nav">
  <div class="row">
    <div class="col">
      <section class="latest-news-widget--rollup__section-margin">
        <h2 class="latest-news-widget__latest__h latest-news-widget__latest__h--no-underline typography__latest-news-widget__h2"><span class="latest-news-widget__red-underline">All News
          <span id="todaysDate" class="latest-news-widget__latest__date"></span></span>
        </h2>
        <ol id="jsTeaseList" class="latest-news-widget--rollup__latest__tease-group">

          {% for post in site.posts limit:10 %}

            {% assign current_date = site.time | date: "%Y-%m-%d %H:%M" %}
            {% assign post_expiration = post.expire_date | date: "%Y-%m-%d %H:%M" %}
            {% if current_date < post_expiration %}

              {% if post.video_content == true %}
                {% if forloop.first == true %}
                  <li class="latest-news-widget__latest__tease latest-news-widget__latest__tease--default latest-news-widget__latest__tease--has-image latest-news-widget--rollup__latest__tease-width">
              <!--  Tease is active   -->
                    <a id="jsTeaseLink{{ forloop.index }}" class="latest-news-widget__latest__tease__link js-hp-latest-tease-link tease-is-active" href="{{ post.url }}" data-image="{{ post.image }}"
                      data-image-alt="" tabindex="0" data-tease-type="" data-index="{{ forloop.index0 }}" aria-hidden="true">
                      <div class="latest-news-widget__latest__tease__hgroup">
                        <h3 class="latest-news-widget__latest__tease__overline typography__latest-news-widget__rollup-list-h">
                        <span class="latest-news-widget__latest__tease__number">{{ forloop.index }}</span>{{ post.title }}</h3>
                        <p class="latest-news-widget__latest__tease__h">{{ post.article_lead }}</p>
                      </div>
                      <div class="latest-news-widget__latest__tease__img-mod latest-news-widget__latest__tease__img-mod--default" style="background-image: url('https://img.youtube.com/vi/{{  post.video_link | remove: "https://youtu.be/" }}/hqdefault.jpg')">
                      </div>
                    </a>
                  </li>

                {% else %}

                  <li class="latest-news-widget__latest__tease latest-news-widget__latest__tease--default latest-news-widget__latest__tease--has-image latest-news-widget--rollup__latest__tease-width">
              <!--  Tease is active   -->
                    <a id="jsTeaseLink{{ forloop.index }}" class="latest-news-widget__latest__tease__link js-hp-latest-tease-link" href="{{ post.url }}" data-image="{{ post.image }}"
                      data-image-alt="" tabindex="0" data-tease-type="" data-index="{{ forloop.index0 }}" aria-hidden="true">
                      <div class="latest-news-widget__latest__tease__hgroup">
                        <h3 class="latest-news-widget__latest__tease__overline typography__latest-news-widget__rollup-list-h">
                        <span class="latest-news-widget__latest__tease__number">{{ forloop.index }}</span>{{ post.title }}</h3>
                        <p class="latest-news-widget__latest__tease__h">{{ post.article_lead }}</p>
                      </div>
                      <div class="latest-news-widget__latest__tease__img-mod latest-news-widget__latest__tease__img-mod--default" style="background-image: url('https://img.youtube.com/vi/{{  post.video_link | remove: "https://youtu.be/" }}/hqdefault.jpg')">
                      </div>
                    </a>
                  </li>
                {% endif %}
              {% else %}
                {% if forloop.first == true %}
                  <li class="latest-news-widget__latest__tease latest-news-widget__latest__tease--default latest-news-widget__latest__tease--has-image latest-news-widget--rollup__latest__tease-width">
              <!--  Tease is active   -->
                    <a id="jsTeaseLink{{ forloop.index }}" class="latest-news-widget__latest__tease__link js-hp-latest-tease-link tease-is-active" href="{{ post.url }}" data-image="{{ post.image }}"
                      data-image-alt="" tabindex="0" data-tease-type="" data-index="{{ forloop.index0 }}" aria-hidden="true">
                      <div class="latest-news-widget__latest__tease__hgroup">
                        <h3 class="latest-news-widget__latest__tease__overline typography__latest-news-widget__rollup-list-h">
                        <span class="latest-news-widget__latest__tease__number">{{ forloop.index }}</span>{{ post.title }}</h3>
                        <p class="latest-news-widget__latest__tease__h">{{ post.article_lead }}</p>
                      </div>
                      <div class="latest-news-widget__latest__tease__img-mod latest-news-widget__latest__tease__img-mod--default" style="background-image: url('{{ page.baseurl }}{{ post.image }}')">
                      </div>
                    </a>
                  </li>

                {% else %}

                  <li class="latest-news-widget__latest__tease latest-news-widget__latest__tease--default latest-news-widget__latest__tease--has-image latest-news-widget--rollup__latest__tease-width">
              <!--  Tease is active   -->
                    <a id="jsTeaseLink{{ forloop.index }}" class="latest-news-widget__latest__tease__link js-hp-latest-tease-link" href="{{ post.url }}" data-image="{{ post.image }}"
                      data-image-alt="" tabindex="0" data-tease-type="" data-index="{{ forloop.index0 }}" aria-hidden="true">
                      <div class="latest-news-widget__latest__tease__hgroup">
                        <h3 class="latest-news-widget__latest__tease__overline typography__latest-news-widget__rollup-list-h">
                        <span class="latest-news-widget__latest__tease__number">{{ forloop.index }}</span>{{ post.title }}</h3>
                        <p class="latest-news-widget__latest__tease__h">{{ post.article_lead }}</p>
                      </div>
                      <div class="latest-news-widget__latest__tease__img-mod latest-news-widget__latest__tease__img-mod--default" style="background-image: url('{{ page.baseurl }}{{ post.image }}')">
                      </div>
                    </a>
                  </li>
                {% endif %}
              {% endif %}

            {% endif %}

          {% endfor %}
        </ol>
      </section>
    </div>
  </div>
  <div class="row">
    <div class="col text-center">
      <a style="margin-top: 15px" href="{{ page.baseurl }}archive/" class="btn btn-primary">View older articles</a>
    </div>
  </div>
</div>
