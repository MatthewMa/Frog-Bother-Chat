<template>
    <div class="row" id="page_header">
        <div class="col-md-6 col-xs-12">
            <h1 id="page_title">{{ title }}</h1>
        </div>
        <div class="col-md-6 col-xs-12">
            <h2 id="page_god_frogger">{{ godFrogger }}</h2>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Header",
        data() {
          return {
              title: "Frog Bother Chat",
              godFrogger: "Vito Croakleone"
          }
        },
    }
</script>

<style scoped>
    #page_header {
        margin-top: 2%;
    }
    #page_title {
        text-align: left;
        font-weight: normal !important;
    }
    #page_god_frogger {
        text-align: right;
    }
</style>