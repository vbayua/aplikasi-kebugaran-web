<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h2>List of Community</h2>
      </div>
      <div class="col-md-6">
        <div class="input-group mb-5">
          <input
            v-model.trim="search"
            type="text"
            class="form-control border-0 small"
            placeholder="Search Community by City"
            aria-label="Search"
            aria-describedby="basic-addon2"
            autocomplete="off"
            @keyup="getCommunityByCity"
          >
          <div class="input-group-append">
            <button class="btn btn-primary" type="button">
              <i class="fas fa-search fa-sm" />
            </button>
          </div>
        </div>
      </div>
    </div>
    <div v-for="community in communityByCity" id="community-group" :key="community._id" class="row">
      <div class="col">
        <div class="card" style="width: 18rem;">
          <div class="card-body">
            <h4 class="card-title">
              {{ community.name }}
            </h4>
            <h6 class="card-subtitle mb-2 text-muted">
              {{ community.city }}
            </h6>
            <p class="card-text">
              {{ community.description }}
            </p>
            <p class="card-text">
              {{ community.schedule }}
            </p>
            <a :href="'https://www.instagram.com/'+ community.instagram" target="_blank" class="card-link">
              {{ community.instagram }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    communities: {
      type: [Object, Array],
      default: () => {}
    }
  },

  data () {
    return {
      communityByCity: [],
      search: ''
    }
  },

  created () {
    this.getCommunityByCity()
  },

  methods: {
    getCommunityByCity () {
      if (this.search) {
        this.communityByCity = this.communities.filter((community) => {
          return community.city.toLowerCase().includes(this.search.toLowerCase())
        })
      } else {
        this.communityByCity = this.communities
        return this.communityByCity
      }
    }
  }

}
</script>
