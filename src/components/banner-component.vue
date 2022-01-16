<template>

        <div :class="[ mode == 'square' ? 'Banner banner-square' : 'Banner banner-rectangular']" 
             :style="[(carouselOnMobile == true && mobileDevice == true) ? {display: 'none'} : {display: 'grid'}]">
              <div v-for="item in items" :key="item" class="bannerItem"
                  :class="[ 
                    (mode=='rectangle' && item.aspectRatio=='rectangle') ? 'with-img-desktop' :
                    (mode=='rectangle' && item.aspectRatio=='square') ? 'with-img-mobile' :
                    (mode=='square' && item.aspectRatio=='square') ? 'default-img' : '']" >
                          <a :href="item.link">
                              <img v-if="item.type=='image'" 
                                  :src="item.src">
                              <div v-else class="cta">
                                  <span>{{item.title}}</span>
                                  <button>{{item.button}}</button>
                              </div>
                          </a>
              </div>
        </div>

        <div v-if="carouselOnMobile == true && mobileDevice == true"  class="Banner banner-square">
            <div class="cta">
                  <span>{{this.bannerMobileCarouselCta().title}}</span>
                  <button>{{this.bannerMobileCarouselCta().button}}</button>
            </div>
            <Splide :options="{ rewind: true }">
                  <SplideSlide v-for="item in this.bannerMobileCarouselImgs()" :key="item" class="bannerItem">
                        <img  :src="item.src">
                  </SplideSlide>
            </Splide>
        </div>


</template>



<script>
//import CarouselOnMobile from './CarouselOnMobile.vue';
export default {
  name: 'Banner',
  //components : { CarouselOnMobile },
  props: {
    mode: String,
    items: Array,
    carouselOnMobile : Boolean
  },

  
  data() {
    return {
      mobileDevice: {
        type:Boolean,
        default: null
      }
    }
  },

  methods:{
    resize : function(){
          window.addEventListener('resize', function(){
            this.mobileDevice = true
          });
    },
    bannerMobileCarouselImgs: function(){
      return this.items.filter(item => item.type === 'image')
    },
    bannerMobileCarouselCta: function(){
      let ctaItem = this.items.filter(item => item.type === 'cta')
      return ctaItem[0]
    }
  },

  mounted(){
    if(window.innerWidth < 767){
      this.mobileDevice = true
    }
  }

}
</script>

<style scoped>
a{
   text-decoration: none;
}
.Banner{
  margin:auto;
  width:85%;
  margin-bottom:20px;
}
.banner-square{
  display: grid;
  grid-template-columns: repeat(3,1fr);
}
.banner-rectangular{
  display: grid;
  grid-template-columns: 2fr 1fr
}
.banner-square .bannerItem{
  aspect-ratio: 1 / 1;  
}
.banner-rectangular img,
.banner-square img{
  width:100%;
  height:100%;
  display: block;
}

.banner-rectangular .with-img-mobile{
  display:none;
}
.cta{
  aspect-ratio: 1 / 1;
  height:100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color:#D95FA7;
  text-align: center;
  color:white;
}
.cta span{
  font-size:2em;
  line-height:1.4;
  padding: 1rem 2rem;
}
.cta button{
  height: 40px;
  min-width:200px;
  border : 2px solid white;
  background: transparent;
  color:white;
  transition: all .5s;
  min-width: 220px;
}
.cta button:hover{
  background: white;
  color:black;
}
/* Portrait tablets and small desktops */
@media (min-width: 768px) and (max-width: 991px) {
    .Banner{
      width:100%;
    }
    .cta span{
      font-size: 1.5rem;
    }
}
/* Landscape phones and portrait tablets */
@media (max-width: 767px) {
  .Banner{
      width:100%;
  }
 .banner-rectangular,.banner-square{
    grid-template-columns: 1fr;
  }
  .cta{
    aspect-ratio: 2 / 1;
  }
  .cta span{
      font-size: 1.5rem;
  }
  .cta button{
        width: 80%
  }
  .banner-square .bannerItem{
    aspect-ratio: 0/0;  
  }
  .banner-rectangular .with-img-mobile{
    display:block;
  }
  .banner-rectangular .with-img-desktop{
    display:none;
  }
}
</style>
