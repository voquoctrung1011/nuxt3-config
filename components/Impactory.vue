<template>
  <div class="impactory">
    <div class="impactory__container container">
      <div
        class="video"
        v-bind:style="{ backgroundImage: 'url(' + videoArea + ')' }"
      >
        <div class="video-img" v-on:click="modalVideo = !modalVideo">
          <img
            src="../assets/images/playcircle.png"
            alt="../assets/images/playcircle.png"
          />
        </div>
      </div>

      <!-- modal video -->
      <div
        class="modal"
        v-bind:class="{ 'is-active': modalVideo }"
        @keydown.esc="modalVideo = false"
      >
        <div class="modal-background"></div>
        <div class="modal-content">
          <iframe
            width="420"
            height="315"
            src="https://www.youtube.com/embed/hF5b-9iAN1k"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
        </div>
        <button
          class="modal-close is-large"
          aria-label="close"
          v-on:click="modalVideo = false"
        ></button>
      </div>

      <div class="box-containe">
        <div class="module" style="padding: 38px 60px">
          <div class="top">
            <!-- left -->
            <div class="left">
              <div class="left__top">
                <p>1페이지 기준</p>
                <h3>5분</h3>
              </div>
              <div class="left__bottom">MS Word</div>
            </div>
            <!-- rignht -->
            <div class="right">
              <div class="percent">
                <h1>60%</h1>
                <h2>빠르게!</h2>
              </div>
              <div class="minutes">
                <div class="minutes__top">
                  <p>1페이지 기준</p>
                  <h2>2분</h2>
                </div>
                <div class="minutes__bottom">IPEDIT</div>
              </div>
            </div>
          </div>
          <div
            class="bottom"
            v-bind:style="{ backgroundImage: 'url(' + highlight + ')' }"
            style="width: 114px"
          >
            <p>작업 시간</p>
          </div>
        </div>

        <div class="module" style="padding: 38px 30px">
          <div class="top top-module_2">
            <h1>NO</h1>
            <!-- <h2>청구항 인용 오류</h2> -->
          </div>
          <div
            class="bottom"
            v-bind:style="{ backgroundImage: 'url(' + highlight + ')' }"
            style="width: 87px"
          >
            <p>품질</p>
          </div>

          <div class="contentt">
            <div class="contentt__containerr">
              <ul class="contentt__containerr__listt">
                <li class="contentt__containerr__listt__itemm">
                  구성요소 오류
                </li>
                <li class="contentt__containerr__listt__itemm">선행사 오류</li>
                <li class="contentt__containerr__listt__itemm">
                  청구항 인용 오류
                </li>
              </ul>
            </div>
          </div>
        </div>

        <div class="module" style="padding: 38px 30px">
          <div class="top top-module_3">
            <div class="top-img">
              <img
                src="../assets/images/Korea.png"
                alt="../assets/images/Korea.png"
              />
            </div>
            <div class="top-img">
              <img
                src="../assets/images/USA.png"
                alt="../assets/images/USA.png"
              />
            </div>
            <div class="top-img">
              <img
                src="~/assets/images/Sec.png"
                alt="../assets/images/Sec.png"
              />
            </div>
            <div class="top-img">
              <img
                src="../assets/images/Japan.png"
                alt="../assets/images/Japan.png"
              />
            </div>
          </div>
          <div
            class="bottom"
            v-bind:style="{ backgroundImage: 'url(' + highlight + ')' }"
            style="width: 127px"
          >
            <p>사용 국가</p>
          </div>

          <!-- <div class="contentt">
            <div class="contentt__containerr">
              <p class="contentt__containerr__textt">Hello</p>

              <ul class="contentt__containerr__listt">
                <li class="contentt__containerr__listt__itemm">world !</li>
                <li class="contentt__containerr__listt__itemm">bob !</li>
                <li class="contentt__containerr__listt__itemm">users !</li>
                <li class="contentt__containerr__listt__itemm">everybody !</li>
              </ul>
            </div>
          </div> -->
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/impactory.scss";
</style>

<script>
import VideoArea from "../assets/images/VideoArea.png";
import Rectangle3 from "../assets/images/Rectangle 3.png";
import Rectangle6 from "../assets/images/Rectangle 6.png";
import Highlight from "../assets/images/img_highlight_1.png";
export default {
  data() {
    return {
      videoArea: VideoArea,
      rectangle3: Rectangle3,
      rectangle6: Rectangle6,
      highlight: Highlight,
      modalVideo: false,
    };
  },
  components: {},
  mounted() {
    document.onkeydown = (evt) => {
      evt = evt || window.event;
      if (evt.keyCode == 27) {
        this.modalVideo = false;
      }
    };
  },
};
</script>
