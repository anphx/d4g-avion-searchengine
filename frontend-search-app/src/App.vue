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
                          placeholder="I am looking for (first name, last name, city or specialty)... "
                          class="search-input">
          </ais-search-box>
          <div class="results-per-page">
            <p>Show: </p>
            <ais-results-per-page-selector :options="[10, 20, 30]"></ais-results-per-page-selector>
            <p>per page </p>
          </div>
          <ais-pagination :padding="5"></ais-pagination>

          <ais-results inline-template>
            <div class="container-fluid results-wrapper">
              <div class="row" v-for="item in results" :key="item.objectID">
                <div class="col-sm-3">
                  <img :src="item.image" class="img-responsive"/>
                </div>
                <div class="col-sm-9 column">
                  <p>
                    <a :href="'mailto:' + item.email">
                      <span class="the-icons glyphicon glyphicon-envelope"></span>
                    </a>
                    <i>{{ item.email }}</i>
                  </p>
                  <p><strong>{{ item.first_name }} - {{item.last_name}}</strong></p>
                  <p>
                    <i>Specialty: </i>{{ item.specialty || "Not defined" }}
                  </p>
                  <p>{{ item.address }} - {{ item.city }}</p>
                  <p>
                    <span class="the-icons glyphicon glyphicon-phone-alt"></span>
                    <i>{{ item.phone }}</i>
                  </p>
                </div>
              </div>
            </div>
          </ais-results>
          <ais-no-results>
             <template slot-scope="props">
             	Sorry, no dentist found for <i>{{ props.query }}</i>. Please try with other keywords...
             </template>
          </ais-no-results>
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
    },
    methods: {
      onPageChange() {
        window.scrollTo(0,0);
      }
    }
  }
</script>

<style lang="scss">
  @import "assets/style.scss"
</style>
