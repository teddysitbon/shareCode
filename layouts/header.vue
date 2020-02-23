<template>
  <div>
    <header class="header">
      <div class="header-container">
        <div class="header-logo">
          <svg data-v-d9b859de="" height="20" viewBox="0 0 53 20" xmlns="http://www.w3.org/2000/svg" class="logo">
            <path d="m4.53394096 30c-2.52112239-.0594151-4.53394096-2.1202285-4.53394096-4.6420509v-15.3579491h4.53394096zm16.38680044-.0502828h-4.533941v-1.9484601c-.8396229.6369191-1.6078663 1.1208866-2.3047533 1.451917s-1.5281012.4965431-2.4936675.4965431c-1.5616986 0-2.76444039-.4483509-3.6082614-1.345066-.84382101-.8967152-1.26572518-2.2208168-1.26572518-3.9723445v-9.1891892h4.55912948v7.0018856c0 .7123439.0230893 1.3052564.0692686 1.7787555.0461792.4734992.1532296.8652824.3211541 1.1753615.1595284.310079.4009163.5363495.7241712.6788183.3232548.1424688.7745453.2137021 1.3538851.2137021.3862265 0 .8144278-.0712333 1.2846166-.2137021s.9235784-.3519785 1.3601823-.6285355v-10.0062854h4.533941zm17.2308946 0h-5.2770035l-3.9671983-6.1470774-1.2342395 1.4959146v4.6511628h-4.533941v-19.9497172c2.5040265 0 4.533941 2.0299145 4.533941 4.533941v7.5339408l4.8865808-6.2350722.2776693-.3587673h5.243473l-.2945159.3587673-5.0880893 6.0842237zm14.848364-7.1969371c0 2.2455145-.6570394 4.0147426-1.971138 5.3077374s-3.1590978 1.9394825-5.5350531 1.9394825c-2.3759554 0-4.2209546-.6464877-5.5350532-1.9394825s-1.971138-3.0622229-1.971138-5.3077374c0-2.2617276.6611078-4.0370356 1.9833432-5.3259771s3.1631663-1.9334026 5.522848-1.9334026c2.3922289 0 4.2412966.6485143 5.5472583 1.9455624s1.9589328 3.0683028 1.9589328 5.3138173zm-5.4068987 3.3196158c.2847892-.3485817.4983779-.7680894.6407725-1.2585357.1423945-.4904463.2135908-1.1693597.2135908-2.0367606 0-.8025485-.0732304-1.4753821-.2196934-2.018521s-.3498808-.9768328-.6102595-1.3010948c-.2603787-.3323686-.573642-.567455-.9397995-.7052664s-.760788-.206716-1.1839033-.206716c-.4231154 0-.7994383.056745-1.12898.1702367-.3295418.1134917-.6448393.3404717-.9459022.6809468-.2685155.3161555-.4821041.7498495-.6407724 1.3010949-.1586682.5512454-.2380012 1.2443451-.2380012 2.0793198 0 .7458026.0691621 1.3922904.2074883 1.9394825.1383261.5471922.3417439.9869659.6102594 1.3193345.2603787.3161555.5716079.5471887.9336969.6931066.3620891.1459179.7750272.2188758 1.2388267.2188758.3987048 0 .7790961-.066878 1.1411852-.2006361s.6692499-.3587115.9214917-.674867z" fill="#0042da" fill-rule="evenodd" transform="translate(0 -10)" />
          </svg>
          <span class="header-description">
            {{ description }}
          </span>
        </div>
        <div class="header-connexion">
          <a class="logout">
            {{ logout }}
          </a>
          <a class="account">
            John Doe
          </a>
        </div>
      </div>
    </header>
    <nuxt />
  </div>
</template>
<script>
import { LOCALE } from '~/constants/locale.js';
export default {
    created() {
        this.description = LOCALE.HEADER.DESCRIPTION;
        this.logout = LOCALE.LOGOUT.TXT;
    }
};
</script>
<style lang="scss">
@import "~/scss/variables.scss";
html {
  font-family: 'Avenir','Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background: $white;
}
*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
.header {
  width: 100%;
  display: flex;
  height: 80px;
  font-size: 16px;
  &-container {
    display: flex;
    width: 1075px;
    margin: 0 auto;
  }
  &-logo {
    flex-direction: row;
    display: flex;
    -webkit-box-align: center;
    align-items: center;
    -webkit-box-pack: start;
    justify-content: flex-start;
    flex: 1 1 0%;
  }
  &-description {
    color: $greyDark;
    margin-left: 16px;
  }
  &-connexion {
    flex-direction: row;
    display: flex;
    align-items: center;
    cursor: pointer;
    -webkit-box-pack: end;
    justify-content: flex-end;
  }
}
.logout{
  color: $blue;
  margin-right: 24px;
}
.account{
  font-weight: 900;
  color: $blue;
}
@media (max-width: 1075px) {
  .header-container{
    padding: 0;
    width: 792px;
  }
}
@media (max-width: 792px) {
  .header-container{
    padding: 0;
    width: 768px;
  }
}
@media (max-width: 768px) {
  .header-description{
    display: none;
  }
  .header-container{
    padding: 0 16px;
    width: 100%;
  }
  .logout{
    margin-right: 12px;
  }
}
</style>
