<template>
  <div class="wrap text-center">
    <ais-index
      index-name="d4g_dentists_db"
      :search-store="searchStore"
      :auto-search="false" >
      <div class="wrap text-center">
        <h1>Welcome to AVION</h1>
        <p>Look for a dentist?</p>
        <div>
          <ais-search-box id="search_box"
                          placeholder="Which dentist you are looking for..."
                          class="search-input">
          </ais-search-box>
          <ais-results inline-template v-show="searchStore._helper.state.query.length > 0">
            <table>
              <thead v-if="results.length > 0">
                <td></td>
                <td>Email</td>
                <td>Full name</td>
                <td>Address</td>
                <td>Specialty</td>
                <td>Phone</td>
              </thead>
              <tbody>
                <tr v-for="result in results" :key="result.objectID">
                  <td><img :src="result.image"/></td>
                  <td>{{ result.email }}</td>
                  <td>{{ result.first_name }} - {{result.last_name}} </td>
                  <td>{{ result.address }} - {{ result.city }}</td>
                  <td>{{ result.specialty || "Not defined" }}</td>
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
  /* eslint-disable */

  import { createFromAlgoliaCredentials } from 'vue-instantsearch'
  const searchStore = createFromAlgoliaCredentials('4FB5SURL9L', '15e605b035695c9e33df0010b3fc204c')

  export default {
    name: 'app',
    data() {
      return { searchStore }
    }
  }
</script>

<style>
  @import "assets/style.scss"
</style>
