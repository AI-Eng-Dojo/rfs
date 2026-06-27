---
title: Requests for Startups
---

<section class="hero">
  <div>
    <h1>Requests for Startups</h1>
    <p>Startup ideas submitted through pull requests. Each request is a focused prompt for founders to investigate, validate, and build from.</p>
  </div>
  <img src="{{ '/icon.png' | relative_url }}" alt="A chick hatching from an egg">
</section>

<section aria-label="Idea list">
  <div class="toolbar">
    <input class="search-input" id="idea-search" type="search" placeholder="Search ideas by title, summary, or tag" aria-label="Search ideas">
    <div class="count" id="idea-count"></div>
  </div>

  <div class="idea-grid" id="idea-grid">
    {% assign ideas = site.pages | where_exp: "page", "page.idea == true" | sort: "date" | reverse %}
    {% for idea in ideas %}
      <article
        class="idea-card"
        data-title="{{ idea.title | default: '' | downcase | escape }}"
        data-summary="{{ idea.summary | default: '' | downcase | escape }}"
        data-tags="{{ idea.tags | join: ' ' | downcase | escape }}"
      >
        <h2><a href="{{ idea.url | relative_url }}">{{ idea.title | escape }}</a></h2>
        {% if idea.summary %}
          <p>{{ idea.summary | escape }}</p>
        {% endif %}
        <div class="meta">
          {% if idea.date %}
            <span class="tag">{{ idea.date | date: "%Y-%m-%d" }}</span>
          {% endif %}
          {% for tag in idea.tags %}
            <span class="tag">{{ tag | escape }}</span>
          {% endfor %}
        </div>
      </article>
    {% else %}
      <div class="empty-state">
        No ideas have been published yet. Add one Markdown file per idea under <code>docs/</code> with <code>idea: true</code> in its front matter.
      </div>
    {% endfor %}
  </div>
</section>

<script>
  const input = document.querySelector("#idea-search");
  const cards = Array.from(document.querySelectorAll(".idea-card"));
  const count = document.querySelector("#idea-count");

  function updateIdeaList() {
    const query = input.value.trim().toLowerCase();
    let visible = 0;

    for (const card of cards) {
      const haystack = [
        card.dataset.title,
        card.dataset.summary,
        card.dataset.tags,
      ].join(" ");
      const match = haystack.includes(query);
      card.hidden = !match;
      if (match) visible += 1;
    }

    count.textContent = `${visible} idea${visible === 1 ? "" : "s"}`;
  }

  if (input && count) {
    input.addEventListener("input", updateIdeaList);
    updateIdeaList();
  }
</script>
