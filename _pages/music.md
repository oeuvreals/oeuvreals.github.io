---
title: "Music"
layout: single
permalink: /music/
author_profile: false
classes: wide
---

<style>
.music-gallery { margin-top: 0.5rem; }
.music-year { margin-bottom: 2.25rem; }
.music-year__label {
  display: flex;
  align-items: center;
  gap: 0.9rem;
  font-size: 0.72rem;
  font-weight: 500;
  color: #6b7a90;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  margin: 0 0 0.9rem;
  border: 0;
  padding: 0;
}
.music-year__label::after {
  content: "";
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, #24395a, transparent);
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
  border-radius: 8px;
  display: block;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
  transition: transform .35s cubic-bezier(.2,.7,.2,1), box-shadow .35s ease;
}
.music-gallery .album:hover .album__cover {
  transform: translateY(-4px) scale(1.02);
  box-shadow: 0 12px 26px rgba(0, 0, 0, 0.45);
}
.music-gallery .album__title {
  display: block;
  width: 150px;
  font-size: 0.78rem;
  color: #e6e9ef;
  margin-top: 0.5rem;
  line-height: 1.25;
  overflow-wrap: anywhere;
  word-break: break-word;
  transition: color .18s ease;
}
.music-gallery .album:hover .album__title { color: #ffffff; }
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
