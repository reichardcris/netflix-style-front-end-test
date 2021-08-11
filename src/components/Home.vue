<template>
  <div class="main-content netflix-font-sans-regular">
    <div class="main-content-container">
      <span class="billboard-slideshow">
        <div class="billboard-row">
          <div class="billboard-pane">
            <div class="billboard-container">
              <img src="../assets/images/billboard.webp" alt="" srcset="" />
              <div class="billboard-black-dip-layer"></div>
              <div class="contents-black-dip-layer"></div>
              <div class="label-component-layer">
                <span class="color-white">TV-PG</span>
              </div>
            </div>
            <div class="billboard-fill">
              <div class="billboard-title-container">
                <div class="billboard-title">
                  <img
                    src="../assets/images/billboard_title.webp"
                    alt=""
                    srcset=""
                  />
                </div>
                <div class="billboard-info">
                  <div class="billboard-info-wrapper">
                    <div class="billboard-label">Watch Season 3 Now</div>
                    <div class="billboard-synopsis">
                      <div class="synopsis">
                        The colorful crew at Gotham Garage overhauls an eclectic
                        collection of cars and trucks, trading up to a
                        showstopper they can sell for big bucks.
                      </div>
                    </div>
                  </div>
                </div>
                <div class="billboard-button-link">
                  <a href="#">
                    <button class="play-btn color-black bg-white">
                      <svg viewBox="0 0 24 24">
                        <path d="M6 4l15 8-15 8z" fill="currentColor"></path>
                      </svg>
                      <span class="play-title">
                        Play
                      </span>
                    </button>
                  </a>
                  <button class="info-btn color-white bg-trans-gray">
                    <div class="info-icon">
                      <svg viewBox="0 0 24 24">
                        <path
                          d="M22 12c0 5.523-4.477 10-10 10S2 17.523 2 12 6.477 2 12 2s10 4.477 10 10zm-2 0a8 8 0 0 0-8-8 8 8 0 0 0-8 8 8 8 0 0 0 8 8 8 8 0 0 0 8-8zm-9 6v-7h2v7h-2zm1-8.75a1.21 1.21 0 0 1-.877-.364A1.188 1.188 0 0 1 10.75 8c0-.348.123-.644.372-.886.247-.242.54-.364.878-.364.337 0 .63.122.877.364.248.242.373.538.373.886s-.124.644-.373.886A1.21 1.21 0 0 1 12 9.25z"
                          fill="currentColor"
                        ></path>
                      </svg>
                    </div>
                    <span class="info-title">
                      More Info
                    </span>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </span>
      <div class="new-release-row">
        <h2 class="row-title-display">
          <a href="">
            <div class="row-title">New Release</div>
          </a>
        </h2>
        <div class="row-body">
          <div class="track-container">
            <div class="hover-field">
              <div class="carousel-slider">
                <span class="handle handle-prev">
                  <font-awesome-icon
                    class="indicator-icon"
                    :icon="['fas', 'chevron-left']"
                  />
                </span>
                <div class="carousel">
                  <div class="inner-carousel">
                    <div class="carousel-content">
                      <div
                        v-for="(nr, index) in new_release.list"
                        :key="index"
                        class="slider-item"
                      >
                        <div class="item-card">
                          <div class="item-card-container">
                            <div class="item-card-title">
                              <a href="#">
                                <div class="item-card-box">
                                  <img :src="nr.Poster" alt="" />
                                </div>
                              </a>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <span class="handle handle-next">
                  <font-awesome-icon
                    class="indicator-icon"
                    :icon="['fas', 'chevron-right']"
                  />
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      new_release: {
        list: [],
        total: 0,
      },
    };
  },
  created() {
    this.getData();
  },
  mounted() {
    this.ini();
  },
  methods: {
    getData() {
      var axios = require("axios");

      var config = {
        method: "get",
        url:
          "https://movie-database-imdb-alternative.p.rapidapi.com/?r=json&s=john",
        headers: {
          "x-rapidapi-key":
            "9ba0420259msh5c85aeab50cba8ep17e631jsncd0c4406aace",
          "x-rapidapi-host": "movie-database-imdb-alternative.p.rapidapi.com",
        },
      };

      axios(config)
        .then((res) => {
          this.new_release.list = res.data.Search;
          this.new_release.total = res.data.totalResults;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    ini() {
      document.addEventListener(
        "DOMContentLoaded",
        function() {
          const prev = document.querySelector(".handle-prev");
          const next = document.querySelector(".handle-next");
          const carousel = document.querySelector(".carousel");
          const track = document.querySelector(".carousel-content");
          let width = carousel.offsetWidth;
          let index = 0;
          window.addEventListener("resize", function() {
            width = carousel.offsetWidth;
          });
          next.addEventListener("click", function(e) {
            e.preventDefault();
            index = index + 1;
            prev.classList.add("show");
            track.style.transform = "translateX(" + index * -width + "px)";
            if (track.offsetWidth - index * width < index * width) {
              next.classList.add("hide");
            }
          });
          prev.addEventListener("click", function() {
            index = index - 1;
            next.classList.remove("hide");
            if (index === 0) {
              prev.classList.remove("show");
            }
            track.style.transform = "translateX(" + index * -width + "px)";
          });
        },
        false
      );
    },
  },
};
</script>
