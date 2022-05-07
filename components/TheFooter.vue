<template>
  <footer class="footer">
    <div class="footer__head">
      <a href="#"><img class="logo" src="~static/img/Logo.svg" alt=""></a>
      <ul class="socials">
        <li><a href=""><img src="~static/img/youtube.svg" alt="youtube"></a></li>
        <li><a href=""><img src="~static/img/linkedin.svg" alt="linkedin"></a></li>
        <li><a href=""><img src="~static/img/instagram.svg" alt="instagram"></a></li>
        <li><a href=""><img src="~static/img/facebook.svg" alt="facebook"></a></li>
      </ul>
      <div class="apps">
        <a href="#"><img src="~static/img/googlePlay.svg" alt=""></a>
        <a href="#"><img src="~static/img/appStore.svg" alt=""></a>
      </div>
    </div>
    <div class="delimetr"></div>
    <div class="footer__end">
      <nav>
        <ul>
          <li><a href="javascript:void(0);">Releases</a></li>
          <li><a href="javascript:void(0);">Privacy</a></li>
          <li><a href="javascript:void(0);">Terms</a></li>
          <li><a href="javascript:void(0);">Terms for brokers</a></li>
          <li><a href="javascript:void(0);">Do you have any questions? visit our FAQ</a></li>
        </ul>
      </nav>
      <p class="address">Rommates Tecnologia LTDA - CNPJ 18.805.299/0001-17 - CRECI/SP nº 037469-J</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "TheFooter",
}
</script>

<style lang="scss">
.footer {
  display: flex;
  flex-direction: column;
  .delimetr {
    height: 1px;
    background: #C8CFD2;
    opacity: .43;
  }
  &__head {
    max-width: 1170px;
    width: 100%;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 27px 0;
    .logo {
      max-height: 40px;
      margin-right: 40px;
      transition: all 300ms;
      &:hover {
        filter: drop-shadow(1px 4px 2px lightgrey);
      }
    }
    .socials {
      max-width: 220px;
      width: 100%;
      margin-right: auto;
      padding: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      max-height: 40px;
      li {
        height: 40px;
        transition: all 300ms;
        a {
          display: block;
          height: 40px;
          transition: all 300ms;
        }
      }
      li:hover a {
        transform: rotate(30deg);
      }
    }
    .apps {
      max-width: 380px;
      width: 100%;
      display: flex;
      justify-content: space-between;
      max-height: 50px;
      a {
        transition: all 300ms;
      }
      a:hover {
        filter: blur(50px);
      }
    }
  }
  &__end {
    max-width: 1170px;
    width: 100%;
    margin: 0 auto;
    padding: 18px 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    ul {
      display: flex;
      padding: 0;
    }
    li {
      margin-right: 30px;
      a {
        font-family: 'Roboto';
        font-style: normal;
        font-weight: 400;
        font-size: 12px;
        line-height: 14px;
        color: #63686B;
        &:hover {
          text-decoration: underline;
        }
      }
    }
    .address {
      font-family: 'Roboto';
      font-style: normal;
      font-weight: 400;
      font-size: 12px;
      line-height: 14px;
      color: #63686B;
      margin: 0;
    }
  }
}
@media screen and (max-width: 1440px) {
  .footer {
    &__head {
      flex-direction: column;
      .logo {
        margin: 0 auto 30px;
      }
      .socials {
        margin: 0 auto 30px;
      }
      .apps {
        max-height: unset;
        flex-direction: column;
        a {
          text-align: center;
        }
      }
    }
    &__end {
      flex-direction: column;
      padding: 30px 45px;
      ul {
        flex-direction: column;
        margin-bottom: 10px;
        li {
          margin: 0;
          line-height: 1;
          text-align: center;
          margin-bottom: 20px;
        }
      }
      .address {
        text-align: center;
      }
    }
  }
}
</style>