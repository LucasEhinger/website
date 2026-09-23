---
    permalink: /about/gnarmpfsk
    title: GNARMPFSK
    # PDFs are listed in _data/gnarmpfsk.yml and hosted on Google Drive.
    # Pages under _pages/about/gnarmpfsk/ with a `type` (stories, photo galleries)
    # are listed too.
---

GNARMPFSK---the sound made by a newly-awoken hiker in a wet sleeping bag on a frosty morning, as they realize that if they are to have any hot chocolate they are going to have to get up and make it themselves---is MITOC's newsletter!

Here, you can read (a selection of) GNARMPFSK newsletters, as well as more recent stories from current and former MITOC'ers!

Every scanned page has been put through text recognition, so the search box below looks *inside* the documents, not just at their titles. The recognition is good but not perfect---these are mimeographs from the 1940s---so an occasional word will be garbled beyond finding.

Contact [mitoc-owner@mit.edu](mailto:mitoc-owner@mit.edu) to add your own trip report!

For other cool stories, also check out the [Sean A. Collier Adventure Grant](https://mitoc-cag.mit.edu/), the [trip report archive (1946-2017)](/legacy-gallery/), or the [tech archive](/about/gnarmpfsk/tech-archive)!


<style>
  .archive-controls { margin: 20px 0; }
  .archive-controls .form-group { margin-right: 20px; margin-bottom: 10px; vertical-align: top; }
  .archive-types .btn { margin: 0 4px 4px 0; }
  .archive-list { display: flex; flex-wrap: wrap; margin: 0 -15px; }
  .archive-doc { margin-bottom: 30px; }
  .archive-doc h4 { margin-bottom: 4px; }
  .archive-doc h4 a { color: inherit; }
  .archive-meta { margin-bottom: 8px; color: #777; }
  .archive-meta .label { margin-left: 4px; }
  .archive-thumbs { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; margin-bottom: 8px; }
  .archive-thumbs img { display: block; width: 100%; aspect-ratio: 4 / 3; object-fit: cover; background: #eee; }
  .archive-excerpt { font-size: 16px; line-height: 1.6; }
  /* Full-text hits from the OCR'd scans. */
  .archive-hits { margin-bottom: 8px; padding: 8px 12px; background: #f6f6f6; border-left: 3px solid #337ab7; font-size: 14px; }
  .archive-hits p { margin: 0 0 4px; color: #555; }
  .archive-hits p:last-child { margin-bottom: 0; }
  .archive-hits .archive-hit-where { font-weight: bold; color: #337ab7; }
  .archive-search-status { font-style: italic; }
  mark { padding: 0; background: #fff3a3; }
  .archive-article { display: block; margin-bottom: 8px; }
  .archive-note { margin: 4px 0 0; }
  .archive-article img { display: block; width: 100%; aspect-ratio: 16 / 9; object-fit: cover; background: #eee; }
  /* Two-handle year slider: two range inputs stacked on one track. */
  .year-range { position: relative; width: 260px; max-width: 100%; height: 34px; }
  .year-range-track { position: absolute; left: 0; right: 0; top: 15px; height: 4px; border-radius: 2px; background: #ddd; }
  .year-range-fill { position: absolute; top: 0; bottom: 0; background: #337ab7; border-radius: 2px; }
  .year-range input[type=range] { position: absolute; left: 0; top: 0; width: 100%; height: 34px; margin: 0; background: none; pointer-events: none; -webkit-appearance: none; appearance: none; }
  .year-range input[type=range]::-webkit-slider-runnable-track { background: none; }
  .year-range input[type=range]::-moz-range-track { background: none; }
  .year-range input[type=range]::-webkit-slider-thumb { -webkit-appearance: none; pointer-events: auto; width: 20px; height: 20px; border-radius: 50%; background: #fff; border: 2px solid #337ab7; cursor: pointer; }
  .year-range input[type=range]::-moz-range-thumb { pointer-events: auto; width: 16px; height: 16px; border-radius: 50%; background: #fff; border: 2px solid #337ab7; cursor: pointer; }
  .year-range input[type=range]:focus-visible { outline: none; }
  .year-range input[type=range]:focus-visible::-webkit-slider-thumb { box-shadow: 0 0 0 3px rgba(51, 122, 183, 0.4); }
  .year-range input[type=range]:focus-visible::-moz-range-thumb { box-shadow: 0 0 0 3px rgba(51, 122, 183, 0.4); }
</style>

{% assign data = site.data.gnarmpfsk %}
{% assign pages = site.pages | where_exp: "p", "p.url contains '/about/gnarmpfsk/'" | where_exp: "p", "p.type" %}
{% assign docs = data.documents | concat: pages | sort: "date" | reverse %}

<form class="archive-controls form-inline" onsubmit="return false">
  <div class="form-group">
    <label for="archive-search">Search <small class="text-muted">(inside the scans too)</small></label><br>
    <input type="search" id="archive-search" class="form-control" placeholder="Intervale, hearse, Katahdin&hellip;" autocomplete="off">
  </div>
  <div class="form-group">
    <label>Type <small class="text-muted">(pick one)</small></label><br>
    <div class="archive-types" role="group" id="archive-types">
      <button type="button" class="btn btn-default active" data-type="" aria-pressed="true">All</button>
      {% for type in data.types %}
      <button type="button" class="btn btn-default" data-type="{{ type }}" aria-pressed="false">{{ type }}</button>
      {% endfor %}
    </div>
  </div>
  {% assign dated = docs | where_exp: "d", "d.date" %}
  {% assign first_year = dated.last.date | slice: 0, 4 %}
  {% assign last_year = dated.first.date | slice: 0, 4 %}
  <div class="form-group">
    <label id="archive-years-label">Years: <span id="archive-years-value">{{ first_year }}–{{ last_year }}</span></label><br>
    <div class="year-range">
      <div class="year-range-track"><div class="year-range-fill" id="archive-years-fill"></div></div>
      <input type="range" id="archive-year-from" min="{{ first_year }}" max="{{ last_year }}" step="1" value="{{ first_year }}" aria-label="From year">
      <input type="range" id="archive-year-to" min="{{ first_year }}" max="{{ last_year }}" step="1" value="{{ last_year }}" aria-label="To year">
    </div>
  </div>
  <div class="form-group">
    <label for="archive-sort">Sort by</label><br>
    <select id="archive-sort" class="form-control">
      <option value="date-desc">Date (newest first)</option>
      <option value="date-asc">Date (oldest first)</option>
      <option value="type">Type (A–Z)</option>
    </select>
  </div>
</form>

<p id="archive-count" class="text-muted">{{ docs.size }} documents</p>
<p id="archive-search-note" class="text-muted archive-search-status" hidden></p>

<div class="archive-list" id="archive-list">
  {% for doc in docs %}
  {% if doc.drive %}{% assign url = "https://drive.google.com/file/d/" | append: doc.drive | append: "/view" %}{% elsif doc.link %}{% assign url = doc.link %}{% else %}{% assign url = doc.url %}{% endif %}
  {% comment %}
    Everything a search should match: the card's own text plus, for pages we
    host, the whole transcription or story.
  {% endcomment %}
  {% capture haystack %}{{ doc.title }} {{ doc.author }} {{ doc.source }} {{ doc.summary }} {{ doc.note }} {{ doc.date_display }} {{ doc.type }} {{ doc.content | markdownify | strip_html }}{% endcapture %}
  <div class="archive-doc col-xs-12 col-md-6" data-date="{{ doc.date }}" data-type="{{ doc.type }}" data-title="{{ doc.title | escape }}"
       {% if doc.drive %}data-drive="{{ doc.drive }}" {% endif %}data-search="{{ haystack | strip_newlines | downcase | escape }}">
    <h4><a href="{{ url }}"{% if doc.link or doc.drive %} target="_blank" rel="noopener"{% endif %}>{{ doc.title }}</a></h4>
    <div class="archive-meta">
      {% if doc.date %}Published {% endif %}{% if doc.date_display %}{{ doc.date_display }}{% else %}{{ doc.date | date: "%b. %-d, %Y" }}{% endif %}
      {% if doc.type %}<span class="label label-primary">{{ doc.type }}</span>{% endif %}
    </div>
    {% comment %}Filled in by the search script when the query is found in the scanned text.{% endcomment %}
    <div class="archive-hits" hidden></div>
    {% if doc.drive %}
    <div class="embed-responsive" style="padding-bottom: 129%">
      <iframe class="embed-responsive-item" src="https://drive.google.com/file/d/{{ doc.drive }}/preview" title="{{ doc.title | escape }}" loading="lazy" allow="autoplay"></iframe>
    </div>
    <a href="{{ url }}" target="_blank" rel="noopener">Open full size</a>
    {% elsif doc.link %}
    {% if doc.image %}
    <a class="archive-article" href="{{ url }}" target="_blank" rel="noopener">
      <img src="{{ doc.image }}" alt="" loading="lazy">
    </a>
    {% endif %}
    <p class="archive-excerpt">{% if doc.source %}<em>{{ doc.source }}{% if doc.author %}, by {{ doc.author }}{% endif %}.</em> {% endif %}{{ doc.summary }}</p>
    <a href="{{ url }}" target="_blank" rel="noopener">Read the full article on {{ doc.source | default: "the web" }} &rarr;</a>
    {% if doc.note %}<p class="archive-note text-muted"><small>{{ doc.note }}</small></p>{% endif %}
    {% elsif doc.thumbnails %}
    <a class="archive-thumbs" href="{{ url }}">
      {% for thumb in doc.thumbnails %}<img src="{{ thumb }}" alt="" loading="lazy">{% endfor %}
    </a>
    <a href="{{ url }}">View all photos &rarr;</a>
    {% else %}
    {% if doc.clipping %}
    <a class="archive-article" href="{{ url }}">
      <img src="{{ doc.clipping }}" alt="" loading="lazy">
    </a>
    {% endif %}
    <p class="archive-excerpt">{% if doc.source %}<em>{{ doc.source }}{% if doc.author %}, by {{ doc.author }}{% endif %}.</em> {% elsif doc.author %}<em>By {{ doc.author }}.</em> {% endif %}{{ doc.content | markdownify | strip_html | truncatewords: 70 }}</p>
    {% if doc.source %}
    <a href="{{ url }}">Read local transcription &rarr;</a>
    {% else %}
    <a href="{{ url }}">Read the full story &rarr;</a>
    {% endif %}
    {% endif %}
  </div>
  {% endfor %}
</div>

<p id="archive-empty" class="text-muted" style="display: none">No documents match these filters.</p>

<script>
(function () {
  var list = document.getElementById('archive-list');
  var docs = Array.prototype.slice.call(list.children);
  var buttons = document.querySelectorAll('#archive-types .btn');
  var yearFrom = document.getElementById('archive-year-from');
  var yearTo = document.getElementById('archive-year-to');
  var minYear = +yearFrom.min, maxYear = +yearFrom.max;
  var sortSelect = document.getElementById('archive-sort');
  var search = document.getElementById('archive-search');
  var note = document.getElementById('archive-search-note');
  // A document has exactly one type, and only one can be chosen at a time.
  // Empty means no filter.
  var selected = '';

  // The scanned documents are OCR'd into search/gnarmpfsk-index.json: one
  // entry per Google Drive file, holding the text of each of its pages. It is
  // about a megabyte, so it is fetched only once someone actually searches,
  // and the card filters keep working on their own if it never arrives.
  var index = null, lowered = null, indexState = 'idle';

  function loadIndex() {
    indexState = 'loading';
    fetch('/search/gnarmpfsk-index.json')
      .then(function (r) { if (!r.ok) throw new Error(r.status); return r.json(); })
      .then(function (json) {
        index = json.docs;
        // A lowercase copy to search, so the stored text keeps its capitals
        // for display in the snippets.
        lowered = {};
        Object.keys(index).forEach(function (id) {
          lowered[id] = index[id].map(function (p) { return p.toLowerCase(); });
        });
        indexState = 'ready';
        update();
      })
      .catch(function () { indexState = 'failed'; update(); });
  }

  function escapeRe(s) { return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&'); }
  function escapeHtml(s) {
    return s.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;');
  }

  // -> {pages: [1-based page numbers], text: page containing the first hit}
  function findHits(el, query) {
    var id = el.getAttribute('data-drive');
    if (!id || !lowered || !lowered[id]) return null;
    var pages = [], text = null;
    for (var i = 0; i < lowered[id].length; i++) {
      if (lowered[id][i].indexOf(query) >= 0) {
        pages.push(i + 1);
        if (text === null) text = index[id][i];
      }
    }
    return pages.length ? { pages: pages, text: text, total: lowered[id].length } : null;
  }

  function listPages(pages) {
    if (pages.length === 1) return 'page ' + pages[0];
    // A common word can hit every page of a long issue; do not list them all.
    if (pages.length > 6) return 'pages ' + pages.slice(0, 6).join(', ') + ' and ' + (pages.length - 6) + ' more';
    return 'pages ' + pages.slice(0, -1).join(', ') + ' and ' + pages[pages.length - 1];
  }

  // A window of about 90 characters either side of the match, trimmed back to
  // whole words.
  function snippet(text, query) {
    var at = text.toLowerCase().indexOf(query);
    var start = Math.max(0, at - 90), end = Math.min(text.length, at + query.length + 90);
    var s = text.slice(start, end);
    if (start > 0) s = '…' + s.replace(/^\S*\s/, '');
    if (end < text.length) s = s.replace(/\s\S*$/, '') + '…';
    return escapeHtml(s).replace(new RegExp('(' + escapeRe(query) + ')', 'gi'), '<mark>$1</mark>');
  }

  function renderHits(el, hits, query) {
    var box = el.querySelector('.archive-hits');
    if (!box) return;
    if (!hits) { box.hidden = true; box.innerHTML = ''; return; }
    var where = hits.total > 1 ? 'Found on ' + listPages(hits.pages) : 'Found in the text';
    box.innerHTML = '<p class="archive-hit-where">' + where + '</p><p>' +
      snippet(hits.text, query) + '</p>';
    box.hidden = false;
  }

  function typeOf(el) { return el.getAttribute('data-type') || ''; }
  function matchesType(el) { return !selected || typeOf(el) === selected; }
  // Undated documents (empty data-date) always sort last.
  function byDateDesc(a, b) {
    var da = a.getAttribute('data-date'), db = b.getAttribute('data-date');
    if (!da || !db) return !da - !db;
    return db.localeCompare(da);
  }

  function update() {
    var query = search.value.trim().toLowerCase();
    var from = +yearFrom.value, to = +yearTo.value;
    var span = maxYear - minYear || 1;
    var fill = document.getElementById('archive-years-fill');
    fill.style.left = (from - minYear) / span * 100 + '%';
    fill.style.right = (maxYear - to) / span * 100 + '%';
    document.getElementById('archive-years-value').textContent = from === to ? from : from + '–' + to;
    var sort = sortSelect.value;
    var sorted = docs.slice().sort(function (a, b) {
      if (sort === 'date-asc') {
        if (!a.getAttribute('data-date') || !b.getAttribute('data-date')) return byDateDesc(a, b);
        return -byDateDesc(a, b);
      }
      if (sort === 'type') {
        return typeOf(a).localeCompare(typeOf(b)) || byDateDesc(a, b);
      }
      return byDateDesc(a, b);
    });
    if (query && indexState === 'idle') loadIndex();
    var shown = 0, inText = 0;
    // Reorder with CSS `order` rather than moving nodes, which would reload the iframes.
    sorted.forEach(function (el, i) {
      var year = el.getAttribute('data-date').slice(0, 4);
      var inRange = year ? +year >= from && +year <= to : from === minYear && to === maxYear;
      var onCard = !query || (el.getAttribute('data-search') || '').indexOf(query) >= 0;
      var hits = query ? findHits(el, query) : null;
      var match = matchesType(el) && inRange && (onCard || !!hits);
      // The snippet is worth showing even when the title already matched, so
      // long as the document is actually on screen.
      renderHits(el, match ? hits : null, query);
      if (match && hits && !onCard) inText++;
      el.style.display = match ? '' : 'none';
      el.style.order = i;
      if (match) shown++;
    });
    document.getElementById('archive-count').textContent =
      shown === docs.length ? docs.length + ' documents' : 'Showing ' + shown + ' of ' + docs.length + ' documents';
    document.getElementById('archive-empty').style.display = shown ? 'none' : '';

    var message = '';
    if (query && indexState === 'loading') message = 'Searching the scanned pages…';
    else if (query && indexState === 'failed') message = 'The scanned pages could not be searched just now — showing title matches only.';
    else if (query && inText) message = inText === 1
      ? 'One of these was found by the text inside the scan, not its title.'
      : inText + ' of these were found by the text inside the scans, not their titles.';
    note.textContent = message;
    note.hidden = !message;
  }

  Array.prototype.forEach.call(buttons, function (btn) {
    btn.addEventListener('click', function () {
      var k = btn.getAttribute('data-type');
      // One type at a time: picking one replaces whatever was chosen, and
      // picking the one already chosen goes back to "All".
      selected = (!k || k === selected) ? '' : k;
      Array.prototype.forEach.call(buttons, function (b) {
        var bk = b.getAttribute('data-type');
        var on = bk ? bk === selected : !selected;
        b.classList.toggle('active', on);
        b.setAttribute('aria-pressed', on ? 'true' : 'false');
      });
      update();
    });
  });
  // Keep the handles from crossing; the one being dragged stops at the other.
  yearFrom.addEventListener('input', function () {
    if (+yearFrom.value > +yearTo.value) yearFrom.value = yearTo.value;
    update();
  });
  yearTo.addEventListener('input', function () {
    if (+yearTo.value < +yearFrom.value) yearTo.value = yearFrom.value;
    update();
  });
  // When both handles sit at the same end, keep the one that can still move on top.
  yearFrom.addEventListener('pointerdown', function () { yearFrom.style.zIndex = 2; yearTo.style.zIndex = 1; });
  yearTo.addEventListener('pointerdown', function () { yearTo.style.zIndex = 2; yearFrom.style.zIndex = 1; });
  update();
  sortSelect.addEventListener('change', update);
  // Typing scans every OCR'd page, so wait for a pause rather than running on
  // each keystroke.
  var typing = null;
  search.addEventListener('input', function () {
    clearTimeout(typing);
    typing = setTimeout(update, 120);
  });
})();
</script>
