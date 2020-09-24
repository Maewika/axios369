<template>
  <div id="sup">
    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand>Search Anime</b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" v-model="textSearch"></b-form-input>
              <b-button variant="success" size="sm" class="my-2 my-sm-0" @click="searchData()">Search</b-button>
            </b-nav-form>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div><br>
    <div id="sup">
      <b-container class="bv-example-row bv-example-row-flex-cols">
        <div class="row">
          <div class="col">
            <b-row align-v="stretch">
              <b-card-group columns>
                <b-card class="card text-dark bg-info mb-3" v-for="data in List"
                  :key="data.mal_id"
                  :title="data.title"
                  :img-src="data.image_url"
                  :img-alt="url"
                  img-top
                  tag="article"
                  style="max-width: 30rem;"
                >
                  <b-card-text>
                    Synopsis : {{data.synopsis}}
                    <br />
                    Score : {{data.score}}
                    <br />
                    Episodes : {{data.episodes}}
                    <br />
                    Rated : {{data.rated}}
                  </b-card-text>
                </b-card>
              </b-card-group>
            </b-row>
          </div>
        </div>
      </b-container>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      List: null,
      textSearch: "",
    };
  },
  methods: {
    searchData() {
      axios
        .get(
          "https://api.jikan.moe/v3/search/anime?q=" +
            this.textSearch +
            "&limit=10"
        )
        .then((response) => {
          this.List = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>