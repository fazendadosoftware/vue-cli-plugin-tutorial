<template>
  <div id="app">
    <div class="cards-container">
      <application-card
        v-for="application in dataset"
        :key="application.id"
        :application="application"/>
    </div>
  </div>
</template>

<script>
import ApplicationCard from './components/ApplicationCard'

export default {
  name: 'app',
  components: {ApplicationCard},
  data () {
    return {
      baseUrl: '',
      dataset: []
    }
  },
  created () {
    this.$lx.init()
      .then(setup => { /* eslint-disable */
        const { settings = {} } = setup
        const { baseUrl } = settings
        this.baseUrl = baseUrl

        const config = {
          allowEditing: false,
          allowTableView: false,
          facets: [
            {
              attributes: ['id', 'name', 'description'],
              callback: dataset => {
                this.dataset = dataset
              },
              fixedFactSheetType: 'Application',
              key: 'applications',
              label: 'Applications'
            }
          ]
        }
        this.$lx.ready(config)
      })
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto+Condensed');

html, body {
  font-family: 'Roboto Condensed', sans-serif;
  background: #e2e1e0;
}

.cards-container {
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
}

.cards-container > .card {
  margin: 1rem;
}
</style>