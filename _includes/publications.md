## Publications

<style>
  .publication-card {
    display: grid;
    grid-template-columns: 270px 1fr;
    gap: 25px;
    align-items: center;
    margin: 30px 0 45px;
  }

  .publication-media {
    width: 270px;
    height: 152px;
    overflow: hidden;
    border-radius: 8px;
    background: white;
    box-shadow: 3px 3px 6px #888;
  }

  .publication-pdf,
  .publication-image {
    width: 100%;
    height: 100%;
    border: none;
    object-fit: contain;
    display: block;
  }

  .publication-pdf {
    pointer-events: none;
  }

  .publication-title {
    font-size: 1rem;
    font-weight: 700;
    line-height: 1.4;
    margin-bottom: 5px;
  }

  .publication-authors,
  .publication-venue {
    margin-bottom: 5px;
    line-height: 1.5;
  }

  .publication-links a {
    display: inline-block;
    padding: 3px 12px;
    margin: 4px 4px 0 0;
    border: 1px solid currentColor;
    text-decoration: none;
  }

  @media screen and (max-width: 700px) {
    .publication-card {
      grid-template-columns: 1fr;
    }

    .publication-media {
      width: 100%;
      max-width: 270px;
    }
  }
</style>

<div class="publications">
{% for link in site.data.publications.main %}

<div class="publication-card">

  <div class="publication-media">
    {% if link.thumbnail_pdf %}
    <object
      class="publication-pdf"
      data="{{ link.thumbnail_pdf | relative_url }}#page=1&view=FitH&toolbar=0&navpanes=0&scrollbar=0"
      type="application/pdf"
      aria-label="{{ link.title }}">
      <a href="{{ link.thumbnail_pdf | relative_url }}"
         target="_blank"
         rel="noopener">View publication diagram</a>
    </object>

    {% elsif link.image %}
    <img
      class="publication-image"
      src="{{ link.image | relative_url }}"
      alt="{{ link.title }}">
    {% endif %}
  </div>

  <div class="publication-details">

    <div class="publication-title">
      {% if link.pdf %}
      <a href="{{ link.pdf }}" target="_blank" rel="noopener">
        {{ link.title }}
      </a>
      {% else %}
      {{ link.title }}
      {% endif %}
    </div>

    <div class="publication-authors">
      {{ link.authors }}
    </div>

    <div class="publication-venue">
      <em>{{ link.conference }}</em>
    </div>

    <div class="publication-links">
      {% if link.pdf %}
      <a href="{{ link.pdf }}" target="_blank" rel="noopener">PDF</a>
      {% endif %}

      {% if link.code %}
      <a href="{{ link.code }}" target="_blank" rel="noopener">Code</a>
      {% endif %}

      {% if link.page %}
      <a href="{{ link.page }}" target="_blank" rel="noopener">Project Page</a>
      {% endif %}
    </div>

  </div>

</div>

{% endfor %}
</div>
