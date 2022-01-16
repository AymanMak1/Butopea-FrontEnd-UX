<template>
<banner-component
  mode="square"
  :carouselOnMobile="false"
  :items="[
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/500',
      link: 'https://example.com/link1'
		},
    {
			type: 'cta',
			title: 'CTA Title',
      button: 'CTA Button',
      link: 'https://example.com/link2'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/400',
      link: 'https://example.com/link3'
		}
	]"
>
</banner-component>


<banner-component
  mode="square"
  :carouselOnMobile="true"
  :items="[
    {
			type: 'cta',
			title: 'CTA Title',
      button: 'CTA Button',
      link: 'https://example.com/link1'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/700',
      link: 'https://example.com/link2'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/800',
      link: 'https://example.com/link3'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/900',
      link: 'https://example.com/link3'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/1000',
      link: 'https://example.com/link3'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/1200',
      link: 'https://example.com/link3'
		}
	]"
>
</banner-component>



<banner-component
  mode="rectangle"
  :carouselOnMobile="false"
  :items="[
		{
			type: 'image',
			aspectRatio: 'rectangle',
			src: 'https://picsum.photos/1200/400',
      link: 'https://example.com/link1'
		},
		{
			type: 'image',
			aspectRatio: 'square',
			src: 'https://picsum.photos/800',
      link: 'https://example.com/link1'
		},
    {
			type: 'cta',
			title: 'CTA Title',
      button: 'CTA Button',
      link: 'https://example.com/link1'
		}
	]"
>
</banner-component>

</template>

<script>
import BannerComponent from './components/banner-component.vue'

export default {
  name: 'App',
  components: {
    BannerComponent,

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  text-decoration: none;
}
</style>
