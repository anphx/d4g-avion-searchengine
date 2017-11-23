<template>

  <div class="wrap text-center">
    <ais-index
      index-name="d4g_dentists_db"
      app-id="4FB5SURL9L"
      api-key="15e605b035695c9e33df0010b3fc204c"
      :auto-search="false" >
      <div class="wrap text-center">
        <h1>Welcome to AVION</h1>
        <p>Look for a dentist?</p>
        <div>
          <ais-search-box id="search_box" placeholder="Which dentist you are looking for..." class="search-input"></ais-search-box>
          <ais-results inline-template>
            <table>
              <tbody>
                <tr v-for="result in results" :key="result.objectID">
                  <td><img :src="result.image"/></td>
                  <td>{{ result.email }}</td>
                  <td>{{ result.first_name }}</td>
                  <td>{{ result.last_name }}</td>
                  <td>{{ result.address }}</td>
                  <td>{{ result.city }}</td>
                  <td>{{ result.phone }}</td>
                </tr>
              </tbody>
            </table>
          </ais-results>
        </div>
      </div>

    </ais-index>
  </div>

</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
  @import "assets/style.scss"
</style>
