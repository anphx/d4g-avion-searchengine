<template>
  <ais-index
    index-name="d4g_dentists_db"
    app-id="4FB5SURL9L"
    api-key="15e605b035695c9e33df0010b3fc204c">

    <ais-search-box></ais-search-box>
    <ais-results>
      <template slot-scope="{ result }">
          <!-- <ais-highlight :result="result" attribute-name="name"></ais-highlight> -->
        <h2>
          {{ result.email }}
        </h2>
        <p>{{ result.first_name }}</p>
      </template>
    </ais-results>
  </ais-index>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
