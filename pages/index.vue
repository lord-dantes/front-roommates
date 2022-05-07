<template>
  <main>
    <section class="banner">
      <h2>See how Roommates Home Loans can help</h2>
      <v-btn class="banner-action">Mortgage calculator</v-btn>
    </section>
    <section class="mortgage">
      <div class="form__wrapper">
        <h3>Take the easy first step toward a mortgage</h3>
        <v-form class="form">
          <p class="form-label">Property value</p>
          <vuetify-money
            v-model="form.valuePayment"
            :label="''"
            :placeholder="''"
            :readonly="false"
            :disabled="false"
            :outlined="false"
            :clearable="false"
            :value-when-is-empty="''"
            solo
            :hide-details="true"
            :options="form.paymentOptions"
            class="form-field"
          />
          <p class="term-info">Term <span>30 years</span></p>
          <p class="down-payment">Down payment: <b>R$ <span>{{ form.downPayment }}</span></b></p>
          <v-slider
            v-model="form.percentMortgage"
            class="form-slider"
            min="0.1"
            step=".01"
            max="0.9"
            :hide-details="true"
          />
          <p class="slider-info"><span>10%</span><span>90%</span></p>
          <div class="finance-info">
            <p>Financing</p>
            <b>R$ <span>{{ 'XXX.XXX' }}</span></b>
          </div>
          <p class="form-label">CPF</p>
          <v-text-field readonly class="form-field" solo value="XXX.XXX.XXX-XX" :hide-details="true"/>
          <v-btn class="form-submit">FUNDING CONSULTATION</v-btn>
        </v-form>
      </div>
    </section>
    <section class="benefits">
      <h2>Benefits</h2>
      <div class="cards">
        <div class="card">
          <div class="card-img">
            <img src="~static/img/benefit1.svg" alt="">
            <img src="~static/img/benefit1a.svg" alt="">
          </div>
          <p class="card-title">Low down payments</p>
          <p class="card-info">We offer a variety of loan options to meet your unique needs.</p>
        </div>
        <div class="card">
          <div class="card-img">
            <img src="~static/img/benefit2.svg" alt="">
            <img src="~static/img/benefit2a.svg" alt="">
          </div>
          <p class="card-title">Works with your timeline</p>
          <p class="card-info">Count on us to respond ASAP and always meet deadlines.</p>
        </div>
        <div class="card">
          <div class="card-img">
            <img src="~static/img/benefit3.svg" alt="">
            <img src="~static/img/benefit3a.svg" alt="">
          </div>
          <p class="card-title">Best-in-class service</p>
          <p class="card-info">Clear communication, friendly staff, and local market expertise.</p>
        </div>
        <div class="card">
          <div class="card-img">
            <img src="~static/img/benefit4.svg" alt="">
            <img src="~static/img/benefit4a.svg" alt="">
          </div>
          <p class="card-title">Total transparency</p>
          <p class="card-info">We'll always keep you and your agent informed and up-to-date.</p>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      form: {
        valuePayment: '250000',
        downPayment: '125.000',
        percentMortgage: 0.5,
        finalPayment: 0,
        paymentOptions: {
          locale: "pt-BR",
          prefix: "R$",
          suffix: "",
          length: 7,
          precision: 0
        }
      }
    }
  },
  watch: {
    "form.valuePayment" (val) {
      this.calcDownPayment(val, this.form.percentMortgage);
    },
    "form.percentMortgage" (val) {
      this.calcDownPayment(this.form.valuePayment, val);
    }
  },
  methods: {
    calcDownPayment(valuePayment = this.form.valuePayment, percentMortgage = this.form.percentMortgage) {
      let downPayment = ((valuePayment).replace('.','') * percentMortgage).toFixed(0);
      downPayment = downPayment.toString().split(".");
      downPayment[0] = downPayment[0].replace(/\B(?=(\d{3})+(?!\d))/g, ".");
      this.form.downPayment = downPayment[0];
    }
  },
}
</script>

<style lang="scss">
main {
  background-color: #F5F6F8;
}
.banner {
  padding: 147px;
  background: linear-gradient(0deg, rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('~static/img/indexBanner.png');
  height: 666px;
  background-size: cover;
  background-position: center;
  h2 {
    max-width: 953px;
    margin: 0 auto 20px;
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 600;
    font-size: 72px;
    line-height: 120%;
    text-align: center;
    color: #FFFFFF;
  }
  .banner &-action.v-btn {
    display: flex;
    height: auto;
    max-width: 290px;
    margin: 0 auto;
    padding: 22px 61px 22px 62px;
    background: #4079FF;
    border-radius: 40px;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 700;
    font-size: 14px;
    line-height: 16px;
    text-align: center;
    text-transform: uppercase;
    color: #FFFFFF;
    transition: all 300ms;
    &:hover {
      background: #fff;
      color: #4079FF;
    }
  }
}
.form {
  max-width: 740px;
  width: 100%;
  & .v-text-field {
    border: 1px solid #C8CFD2;
    border-radius: 30px;
    padding: 10px 20px;
    &.v-text-field--solo {
      padding: 5px 10px;
      & .v-input__control .v-input__slot {
        box-shadow: none;
      }
    }
  }
  .form-label {
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    color: #1B2125;
    margin-bottom: 10px;
  }
  .form-field {
    margin-bottom: 30px;
    .v-input__slot::before, .v-input__slot::after {
      border: none;
    }
  }
  .term-info {
    display: flex;
    justify-content: space-between;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    color: #1B2125;
    margin-bottom: 33px;
    & span {
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 600;
      font-size: 20px;
      line-height: 23px;
      display: flex;
      align-items: center;
      color: #1B2125;
    }
  }
  .down-payment {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 19px;
    color: #1B2125;
    margin-bottom: 22px;
    & b {
      margin: 0 0 0 10px;
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 600;
      font-size: 20px;
      line-height: 23px;
      display: flex;
      align-items: center;
      color: #4079FF;
      & span {
        margin: 0 0 0 4px;
        color: #000;
      }
    }
  }
  &-slider {
    margin-bottom: 10px;
    .v-slider__track-background.primary.lighten-3 {
      background-color: #EAEDF1 !important;
    }
    .v-slider__track-fill.primary {
      background-color: #4079FF !important;
    }
    .v-slider--horizontal .v-slider__track-container {
      height: 4px;
    }
    .v-slider__thumb.primary {
      width: 36px;
      height: 36px;
      left: -16px;
      background-color: #fff !important;
    }
    .v-slider__thumb::before {
      left: 0;
      top: 0;
    }
    .v-slider__thumb-container:hover .v-slider__thumb::before {
      background: transparent;
      border: solid 2px;
      opacity: 1;
    }
    .v-slider__thumb::after {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      background: #4079fe;
    }
  }
  .slider-info {
    display: flex;
    justify-content: space-between;
    span {
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 400;
      font-size: 16px;
      line-height: 19px;
      color: #1B2125;
    }
    margin-bottom: 30px;
  }
  .finance-info {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px;
    border-radius: 10px;
    background: #F4F7FF;
    margin-bottom: 30px;
    p {
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 400;
      font-size: 16px;
      line-height: 19px;
      color: #1B2125;
      margin-bottom: 0;
    }
    b {
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 600;
      font-size: 20px;
      line-height: 23px;
      display: flex;
      align-items: center;
      color: #4079FF;
      span {
        margin-left: 4px;
        color: #000;
      }
    }
  }
  .form &-submit.v-btn {
    width: 100%;
    padding: 22px;
    height: auto;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 700;
    font-size: 14px;
    line-height: 16px;
    text-align: center;
    text-transform: uppercase;
    color: #FFFFFF;
    background: #4079FF;
    border-radius: 40px;
    box-shadow: none;
    transition: all 300ms;
    &:hover {
      opacity: .5;
    }
  }
  &__wrapper {
    margin: 0 auto;
    max-width: 930px;
    width: 100%;
    display: flex;
    align-items: center;
    flex-direction: column;
    padding: 80px 95px;
    background: #FFFFFF;
    box-shadow: 21.5556px 43.1111px 53.0598px rgba(21, 27, 37, 0.07), 2.48718px 4.1453px 17.4103px -9.11966px rgba(28, 69, 97, 0.06), 29.8462px 43.9402px 140.94px -19.8974px rgba(12, 25, 71, 0.08);
    border-radius: 20px;
    & h3 {
      max-width: 560px;
      width: 100%;
      font-family: 'Poppins';
      font-style: normal;
      font-weight: 500;
      font-size: 40px;
      line-height: 120%;
      text-align: center;
      color: #1B2125;
      margin-bottom: 30px;
    }
  }
}
.mortgage {
  margin-top: -163px;
  padding-bottom: 82px;
}
.benefits {
  padding-bottom: 100px;
  h2 {
    font-family: 'Poppins';
    font-style: normal;
    font-weight: 500;
    font-size: 60px;
    line-height: 120%;
    text-align: center;
    color: #1B2125;
    margin-bottom: 50px;
  }
  .cards {
    display: flex;
    justify-content: space-between;
    max-width: 1170px;
    margin: 0 auto;
  }
  .card {
    max-width: 270px;
    padding: 40px 30px 58px;
    background: transparent;
    border: 3px solid #FFFFFF;
    border-radius: 20px;
    transition: all 300ms;
    cursor: pointer;
    &:hover {
      background: #fff;
      img:first-child {
        height: 0;
        opacity: 0;
      }
      img:last-child {
        height: auto;
        opacity: 1;
      }
    }
  }
  .card-img {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    margin-bottom: 40px;
    max-width: 120px;
    max-height: 120px;
    img {
      transition: all 300ms;
      &:first-child {
        object-fit: cover;
      }
      &:last-child {
        height: 0;
        opacity: 0;
      }
    }
  }
  .card-title {
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 500;
    font-size: 28px;
    line-height: 33px;
    color: #1B2125;
    margin-bottom: 20px;
  }
  .card-info {
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 150%;
    color: #63686B;
    margin-bottom: 0;
  }
}
@media screen and (max-width: 1440px) {
  .banner {
    padding: 50px 15px;
    height: 583px;
    h2 {
      max-width: 450px;
      font-size: 36px;
      line-height: 120%;
    }
  }
  .mortgage {
    margin-top: -273px;
    padding-bottom: 50px;
  }
  .form__wrapper {
    max-width: 92%;
    padding: 50px 20px;
    h3 {
      font-size: 24px;
      line-height: 120%;
    }
  }
  .benefits {
    padding-bottom: 50px;
    h2 {
      font-size: 36px;
      line-height: 120%;
      margin-bottom: 30px;
    }
    .cards {
      align-items: center;
      justify-content: center;
      flex-direction: column;
      padding: 0 15px;
    }
    .card {
      max-width: 345px;
      margin-bottom: 30px;
      &:last-child {
        margin-bottom: 0px;
      }
    }
  }
}
</style>