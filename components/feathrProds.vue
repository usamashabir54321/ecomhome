<template>
	<section class="featured" id="featured">
		<h1 class="heading"> <span>featured</span> products </h1>
		<div v-for="(feathr , indexOne) in feathrProds" :key="indexOne" class="row">
			<div class="image-container">
				<div class="small-image">
					<img 
					v-for="(gal , indexTwo) in feathr.gall" :key="indexTwo" :src="`https://attakus.masoodapp.com/static/gall/${gal.src}`" @click="chngFeathImg(indexOne,indexTwo)" class="featured-image-1" 
					:class="indexOne == manProdIndx ? indexTwo == subProdIndx ? 'active' : '' : ''"
					>
				</div>
				<div class="big-image">
					<img :src="`https://attakus.masoodapp.com/static/gall/${feathr.src}`" class="big-image-1" alt="">
				</div>
			</div>
			<div class="content">
				<h3>{{ feathr.title }}</h3>
				<div class="stars">
					<i class="fas fa-star"></i>
					<i class="fas fa-star"></i>
					<i class="fas fa-star"></i>
					<i class="fas fa-star"></i>
					<i class="far fa-star"></i>
				</div>
				<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dicta facilis praesentium odit voluptas illum iure libero quis fuga commodi. Autem.</p>
				<div class="price">$80.99 <span>$120.99</span></div>
				<a href="#" class="btn">add to cart</a>
			</div>
		</div>
	</section>
</template>

<script>
	export default {
		props: ['feathrProds'],
		data () {
			return {
				manProdIndx: null,
				subProdIndx: null,
			}
		},
		methods: {
			chngFeathImg (indexOne,indexTwo) {
				this.feathrProds[indexOne].src = this.feathrProds[indexOne].gall[indexTwo].src;
				this.manProdIndx = indexOne;
				this.subProdIndx = indexTwo;
			},
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