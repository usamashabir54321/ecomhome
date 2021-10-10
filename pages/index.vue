<template>
	<div>
			<!-- WEB HOME SLIDER -->
		<section class="home" id="home">
		    <div v-for="(sldr , index) in sliderArr" :key="index" :class="[index == sldrIdx ? 'active' : '']" class="slide-container">
		        <div class="slide" :style="`background:url(/slider/${sldr.bgImg});`">
		            <div class="content">
		                <span>nike red shoes</span>
		                <h3>{{ sldr.title }}</h3>
		                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Repellat maiores et eos eaque veritatis aut laboriosam earum dolorem iste atque.</p>
		                <a href="#" class="btn">add to cart</a>
		            </div>
		            <div class="image">
		                <img :src="`/slider/${sldr.src}`" class="shoe" alt="">
		                <img :src="`/slider/${sldr.textImg}`" class="text" alt="">
		            </div>
		        </div>
		    </div>
		    <div id="prev" @click="sldrIdx -= 1">&#8592;</div>
		    <div id="next" @click="sldrIdx += 1">&#8594;</div>
		</section>
			<!-- MY LATEST PRODUCTS DYNAMICS -->
		<section class="products" id="products">
		    <h1 class="heading">latest<span>products</span> </h1>
		    <div class="box-container">

		        <div v-for="(prod , index) in prodsArr" :key="index" class="box">
		            <div class="icons">
		                <a href="#" class="fas fa-heart"></a>
		                <a href="#" class="fas fa-share"></a>
		                <a href="#" class="fas fa-eye"></a>
		            </div>
		            <img :src="`/products/${prod.src}`" alt="">
		            <div class="content">
		                <h3>{{ prod.title }}</h3>
		                <div class="price">$120.99 <span>$150.99</span></div>
		                <div class="stars">
		                    <i class="fas fa-star"></i>
		                    <i class="fas fa-star"></i>
		                    <i class="fas fa-star"></i>
		                    <i class="fas fa-star"></i>
		                    <i class="far fa-star"></i>
		                </div>
		                <a href="#" class="btn">add to cart</a>
		            </div>
		        </div>

		    </div>
		</section>
			<!-- MY FEATHURES PRODUCTS DYNAMICS -->
		<section class="featured" id="featured">
		    <h1 class="heading"> <span>featured</span> products </h1>
		    <div v-for="(feathr , indexOne) in feathProdsArr" :key="indexOne" class="row">
		        <div class="image-container">
		            <div class="small-image">
		                <img 
		                	v-for="(gal , indexTwo) in feathr.gall" :key="indexTwo" :src="`/gall/${gal.src}`" @click="chngFeathImg(indexOne,indexTwo)" class="featured-image-1" 
		                	:class="indexOne == manProdIndx ? indexTwo == subProdIndx ? 'active' : '' : ''"
		                >
		            </div>
		            <div class="big-image">
		                <img :src="`/gall/${feathr.src}`" class="big-image-1" alt="">
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

	</div>
</template>

<script>
	export default {
		data () {
			return {
				prodsArr: [],
				sliderArr: [],
				feathProdsArr: [],
				manProdIndx: null,
				subProdIndx: null,
				sldrIdx: 0,
			}
		},
		async fetch() {
			await this.getMyProds();
		},
		fetchDelay: 1000,
		methods: {
			async getMyProds() {
				const prods = [
					{src:'prod1.png',title:'Product 1'},
					{src:'prod2.png',title:'Product 2'},
					{src:'prod3.png',title:'Product 3'},
					{src:'prod4.png',title:'Product 4'},
					{src:'prod5.png',title:'Product 5'},
					{src:'prod6.png',title:'Product 6'},
					{src:'prod7.png',title:'Product 7'},
					{src:'prod8.png',title:'Product 8'},
					{src:'prod9.png',title:'Product 9'},
					{src:'prod10.png',title:'Product 10'},
					{src:'prod11.png',title:'Product 11'},
					{src:'prod12.png',title:'Product 12'},
				];
				const featureProds = [
					{
						src:'prod7.png',
						title:'Product 1',
						gall: [
							{src:'fgall1.png'},
							{src:'fgall2.png'},
							{src:'fgall3.png'},
							{src:'fgall4.png'},
						],
					},
					{
						src:'prod8.png',
						title:'Product 2',
						gall: [
							{src:'fgall5.png'},
							{src:'fgall6.png'},
							{src:'fgall7.png'},
							{src:'fgall8.png'},
						],
					},
					{
						src:'prod9.png',
						title:'Product 3',
						gall: [
							{src:'fgall9.png'},
							{src:'fgall10.png'},
							{src:'fgall11.png'},
							{src:'fgall12.png'},
						],
					},
				];
				const slider = [
					{
						src:'sldr1.png',
						title:'Product 1',
						textImg:'run1.png',
						bgImg:'bg1.jpg',
					},
					{
						src:'sldr2.png',
						title:'Product 2',
						textImg:'run2.png',
						bgImg:'bg2.jpg',
					},
					{
						src:'sldr3.png',
						title:'Product 3',
						textImg:'run3.png',
						bgImg:'bg3.jpg',
					},
				];
				const myProds = await prods;
				const myFeathProds = await featureProds;
				const mySlider = await slider;
				myProds.forEach((prods) => {
					this.prodsArr.push(prods)
				})
				myFeathProds.forEach((feathure) => {
					this.feathProdsArr.push(feathure)
				})
				mySlider.forEach((sldr) => {
					this.sliderArr.push(sldr)
				})
			},
			chngFeathImg (indexOne,indexTwo) {
				console.log('console chngFeathImg');
				this.feathProdsArr[indexOne].src = this.feathProdsArr[indexOne].gall[indexTwo].src;
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

<style>
	img.featured-image-1.active {
	    border: 2px solid #e31a93 !important;
	}
</style>