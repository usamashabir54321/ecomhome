<template>
	<section class="home" id="home">
	    <div v-for="(sldr , index) in sliderArr" :key="index" :class="[index == sldrIdx ? 'active' : '']" class="slide-container">
	        <div class="slide" :style="`background:url(https://attakus.masoodapp.com/static/slider/${sldr.bgImg});`">
	            <div class="content">
	                <span>nike red shoes</span>
	                <h3>{{ sldr.title }}</h3>
	                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Repellat maiores et eos eaque veritatis aut laboriosam earum dolorem iste atque.</p>
	                <a href="#" class="btn">add to cart</a>
	            </div>
	            <div class="image">
	                <img :src="`https://attakus.masoodapp.com/static/slider/${sldr.src}`" class="shoe" alt="">
	                <img :src="`https://attakus.masoodapp.com/static/slider/${sldr.textImg}`" class="text" alt="">
	            </div>
	        </div>
	    </div>
	    <div id="prev" @click="sldrIdx -= 1">&#8592;</div>
	    <div id="next" @click="sldrIdx += 1">&#8594;</div>
	</section>
</template>

<script>
	export default {
		props: ['sliderArr'],
		data () {
			return {
				sldrIdx: 0,
			}
		},
		watch: {
			sldrIdx (val) {
				if (val > this.sliderArr.length - 1 || val < 0) {
					this.sldrIdx = 0;
				}
			},
		},
	}
</script>