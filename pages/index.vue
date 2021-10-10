<template>
	<div>
			<!-- WEB HOME SLIDER -->
		<hero-slider :sliderArr="sliderArr"/>
			<!-- MY LATEST PRODUCTS DYNAMICS -->
		<all-product :products="prodsArr"/>
			<!-- MY FEATHURES PRODUCTS DYNAMICS -->
		<feathr-prods :feathrProds="feathProdsArr"/>
	</div>
</template>

<script>
	export default {
		data () {
			return {
				prodsArr: [],
				sliderArr: [],
				feathProdsArr: [],
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