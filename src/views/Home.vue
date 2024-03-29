<template>
  <div class="home">
    <div>
      <div class="columns">
        <div class="left">
          <img class="full-avatar" src="https://cdn.eyzi.dev/avatar-full.png" />
          <img class="min-avatar" src="https://cdn.eyzi.dev/avatar.png" />
        </div>

        <div class="right">
          <div id="header">
            <span class="title-header eyzi-color">Eyzi</span>
          </div>

          <div id="definition">
            <span id="phonetic" @click="pronounce">/eɪzi/</span>
            <br />
            <span id="pos">(noun)</span> <span>Lazy without L</span>
          </div>

          <div id="links">
            <Link
              v-for="link in links"
              :key="link.label"
              :label="link.label"
              :url="link.url"
              :image="link.image"
            />
          </div>

          <div id="info">
            Check my github for bad codes
            <br />
            Check my blog for bad takes
            <br /><br />
            Creative Lead at
            <a class="moonlit-link" href="https://moonlit.works"
              ><img
                class="moonlit-icon"
                src="https://cdn.moonlit.works/logo/image.png"
              />Moonlit Works</a
            >
            <br /><br />
            Reach me by email at
            <a href="mailto:contact@eyzi.dev"
              ><span class="eyzi-color">contact@eyzi.dev</span></a
            >
            or on Discord at
            <span class="eyzi-color">Eyzi#3994</span>
          </div>
        </div>
      </div>

      <div id="footer">
        <div>Eyzi &copy; {{ new Date().getFullYear() }}</div>
        <div>
          Avatar by
          <a href="https://twitter.com/riotsuji" target="_blank">Riotsuji</a>
        </div>
        <div>
          Social media icons by
          <a href="https://www.iconfinder.com/jessicalanan" target="_blank">
            Lanan Illustration
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Link from "@/components/Link.vue";

export default defineComponent({
  name: "Home",
  data: () => ({
    links: [
      {
        label: "Github",
        url: "https://github.com/eyzi",
        image:
          "https://cdn2.iconfinder.com/data/icons/social-aquiocons/512/Aquicon-Github.png",
      },
      {
        label: "Blogsite",
        url: "https://blog.eyzi.dev",
        image:
          "https://cdn2.iconfinder.com/data/icons/social-aquiocons/512/Aquicon-Blogger.png",
      },
    ],
  }),
  methods: {
    pronounce() {
      const audio = new Audio("/audio/pronunciation.mp3");
      audio.play();
    },
  },
  components: {
    Link,
  },
  created: () => {
    document.title = "Eyzi";
  },
});
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Noto+Serif&family=Source+Sans+Pro&display=swap");

a,
a:link,
a:hover,
a:visited {
  text-decoration: none;
  color: var(--eyzi-color);
  font-family: var(--text-font2);
}

@media only screen and (max-width: 600px) {
  .full-avatar {
    display: none;
  }

  .min-avatar {
    display: inline-block;
    width: 250px;
    margin-top: 30px;
  }

  .columns {
    display: block;
  }

  .left,
  .right {
    text-align: center;
  }

  #header {
    padding-top: 1em;
  }
}

@media only screen and (min-width: 600px) {
  .full-avatar {
    display: inline-block;
  }

  .min-avatar {
    display: none;
  }

  .columns {
    display: flex;
  }

  .left {
    width: 50%;
    text-align: right;
  }

  .right {
    width: 50%;
    max-width: 20em;
    text-align: left;
  }

  #header {
    padding-top: 7em;
    margin: auto;
    width: 10em;
    text-align: center;
  }
}

.home {
  min-width: 100vw;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #131313;
  color: white;
}

.title-header {
  font-size: 3em;
  font-family: var(--text-font);
}

.eyzi-color {
  color: var(--eyzi-color);
}

#links {
  padding: 1em;
  margin: auto;
  text-align: center;
}

#definition {
  font-family: "Times New Roman";
  padding: 1em;
  text-align: center;

  #phonetic {
    letter-spacing: 0.1em;
    cursor: pointer;
  }

  #pos {
    font-style: italic;
  }
}

#info {
  padding: 1em;
  text-align: center;
  font-family: var(--text-font2);
}

.moonlit-icon {
  width: 20px;
  vertical-align: middle;
}

.moonlit-link {
  text-decoration: none;
  color: var(--moonlit-color);
}

#contact {
  margin: 2em;
  font-family: var(--text-font2);
}

#footer {
  font-size: 0.7em;
  padding-bottom: 1em;
  font-family: var(--text-font2);
}
</style>
