---
layout: default
---
{% assign all_tags = site.data.targets | map: "tags" %}
{% assign asdf = all_tags | join: ", " %}
{% assign test = asdf | split: ", " %}
{% assign final = test | uniq | sort %}
<div class="columns">
  <div class="column col-12">
    <h1>Check Website</h1>
    <p>Various websites provide testing opportunities for different relevant aspects like accessibility, HTML/CSS-standards and lots more.</p>
    <p>This site tries to help you with that - giving you easy access to various services in a central place.</p>
    <p>The list includes services related to a range of topics:</p>
    <p>
      {% for x in final %}
        <span class="label">{{x}}</span>
      {% endfor %}
    </p>
  </div>
</div>

<div class="columns">
  <div class="column col-12">
    <h2>1. Enter a URL</h2>
    <div class="toast toast-danger">
      Not a valid URL. Please check and try again.
    </div>
    <form id="js-form" action="">
      <div class="form-group">
        <label class="form-label text-hide" for="input-url">URL</label>
        <input class="form-input" type="text" id="input-url" placeholder="http://example.com" />
      </div>
      <div class="form-group">
        <input class="btn btn-primary" type="submit"></input>
      </div>
    </form>
  </div>
</div>

<div class="" style="width: 100%; display: flex; flex-wrap: wrap">
  <h2>2. Choose a service</h2>
  {% for target in site.data.targets %}
      <div class="card" style="">
        <div class="card-header">
          <h4 class="card-title">{{ target.name }}</h4>
        </div>
        <div class="card-body">
        {% if target.description %}
            <p>{{ target.description }}</p>
          {% endif %}
          {% if target.tags %}
            <p>
              {% for tag in target.tags %}
                <span class="label">{{ tag }}</span>
              {% endfor %}
            </p>
          {% endif %}
          {% if target.notes %}
            <p>Please note: 
              {% for note in target.notes %}
                {{ note }}
              {% endfor %}
            </p>
          {% endif %}
          {% if target.addLink %}
          {% else %}
            <p>Manual URL paste required</p>
          {% endif %}
        </div>
        <div class="card-footer">
          <a class="btn js-testlink" rel="external" data-auto="{{ target.addLink }}" data-url="{{ target.url }}" href="{{ target.url }}">Test</a>
        </div>
      </div>
  {% endfor %}
</div>

<div class="columns">
  <div class="column col-12">
    <h2>Misc</h2>
    <p>For requests and/or comments <a href="https://github.com/nilswindisch/check-website/issues?utf8=✓&q=is%3Aissue+">open an issue at GitHub</a> or <a href="https://twitter.com/nilswindisch">send a tweet @nilswindisch</a>.</p>
    <h3>Version History</h3>
    <ul>
      <li>1.0.0 - Initial</li>
    </ul>
  </div>
</div>