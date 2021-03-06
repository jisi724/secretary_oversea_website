<template>
  <div class="landing-page">
    <!-- HERO HEADING -->
    <section class="top-banner">
      <div class="banner-shape desktop-only">
        <img src="~assets/images/banner_shape.png" alt="shape" />
      </div>
      <div class="banner-image mobile-only">
        <img src="~assets/images/mobile-bg.png" alt="Illustrations" />
      </div>
      <div class="banner-body container">
        <div class="columns is-centered wrapper">
          <div class="column is-three-fifths">
            <Slogan />
            <h2 class="subtitle m-b-70">
              The future of call forwarding with HeyTico’s AI-powered phone
              assistant.
            </h2>
            <Button
              v-if="!user"
              tag="a"
              :href="signup"
              text="Try Now"
              sub-text="It's free"
            />
            <Button
              v-if="user"
              tag="router-link"
              to="/call-history"
              text="Try Now"
              sub-text="It's free"
            />
          </div>
          <div class="column is-two-fifths messager">
            <img src="~assets/images/messager.png" alt="Illustrations" />
          </div>
        </div>
      </div>
    </section>

    <!-- PRODUCT SECTION -->
    <section id="product" class="section product-section">
      <div class="container">
        <div class="columns is-mobile wrapper">
          <div class="column is-two-fifths">
            <img
              src="~assets/images/logo_shadow.png"
              alt="Logo"
              class="product-logo"
            />
          </div>
          <div class="column">
            <h2 class="title m-b-25 is-spaced has-text-centered-mobile">
              Is voicemail <br />
              the only place for missed calls?
            </h2>
            <h5 class="subtitle has-text-centered-mobile">
              Whether you are busy or do not want to answer a call, your
              personal assistant can help you answer your call anywhere,
              anytime, with the appropriate answer.
            </h5>
          </div>
        </div>
      </div>
    </section>

    <!-- FEATURE SECTION -->
    <section class="section">
      <div class="container">
        <h2 class="title m-b-25 has-text-centered">
          Works on Any Phone You Have
        </h2>
        <div class="wrapper">
          <TextImage
            title="Different Scenarios, Different Answers"
            sub-title="Unlike your regular voicemail that only has one answer for all,
                HeyTico has answers for all your callers."
            image="icon1.png"
          />
          <TextImage
            title="Your Time is Valuable"
            sub-title="Stop wasting your time on listening to voice mails and answering spam calls. Get an assistant to save that time and enjoy life!"
            image="icon2.png"
            :inverse="true"
          />
          <TextImage
            title="Beyond an Answering Machine"
            sub-title="From answering with appropriate answers to taking down messages, HeyTico helps you eliminate spam calls and focus more on the calls and messages that matter."
            image="icon3.png"
          />
        </div>
      </div>
    </section>

    <!-- HOW IT WORKS SECTION -->
    <section id="how-it-works" class="section video-section">
      <div class="container">
        <h2 class="title m-b-60 has-text-centered">
          How Does HeyTico Work?
        </h2>
        <div class="wrapper m-b-60">
          <div class="video">
            <Video />
          </div>
        </div>
      </div>
    </section>

    <!-- TESTIMONIAL SECTION -->
    <section class="section testimonial-section">
      <div class="container">
        <h2 class="title m-b-60 has-text-centered inverse-color">
          Everyone Can Have a Personal Assistant
        </h2>
        <div class="wrapper m-b-60">
          <Testimonials />
        </div>
      </div>
      <div class="shape-1">
        <img src="~assets/images/shape-1.png" alt="shape" />
      </div>
    </section>

    <!-- PRICE SECTION -->
    <section id="pricing" class="section pricing-section">
      <div class="container">
        <h2 class="title m-b-60 has-text-centered">
          Plans and Pricing
        </h2>
        <div class="wrapper m-b-60">
          <Plans :user="user" :signup="signup" />
        </div>
      </div>
    </section>

    <!-- CTA SECTION -->
    <section class="section">
      <div class="container">
        <h2 class="title m-b-60 has-text-centered">
          Your Personal Assistant Awaits
        </h2>
        <div class="wrapper m-b-60 CTA">
          <p class="m-b-45">
            Get started today for free and find out <br />
            what your personal assistant can do for you!
          </p>
          <Button
            v-if="!user"
            tag="a"
            :href="signup"
            text="Try Now"
            sub-text="It's free"
          />
          <Button
            v-if="user"
            tag="router-link"
            to="/call-history"
            text="Try Now"
            sub-text="It's free"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Button from '~/components/utils/Button.vue'
import Slogan from '~/components/landingPage/Slogan.vue'
import TextImage from '~/components/landingPage/TextImage.vue'
import Video from '~/components/landingPage/Video.vue'
import Testimonials from '~/components/landingPage/Testimonials.vue'
import Plans from '~/components/landingPage/Plans.vue'

export default {
  name: 'HomePage',
  components: { Button, Slogan, TextImage, Video, Testimonials, Plans },
  data() {
    return {
      user: this.$store.getters['auth/loggedIn'],
      signup: `https://passport.mobvoi.com/pages/register?lang=en-us&from=secretary-oversea&redirect_url=${process.env.returnUrl}/get-started`
    }
  }
}
</script>

<style lang="scss" scoped>
/* Reset Style for Landing Page only */
.subtitle,
h1,
h2,
h3,
h4,
h5,
h6,
span,
p {
  line-height: 1.6;
}

@include mobile {
  h1 {
    font-size: 19px;
    line-height: 32px;
  }

  h2 {
    font-size: 17px;
    line-height: 26px;
  }

  h4,
  h5,
  p,
  span {
    font-size: 13px;
    line-height: 20px;
  }

  .column {
    padding-left: 0px;
    padding-right: 0px;
  }

  section {
    max-width: 560px;
    margin: 0 auto;
  }

  .title.m-b-60 {
    margin-bottom: 20px !important;
  }
}

.landing-page {
  font-size: $size-4;
}

.wrapper {
  width: 80%;
  margin: 0 auto;

  @include touch {
    width: 85%;
    width: 100%;
  }
}

.section {
  z-index: 1;
  position: relative;
}

.top-banner {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  width: 100%;
  background: $white;

  .subtitle {
    color: $colored-bg;
    max-width: 520px;
  }

  @include mobile {
    min-height: inherit;
    flex-direction: column;

    .subtitle {
      color: #59687a;
      margin-bottom: 1.5rem !important;
    }

    .wrapper {
      overflow: hidden;
    }
  }

  .banner-shape {
    position: absolute;
    top: 0;
    left: 0;
  }

  .banner-body {
    width: 85%;

    @include mobile {
      width: 80%;

      .wrapper {
        margin-top: -3rem;
      }
    }
  }

  .messager {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    transform: scale(1.2);

    @include mobile {
      display: none;
    }
  }
}

.product-section {
  padding-top: 5rem;

  .product-logo {
    width: 325px;

    @include mobile {
      width: 100%;
    }
  }

  @include mobile {
    h2 {
      text-align: left !important;
      margin-bottom: 1rem;
    }

    h5 {
      color: #59687a;
      text-align: left !important;
    }
  }
}

.minor-container {
  width: 85%;
  margin-left: auto;
  margin-right: auto;
}

.video {
  width: 70%;
  margin: 0 auto;

  @include mobile {
    width: 100%;
  }

  video {
    width: 100%;
  }
}

@include mobile {
  .pricing-section {
    margin-top: -8rem;
  }
}

.video-section {
  z-index: 2;
}

.testimonial-section .shape-1 {
  position: absolute;
  z-index: -2;
  top: -32rem;
  left: 0;

  @include mobile {
    top: -12rem;
  }
}

.inverse-color {
  color: $white;
}

.CTA {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;

  @include mobile {
    p {
      margin-bottom: 2rem;
    }
  }
}
</style>
