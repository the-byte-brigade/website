<script>
  import { Carousel } from 'flowbite-svelte'
  import {images} from './images.js';
  let showThumbs=false
  let showCaptions=false
  
</script>

<div class="max-w-4xl mx-20 my-10">
  <Carousel {images} loop {showCaptions} {showThumbs} duration='3000'/>
</div>

<style>
 
</style>

