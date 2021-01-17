<template>
	<Hero />
	<About />
	<Skills />
</template>

<script>
import Hero from "./homepage/Hero.vue";
import About from "./homepage/About.vue";
import Skills from "./homepage/Skills.vue";

export default {
  components: {
    Hero,
    About,
    Skills
  }
};
</script>

<style lang="scss">
@use "./../sass/abstracts/abstracts" as abs;


.section {
	height: auto;
	min-height: 25vh;
	width: auto;
	max-width: 144rem;


	overflow: hidden;

	&-about,
	&-skills,
	&-footer {
		padding: 7rem 0;

		// background: yellow;
	}


	&-margin {

		height: auto;
		width: 100%;
		max-width: 85%;
		margin: auto;

		@include abs.fns-respond(mlaptop) {
			max-width: 90%;
		}

		// background: orange;
	}


	&-title {
		padding: 3vh 0;
		margin-bottom: 3rem;

		// background: green;
	}
	&-title > * {
		font-family: heading;
		text-transform: uppercase;
		letter-spacing: -.2rem;
		color: rgba(abs.$vars-c-black,.8);
	}
}


.row {
	height: auto;
	width: auto;

	display: flex;
	justify-content: space-between;
	flex-wrap: wrap;

	// background: green;
}
.col {
	flex: 1 1 auto;
	max-width: 45%;
	padding-right: 2%;
	
	// background: crimson;


	@include abs.fns-respond(mptab) {
		min-width: 100%;
		padding: 0;
	}
}

.category {
	margin-bottom: 6rem;

	// background: blue;

	&:last-child {
		// margin-bottom: 0;
	}

	&-title {
		text-transform: uppercase;
		font-family: tthin;
		letter-spacing: .3rem;
		color: abs.$vars-c-darkblue;


		margin-bottom: 1.5rem;
	}

	&-list {

		& li {
			display: flex;
			align-items: center;
		}
		& li p span {
			// white-space: unset;
		}
	}
}

</style>
