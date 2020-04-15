<template>
  <div class="home">
    <section class="image-gallery">
      <div class="image" v-for="item in items" :key="item.id">
        <h2>{{item.title}}</h2>
        <!--h2>{{item.description}}</h2-->

        <div class="example" @click="open(item)">
          <img :src="item.path" />
          <div v-if="item.hasOwnProperty('description') && item.description != ''" class="fadedbox">
            <div class="title text">{{item.description}}</div>
          </div>
        </div>

      </div>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      items: []
    };
  },
  async created() {
    await this.getItems()
    this.items.forEach(x => {
      console.log(x.description)
    });
    
  },
  methods: {
    async getItems() {
      try {
        let response = await axios.get("/api/items");
        this.items = response.data;
        return true;
      } catch (error) {
        console.log(error);
      }
    },
    open(item) {
      window.open(item.path);
    }
  }
};
</script>

<style scoped>
/* Hover text*/
.example {
  cursor: pointer;
  height: 300px;
  position: relative;
  overflow: hidden;
  width: 400px;
  text-align: center;
}
.example .fadedbox {
  background-color: #666666;
  position: absolute;
  top: 0;
  left: 0;
  color: #fff;
  -webkit-transition: all 300ms ease-out;
  -moz-transition: all 300ms ease-out;
  -o-transition: all 300ms ease-out;
  -ms-transition: all 300ms ease-out;
  transition: all 300ms ease-out;
  opacity: 0;
  width: 360px;
  height: 100px;
  padding: 130px 20px;
}
.example:hover .fadedbox {
  opacity: 0.8;
}
.example .text {
  -webkit-transition: all 300ms ease-out;
  -moz-transition: all 300ms ease-out;
  -o-transition: all 300ms ease-out;
  -ms-transition: all 300ms ease-out;
  transition: all 300ms ease-out;
  transform: translateY(30px);
  -webkit-transform: translateY(30px);
}
.example .title {
  font-size: 2.5em;
  text-transform: uppercase;
  opacity: 0;
  transition-delay: 0.2s;
  transition-duration: 0.3s;
}
.example:hover .title,
.example:focus .title {
  opacity: 1;
  transform: translateY(0px);
  -webkit-transform: translateY(0px);
}
/* End hover text*/
.image h2 {
  font-style: italic;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  column-gap: 1.5em;
}

.image {
  margin: 0 0 1.5em;
  display: inline-block;
  width: 100%;
}

.image img {
  width: 100%;
}

.image img:hover {
  cursor: zoom-in;
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .image-gallery {
    column-count: 2;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .image-gallery {
    column-count: 1;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .image-gallery {
    column-count: 1;
  }
}
</style>
