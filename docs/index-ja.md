---
title: Requests for Startups
lang: ja
alternate_url: /
---

<section class="hero">
  <div>
    <h1>Requests for Startups</h1>
    <p>Pull request で投稿されたスタートアップアイデアの一覧です。各 request は、創業者が調査し、検証し、プロダクトにできるかを考えるための具体的な問いです。</p>
  </div>
  <img src="{{ '/icon.png' | relative_url }}" alt="卵からかえるひよこ">
</section>

<section aria-label="アイデア一覧">
  <div class="toolbar">
    <input class="search-input" id="idea-search" type="search" placeholder="タイトル、概要、タグでアイデアを検索" aria-label="アイデアを検索">
    <div class="count" id="idea-count"></div>
  </div>

  <div class="idea-grid" id="idea-grid">
    {% assign ideas = site.pages | where: "idea", true | where: "lang", page.lang | sort: "date" | reverse %}
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
        まだ公開済みのアイデアはありません。<code>docs/</code> 配下に 1 アイデア 1 Markdown ファイルを作り、front matter に <code>idea: true</code> と <code>lang: ja</code> を入れてください。
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

    count.textContent = `${visible}件のアイデア`;
  }

  if (input && count) {
    input.addEventListener("input", updateIdeaList);
    updateIdeaList();
  }
</script>
