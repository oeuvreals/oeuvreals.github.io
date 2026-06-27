---
title: "Music"
layout: single
permalink: /music/
author_profile: false
classes: wide
---

<style>
.music-gallery { margin-top: 0.5rem; }
.music-year { margin-bottom: 1.75rem; }
.music-year__label {
  font-size: 0.9rem;
  font-weight: 400;
  color: #6b7a90;
  letter-spacing: 0.06em;
  margin: 0 0 0.6rem;
  border: 0;
  padding: 0;
}
.music-row {
  display: flex;
  flex-wrap: nowrap;
  gap: 1rem;
  overflow-x: auto;
  padding-bottom: 0.4rem;
  min-height: 1rem;
}
.music-row::-webkit-scrollbar { height: 6px; }
.music-row::-webkit-scrollbar-thumb { background: #24395a; border-radius: 3px; }
.music-gallery .album {
  flex: 0 0 auto;
  width: 150px;
  margin: 0;
  display: flex;
  flex-direction: column;
}
.music-gallery .album__cover {
  width: 150px;
  height: 150px;
  object-fit: cover;
  background: #16273f;
  border-radius: 6px;
  display: block;
}
.music-gallery .album__title {
  display: block;
  width: 150px;
  font-size: 0.78rem;
  color: #e6e9ef;
  margin-top: 0.4rem;
  line-height: 1.25;
  overflow-wrap: anywhere;
  word-break: break-word;
}
.music-gallery .album__artist {
  display: block;
  width: 150px;
  font-size: 0.72rem;
  color: #8a96a8;
  overflow-wrap: anywhere;
  word-break: break-word;
}
</style>

<div class="music-gallery">
{% assign years = site.data.music | sort: "year" | reverse %}
{% for entry in years %}<section class="music-year">
<h2 class="music-year__label">{{ entry.year }}</h2>
<div class="music-row">
{% for album in entry.albums %}<figure class="album"><img class="album__cover" src="{{ album.cover }}" alt="{{ album.title }}" loading="lazy"><span class="album__title">{{ album.title }}</span><span class="album__artist">{{ album.artist }}</span></figure>
{% endfor %}</div>
</section>
{% endfor %}</div>
