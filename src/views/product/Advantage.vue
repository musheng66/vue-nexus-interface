<template>
  <div class="advantage">
    <section class="page card-collection">
      <div class="page-body">
        <div class="content">
          <div class="eben-card" v-for="item in cards" :key="item">
            <figure :style="item.style" @click="onClickItem(item)"></figure>
            <div class="title">
              {{ item.title }}
            </div>
          </div>
        </div>
        <div></div>
      </div>
    </section>

    <section class="page pic-banner">
      <div class="page-body">
        <div class="content">
          <figure :style="picBanner.style" @click="onClickItem(picBanner.item)"></figure>
        </div>
      </div>
    </section>

    <info-nav></info-nav>

  </div>
</template>

<script>
  import InfoNav from '../common/InfoNav'
  import { EbenResourceDomain, EbenDomain } from '../../constants/index'
  import { $utils } from '@helper'

  export default{
    name: 'Advantage',

    data () {
      return {
        cards: [
          {
            title: 'E本定制',
            path: EbenDomain + '/businessproduct/advantagesdetail/customized',
            pathType: '_blank',
            style: {
              backgroundImage: 'url("' + EbenResourceDomain + '/new_images/product_a1.jpg")',
            }
          },
          {
            title: 'E本能力',
            path: EbenDomain + '/businessproduct/advantagesdetail/ability',
            pathType: '_blank',
            style: {
              backgroundImage: 'url("' + EbenResourceDomain + '/new_images/product_a2.jpg")',
            }
          },
          {
            title: 'E本特色',
            path: EbenDomain + '/businessproduct/advantagesdetail/characteristic',
            pathType: '_blank',
            style: {
              backgroundImage: 'url("' + EbenResourceDomain + '/new_images/product_a3.jpg")',
            }
          },
          {
            title: '应用领域',
            path: EbenDomain + '/businessproduct/advantagesdetail/application',
            pathType: '_blank',
            style: {
              backgroundImage: 'url("' + EbenResourceDomain + '/new_images/product_a4.jpg")',
            }
          },
          {
            title: '合作开发',
            path: EbenDomain + '/businessproduct/advantagesdetail/cooperation',
            pathType: '_blank',
            style: {
              backgroundImage: 'url("' + EbenResourceDomain + '/new_images/product_a5.jpg")',
            }
          },
        ],
        picBanner: {
          style: {
            backgroundImage: 'url("' + EbenResourceDomain + '/new_images/k8s_pic.jpg")',
          },
          item: {
            path: '/product/eben?mark=K8S'
          }
        },
      }
    },

    computed: {},

    created () {

      this.$utils.scrollTop();
    },

    mounted () {},

    props: {

    },

    watch: {

    },

    components: {
      InfoNav
    },

    methods: {

      onClickItem(item) {
        console.log(item);
        if (item.pathType === '_blank') {
          window.location.href = item.path;
          return;
        }
        this.$router.push(item.path);
      },

    },

  }
</script>

<style type="text/css" lang="scss">
  @import "../../assets/scss/variables.scss";
  @import "../../assets/scss/mixins.scss";

  #app .advantage {

    section {
      width: $common-content-width-xxs;
      margin: 0 auto;
    }

    section.pic-banner {
      padding-top: $section-padding-top;

      .page-body {

        .content {
          height: 32vw;
          max-height: 350px;
          min-height: 140px;

          figure {
            @include background-image-common("", cover);
            @include transition-common(all, 0.25s, linear);
            opacity: 0.9;
            border: 1px solid #555;
          }

          figure:hover {
            cursor: pointer;
            opacity: 1;
            border-color: $char-hover-color;
          }
        }
      }
    }

    section.card-collection {

    }

    section.page {

      .page-body {

        .content {
          display: flex;
          flex-wrap: wrap;

          .eben-card {
            width: 100%;
            min-width: 285px;
            margin: 0 auto;
            height: 200px;
            cursor: pointer;
            opacity: 0.9;
            @include transition-common(opacity, 0.25s, linear);
            padding: 5px 0;

            figure {
              @include background-image-common("", cover);
            }

            .title {
              width: 100%;
              background: rgba(121, 96, 19, 0.8);
              position: relative;
              bottom: 50px;
              color: #fff;
              height: 40px;
              line-height: 40px;
              padding: 0 15px;
            }
          }

          .eben-card:hover {
            opacity: 1;
          }
        }
      }
    }
  }

  @media (min-width: #{$responsive-width-xs}) {
    #app .advantage {

      section.pic-banner {

        .page-body {

          .content {

            figure {

            }
          }
        }
      }

      section.page {

        .page-body {

          .content {

            .eben-card {
              width: 50%;
              padding: 5px;
            }

            div.eben-card:nth-of-type(1),
            div.eben-card:nth-of-type(3),
            div.eben-card:nth-of-type(5) {
              padding-left: 0;
            }

            div.eben-card:nth-of-type(2),
            div.eben-card:nth-of-type(4),
            div.eben-card:nth-of-type(5) {
              padding-right: 0;
            }
          }
        }
      }
    }
  }

  @media (min-width: #{$responsive-width-small}) {
    #app .advantage {

      section {
        width: $common-content-width-small;
      }

      section.page {

        .page-body {

          .content {

            .eben-card {
              width: 33.3%;
              padding: 5px;
            }

            div.eben-card:nth-of-type(4),
            div.eben-card:nth-of-type(5) {
              width: 50%;
            }

            div.eben-card:nth-of-type(1),
            div.eben-card:nth-of-type(4) {
              padding: 5px 5px 5px 0;
            }

            div.eben-card:nth-of-type(2) {
              padding: 5px;
            }

            div.eben-card:nth-of-type(3),
            div.eben-card:nth-of-type(5) {
              padding: 5px 0 5px 5px;
            }

          }
        }
      }
    }
  }
</style>
