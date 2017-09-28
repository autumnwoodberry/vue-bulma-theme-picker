<template>
  <div id="app" class="container">

    <link rel="stylesheet" :href="selected">

    <div class="level">
      <div class="level-left">
        <div class="control">
          <div class="select">
            <select v-model="selected" class="select">
              <option v-for="theme in themes" :value="theme.css">
                {{ theme.name }} - {{  theme.description }}
              </option>
            </select>
          </div>
        </div>
      </div>
    </div>

    <div class="level">
      <div class="level-left">
        <div>
          <a class="button is-primary">Primary</a>
          <a class="button is-info">Info</a>
          <a class="button is-success">Success</a>
          <a class="button is-warning">Warning</a>
          <a class="button is-danger">Danger</a>
        </div>
      </div>
    </div>

    <div class="columns">
      <div class="column">
        <div class="box">
          <article class="media">
            <div class="media-left">
              <figure class="image is-64x64">
                <img src="http://bulma.io/images/placeholders/128x128.png" alt="Image">
              </figure>
            </div>
            <div class="media-content">
              <div class="content">
                <p>
                  <strong>John Smith</strong> <small>@johnsmith</small> <small>31m</small>
                  <br>
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.
                </p>
              </div>
              <nav class="level is-mobile">
                <div class="level-left">
                  <a class="level-item">
                    <span class="icon is-small"><i class="fa fa-reply"></i></span>
                  </a>
                  <a class="level-item">
                    <span class="icon is-small"><i class="fa fa-retweet"></i></span>
                  </a>
                  <a class="level-item">
                    <span class="icon is-small"><i class="fa fa-heart"></i></span>
                  </a>
                </div>
              </nav>
            </div>
          </article>
        </div>
      </div>
      <div class="column"></div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'app',
  data () {
    return {
      themes: null,
      selected: 'https://unpkg.com/bulmaswatch/default/bulmaswatch.min.css'
    }
  },
  async created () {
    const { data: { themes } } = await axios.get('https://jenil.github.io/bulmaswatch/api/themes.json')
    this.themes = themes
  }
}
</script>
