<template>
  <div class="card">
    <div class="card-header elipsis">
      {{name}}
    </div>
    <div class="card-body block-elipsis">
      {{description}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'ApplicationCard',
  props: {
    application: {
      type: Object,
      required: true
    }
  },
  computed: {
    name () {
      return this.application.name
    },
    description () {
      return this.application.description || 'no description provided'
    }
  }
}
</script>

<style>
  .card {
    background: #fff;
    border-radius: 2px;
    width: 200px;
    height: 150px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    cursor: default;
  }

  .card-header {
    padding: 1rem;
    border-bottom: 1px solid grey;
    font-weight: bold;
    height: 20px;
  }

  .card-body {
    padding: 0.5rem;
  }

  /* truncates a single-line long text with ellipsis */ 
  .elipsis {
    white-space: nowrap; 
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* truncates a 6-line long text with ellipsis */
  .block-elipsis {
    display: block;
    display: -webkit-box;
    max-width: 100%;
    height: 76px;
    margin: 0 auto;
    font-size: 14px;
    line-height: 1;
    -webkit-line-clamp: 6;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
  }
</style>