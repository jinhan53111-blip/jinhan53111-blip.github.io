---
layout: default
---

<section class="home">

  <div class="home-eyebrow">
    REINFORCEMENT LEARNING NOTES
  </div>

  <h1 class="home-title">
    Reinforcement Learning<br>
    & Stochastic Processes
  </h1>

  <p class="home-description">
    Notes on reinforcement learning, stochastic processes,
    and their mathematical foundations.
  </p>

  <div class="home-divider"></div>


  <section class="notes-section">

    <div class="notes-label">
      01 / STUDY NOTES
    </div>

    <h2 class="notes-heading">
      Latest Notes
    </h2>

    <ul class="post-list">

      {% for post in site.posts %}

      <li class="post-list-item">

        <a class="post-list-link" href="{{ post.url | relative_url }}">

          <div>

            <div class="post-list-number">
              NOTE / {{ forloop.index | prepend: '0' }}
            </div>

            <h3 class="post-list-title">
              {{ post.title }}
            </h3>

            {% if post.description %}
            <p class="post-list-description">
              {{ post.description }}
            </p>
            {% endif %}

          </div>

          <time class="post-list-date">
            {{ post.date | date: "%Y.%m.%d" }}
          </time>

        </a>

      </li>

      {% endfor %}

    </ul>

  </section>

</section>
