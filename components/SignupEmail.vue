<template>
  <div class="modal is-active">
    <div class="modal-background"></div>
    <div class="modal-content">
      <div class="logo">
        <img
          src="../assets/images/ipedit.png"
          alt="../assets/images/ipedit.png"
        />
      </div>

      <p class="signup-title">회원가입</p>

      <div class="services">
        <h3>서비스 및 유형 <span>*</span></h3>
        <p>
          어머니 이름을 까닭이요, 계집애들의 봅니다. 별 피어나듯이 그리워
          이름과.
        </p>
      </div>

      <!-- tabs -->
      <div class="tabs-containe">
        <ul>
          <li
            class=""
            v-on:click="ShowTabContent(1)"
            v-bind:class="{ isActive: idTabs === 1 }"
          >
            <img
              src="../assets/images/draft.png"
              alt="../assets/images/draft.png"
            />
          </li>
          <li
            class=""
            v-on:click="ShowTabContent(2)"
            v-bind:class="{ isActive: idTabs === 2 }"
          >
            <img
              src="../assets/images/translate.png"
              alt="../assets/images/translate.png"
            />
          </li>
        </ul>
      </div>
      <!-- tabs content -->
      <div class="px-2" id="tab-content">
        <!-- content 1 -->
        <div id="product-details" class="content-data" v-if="idTabs === 1">
          <!-- Type of application -->
          <!-- <div class="field">
            <div class="control">
              <div class="select">
                <select>
                  <option>명세서 유형</option>
                </select>
              </div>
            </div>
          </div> -->

          <div
            class="navbar-item has-dropdown"
            v-on:click="activeDropdown = !activeDropdown"
            v-bind:class="{ 'is-active': activeDropdown }"
          >
            <a class="navbar-link"> {{ type }} </a>
            <div
              class="navbar-dropdown"
              style="height: max-content; bacground: #fff"
              :style="[!activeDropdown && { display: 'none' }]"
            >
              <a
                class="navbar-item"
                style="margin-bottom: 10px; border: none"
                v-for="item in arrSelect"
                :key="item"
                v-on:click="selectItem(item)"
              >
                <p>{{ item }}</p>
              </a>
            </div>
          </div>

          <div class="services" style="margin-top: 10px">
            <h3>서비스 및 유형 <span>*</span></h3>
          </div>
          <!-- name -->
          <div class="field">
            <div class="control">
              <input
                class="input"
                type="text"
                placeholder="이름"
                style="border-color: #d2416d"
              />
              <p style="color: #d2416d; font-size: 10px; padding-top: 5px">
                에러메세지는 여기에
              </p>
            </div>
          </div>

          <!-- email -->
          <div class="field field-doubles">
            <div class="control has-icons-left has-icons-right">
              <input
                class="input is-success"
                type="text"
                placeholder="이메일 주소"
              />
            </div>
            <div class="control control-button">
              <button class="button is-link is-light">인증코드 발송</button>
            </div>
          </div>

          <!--verify email -->
          <div class="field field-doubles">
            <div class="control has-icons-left has-icons-right">
              <input
                class="input is-success"
                type="text"
                placeholder="이메일 인증코드"
              />
            </div>
            <div class="control control-button">
              <button class="button is-link is-light">인증하기</button>
            </div>
          </div>

          <!-- password -->
          <div class="field">
            <div class="control">
              <input class="input" type="text" placeholder="비밀번호" />
            </div>
          </div>

          <!-- password confirm-->
          <div class="field">
            <div class="control">
              <input class="input" type="text" placeholder="비밀번호 재입력" />
            </div>
          </div>

          <!-- COUNTRY -->
          <div class="services">
            <h3>휴대폰 인증 <span>*</span></h3>
          </div>
          <!-- Select country -->
          <div class="select-country">
            <div
              class="navbar-item has-dropdown field"
              style="width: 27%"
              v-on:click="activeCountry = !activeCountry"
              v-bind:class="{ 'is-active': activeCountry }"
            >
              <a class="navbar-link">
                <img
                  v-bind:style="[
                    country === '' ? { display: 'none' } : { display: 'block' },
                  ]"
                  src="../assets/images/Korea.png"
                />
                {{ country.dial_code }}
              </a>
              <div
                class="navbar-dropdown"
                style="background: #fff"
                :style="[!activeCountry && { display: 'none' }]"
              >
                <a
                  class="navbar-item item__country"
                  v-for="item in countries"
                  :key="item"
                  v-on:click="selectCountry(item)"
                >
                  <img src="../assets/images/Korea.png" />
                  <span class="nameCountry">{{ item.name }}</span>
                  <span class="dial_code">{{ item.dial_code }}</span>
                </a>
              </div>
            </div>

            <!-- Phone -->
            <div class="field field-doubles">
              <div class="control">
                <input class="input" type="text" placeholder="휴대폰 번호" />
              </div>
              <div class="control control-button">
                <button class="button is-link is-light">인증코드 발송</button>
              </div>
            </div>
          </div>

          <!-- Phone Code-->
          <div class="field field-doubles">
            <div class="control">
              <input class="input" type="text" placeholder="휴대폰 인증코드" />
            </div>
            <div class="control control-button">
              <button class="button is-link is-light">인증하기</button>
            </div>
          </div>

          <!-- Promotion code -->
          <div class="services">
            <h3>프로모션 코드</h3>
          </div>

          <!-- apply Code-->
          <div class="field field-doubles">
            <div class="control">
              <input class="input" type="text" placeholder="프로모션 코드" />
            </div>
            <div class="control control-button">
              <button class="button is-link is-light">적용하기</button>
            </div>
          </div>

          <div class="services">
            <p>
              회원가입 시 IPEDIT의 이용약관과 개인정보처리방침에 동의하게
              됩니다.
            </p>
          </div>

          <!-- button submit -->
          <div class="field is-grouped">
            <div class="control btn-submit">
              <button class="button is-link">가입하기</button>
            </div>
          </div>
        </div>

        <!-- content 2 -->
        <div
          id="delivery-informations"
          class="content-data"
          v-if="idTabs === 2"
        >
          <!-- <h3 class="is-size-5 title">Delivery informations</h3>
          <p>delivery</p> -->
        </div>
      </div>
    </div>
    <button
      class="modal-close is-large"
      aria-label="close"
      v-on:click="changeModalSignUp"
    ></button>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/stylesheets/signUp.scss";
</style>

<script>
import { Country } from "../assets/javascripts/data";
export default {
  data() {
    return {
      idTabs: 1,
      countries: Country,
      arrSelect: ["명세서 유형", "명세서 유형1", "명세서 유형2"],
      activeDropdown: false,
      activeCountry: false,
      type: "명세서 유형",
      country: "",
    };
  },
  props: {
    modalLogin: Boolean,
  },
  components: {},
  methods: {
    ShowTabContent: function (data) {
      this.idTabs = data;
    },
    changeModalSignUp: function () {
      this.$emit("changeModalSignUp");
    },
    selectItem: function (item) {
      this.type = item;
    },
    selectCountry: function (item) {
      this.country = item;
    },
  },
};
</script>
