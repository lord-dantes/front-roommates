<template>
  <header class="header">
    <div class="toggle-navbar">
      <img src="~static/img/toggleNav.svg" alt="">
    </div>
    <a class="logo" href="#">
      <img src="~static/img/Logo.svg" alt="logo">
    </a>
    <v-text-field
      class="search"
      label="Search something"
      solo
      clearable
      :hide-details="true"
    >
      <template slot="append">
        <v-btn icon>
          <img src="~static/img/search.svg" alt="">
        </v-btn>
      </template>
    </v-text-field>
    <nav class="nav">
      <ul>
        <li><a href="">Places to stay</a></li>
        <li><a href="">Mortgage</a></li>
        <li><a href="">Experiences</a></li>
        <li><a href="">About us</a></li>
        <li>
          <v-badge
            color="#4079FF"
            content="1"
          >
            <img src="~static/img/notify.svg" alt="">
          </v-badge>
        </li>
      </ul>
    </nav>
    <div class="user">
      <div class="user-avatar--mobile">
        <img src="~static/img/account.svg" alt="">
      </div>
      <div class="user-avatar">
        <img src="~static/img/DefaultUserAvatar.png" alt="user-avatar">
      </div>
      <div class="user-info">
        <p class="user-name">Richard Lucas</p>
        <p class="user-job">Renter</p>
      </div>
    </div>
    <v-select
      v-model="language.current"
      :items="language.variables"
      :hide-details="true"
      solo
      label="Standard"
      item-text="abbr"
      item-value="abbr"
      return-object
      class="language-select"
    >
      <template #item="{item}">
        <span class="language-option">{{ item.abbr }}</span>
      </template>
    </v-select>
  </header>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      language: {
        current: {abbr: "US"},
        variables: [{abbr: "US"}, {abbr: "UA"}],
      }
    }
  },
  mounted() {

  },
  methods: {
    
  },
}
</script>

<style lang="scss">
.header {
  max-width: 1920px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 30px 60px;
}
.header .logo {
  margin-right: 40px;
  transition: all 300ms;
  &:hover {
    filter: drop-shadow(1px 4px 2px lightgrey);
  }
}
/*  */
.header .search {
  width: 100%;
  max-width: 464px;
  margin-right: 237px !important;
  padding: 5px 12px !important;
  display: flex;
  justify-content: space-between;
  border: 1px solid #C8CFD2;
  border-radius: 30px;
}
.header .v-input.search .v-input__control .v-input__slot {
  padding-right: 0px !important;
  box-shadow: none !important;
}
.header .search input {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 19px;
  color: #63686B;
  border: 0;
}
/* */
.header .nav {
  min-height: 60px;
  display: flex;
}
.header .nav li{
  margin-right: 30px;
  &:last-child {
    margin-right: 40px;
  }
}
.header .nav ul { 
  display: flex;
  padding: 0;
}
.header .nav li {
  display: flex;
  align-items: center;
}
.header .nav li a {
  display: flex;
  align-items: center;
  height: 100%;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 19px;
  text-align: center;
  color: #1B2125;
}
.header .nav li a:hover {
  color: #4079FF;
}
.header .notification sup {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 16px;
  color: #FFFFFF;
  padding: 3px 7px 2px;
  border-radius: 50px;
  background: #4079FF;
  height: auto;
}
/*  */
.header .user {
  display: flex;
  padding-left: 30px;
  margin-right: 24px;
  border-left: 1px solid #6B6F7B;
}
.header .user-avatar {
  margin-right: 12px;
}
.header .user-info {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
}
.header .user-name {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 19px;
  color: #2E2E2E;
  margin-bottom: 4px;
}
.header .user-job {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 14px;
  color: #4079FF;
  margin-bottom: 7px;
}
/*  */
.header .language-select {
  max-width: 87px;
  margin-right: 6px;
  border: 1px solid #EAEAEA;
  border-radius: 54px;
}
.header .language-select.v-text-field .v-input__control .v-input__slot {
  box-shadow: none !important;
}
.header .language-select .v-select__selections {
  justify-content: flex-end;
}
.header .language-select .v-select__selections input{
  width: 0px;
  height: 0px;
  display: none;
}
.header .language-select .v-input__append-inner {
  padding: 0;
}
.header .language-select .v-select__selection {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 21px;
  margin-right: 0;
}
.language-option {
  width: 100%;
  text-align: center;
  font-size: 18px;
}
.v-list-item--active .language-option {
  font-weight: bold;
}
// 
.toggle-navbar, .user-avatar--mobile { display: none; }
@media screen and (max-width: 1440px) {
  .toggle-navbar, .user-avatar--mobile { display: block; }
  .header {
    padding: 15px;
    *:not(.toggle-navbar, .toggle-navbar img, .logo, .logo *, .user, .user-avatar--mobile, .user-avatar--mobile img) {
      display: none;
    }
    .logo {
      max-width: 164px;
      height: 30px;
      margin: 0;
      img {
        width: 100%;
        height: 100%;
        object-fit: contain;
      }
    }
    .user {
      align-items: center;
      padding: 0;
      margin: 0;
      border: 0;
      &-avatar--mobile {
        display: flex;
        align-items: center;
      }
    }
  }
}
</style>