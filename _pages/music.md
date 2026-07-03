---
title: "Music"
layout: single
permalink: /music/
author_profile: false
classes: wide
---

<style>
/* ===== 상단 2탭 / 하위 탭 (순수 CSS, JS 없음) ===== */
.music-tabs { margin-top: 0.5rem; }
.mv-radio, .pl-radio { position: absolute; opacity: 0; pointer-events: none; }

.music-tabbar, .pl-tabbar {
  display: flex;
  gap: 0.25rem;
  overflow-x: auto;
  border-bottom: 1px solid #24395a;
}
.pl-tabbar { border-bottom: 0; margin-bottom: 0.4rem; }
.music-tabbar label, .pl-tablabel {
  cursor: pointer;
  white-space: nowrap;
  padding: 0.45rem 0.95rem;
  font-size: 0.9rem;
  color: var(--text-dim);
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  transition: color .18s ease, border-color .18s ease;
}
.pl-tablabel {
  font-family: "Space Grotesk", sans-serif;
  letter-spacing: 0.04em;
  font-size: 0.82rem;
}
.music-tabbar label:hover, .pl-tablabel:hover { color: var(--text); }

/* 패널 기본 숨김 */
.mv-panel, .pl-panel { display: none; }
.mv-panel { padding-top: 1.4rem; }

/* Level 1 (정적 2개) */
#view-gallery:checked  ~ #panel-gallery,
#view-playlist:checked ~ #panel-playlist { display: block; }
#view-gallery:checked  ~ .music-tabbar label[for="view-gallery"],
#view-playlist:checked ~ .music-tabbar label[for="view-playlist"] {
  color: var(--text);
  border-bottom-color: var(--accent);
}

/* Level 2 (동적: 플레이리스트 id별 규칙 생성) */
{% assign pls = site.data.playlists | sort: "id" | reverse %}
{% for pl in pls %}
#pl-{{ pl.id }}:checked ~ #plp-{{ pl.id }} { display: block; }
#pl-{{ pl.id }}:checked ~ .pl-tabbar label[for="pl-{{ pl.id }}"] {
  color: var(--text);
  border-bottom-color: var(--accent);
}
{% endfor %}

/* 플레이리스트 헤더 / 임베드 / 트랙 */
.pl-head { display: flex; align-items: baseline; gap: 0.8rem; margin: 0.4rem 0 1rem; flex-wrap: wrap; }
.pl-date { font-size: 0.72rem; letter-spacing: 0.14em; text-transform: uppercase; color: var(--text-dim); }
.pl-title { font-size: 1.05rem; color: var(--text); }
.pl-embed { border-radius: 12px; margin-bottom: 1.4rem; max-width: 560px; width: 100%; display: block; border: 0; }
.pl-tracks { display: flex; flex-wrap: wrap; gap: 1rem; }
.pl-empty { color: var(--text-dim); font-size: 0.9rem; }

/* ===== 연도별 앨범 갤러리 ===== */
.music-gallery { margin-top: 0.2rem; }
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

/* ===== 앨범 카드 (갤러리 + 플레이리스트 트랙 공용) ===== */
.music-gallery .album,
.pl-tracks .album {
  flex: 0 0 auto;
  width: 150px;
  margin: 0;
  display: flex;
  flex-direction: column;
}
.music-gallery .album__cover,
.pl-tracks .album__cover {
  width: 150px;
  height: 150px;
  object-fit: cover;
  background: #16273f;
  border-radius: 8px;
  display: block;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
  transition: transform .35s cubic-bezier(.2,.7,.2,1), box-shadow .35s ease;
}
.music-gallery .album:hover .album__cover,
.pl-tracks .album:hover .album__cover {
  transform: translateY(-4px) scale(1.02);
  box-shadow: 0 12px 26px rgba(0, 0, 0, 0.45);
}
.music-gallery .album__title,
.pl-tracks .album__title {
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
.music-gallery .album:hover .album__title,
.pl-tracks .album:hover .album__title { color: #ffffff; }
.music-gallery .album__artist,
.pl-tracks .album__artist {
  display: block;
  width: 150px;
  font-size: 0.72rem;
  color: #8a96a8;
  overflow-wrap: anywhere;
  word-break: break-word;
}
</style>

<div class="music-tabs">
<input type="radio" name="music-view" id="view-gallery" class="mv-radio" checked>
<input type="radio" name="music-view" id="view-playlist" class="mv-radio">
<div class="music-tabbar">
<label for="view-gallery">Album Gallery</label>
<label for="view-playlist">Monthly Playlist</label>
</div>

<div class="mv-panel" id="panel-gallery">
<div class="music-gallery">
{% assign years = site.data.music | sort: "year" | reverse %}
{% for entry in years %}<section class="music-year">
<h2 class="music-year__label">{{ entry.year }}</h2>
<div class="music-row">
{% for album in entry.albums %}<figure class="album"><img class="album__cover" src="{{ album.cover }}" alt="{{ album.title }}" loading="lazy"><span class="album__title">{{ album.title }}</span><span class="album__artist">{{ album.artist }}</span></figure>
{% endfor %}</div>
</section>
{% endfor %}</div>
</div>

<div class="mv-panel" id="panel-playlist">
{% assign pls = site.data.playlists | sort: "id" | reverse %}
{% if pls == nil or pls.size == 0 %}<p class="pl-empty">플레이리스트를 준비 중입니다.</p>
{% else %}{% for pl in pls %}<input type="radio" name="pl-view" id="pl-{{ pl.id }}" class="pl-radio"{% if forloop.first %} checked{% endif %}>
{% endfor %}<div class="pl-tabbar">
{% for pl in pls %}<label for="pl-{{ pl.id }}" class="pl-tablabel">{{ pl.id }}</label>
{% endfor %}</div>
{% for pl in pls %}<section class="pl-panel" id="plp-{{ pl.id }}">
<div class="pl-head"><span class="pl-date">{{ pl.date }}</span>{% if pl.title %}<span class="pl-title">{{ pl.title }}</span>{% endif %}</div>
{% if pl.spotify %}{% assign embed = pl.spotify | replace: 'open.spotify.com/', 'open.spotify.com/embed/' %}<iframe class="pl-embed" src="{{ embed }}" height="420" loading="lazy" allow="autoplay; clipboard-write; encrypted-media; picture-in-picture"></iframe>
{% endif %}<div class="pl-tracks">
{% for t in pl.tracks %}<figure class="album"><img class="album__cover" src="{{ t.cover }}" alt="{{ t.title }}" loading="lazy"><span class="album__title">{{ t.title }}</span><span class="album__artist">{{ t.artist }}</span></figure>
{% endfor %}</div>
</section>
{% endfor %}{% endif %}
</div>
</div>
