<template>
	<section class="section section-hero section-hero--height">
		<div class="section-margin">

			<div class="headline headline-block">
				
				<h1 class="headline-primary">
					<span class="headline-primary text-fade">I’m</span> John <br>
					<span class="headline-primary headline-primary--nickname text-lightblue">Vince</span>nt Basto
				</h1>
				<span class="headline-secondary text-fade">
					A Web Developer
				</span>
				
				<p>
					Hi there! How are you doing this time of pandemic,
					<span class="text-darkblue"> I hope you’re doing fine and well</span>. I’m a graduate of
					<span class="text-darkblue"> Computer Engineering</span>
					who likes
					<span class="text-darkblue"> Web Development</span>. What can I do for you? 
				</p>

				<div class="btn-group">
					<ul>
						<li>
							<a class="btn-headline btn-headline--primary" href="#about">
								About Me
							</a>
						</li>
						<li>
							<a class="btn-headline btn-headline--secondary" href="#contacts">
								Contact
							</a>
						</li>
					</ul>
				</div>
			</div>
		</div>


		<div class="section-bg section-hero--height">
			<div class="section-bg section-bg--color" id="bg_whiteboxes">&nbsp;</div>
			<div class="section-bg section-bg--gradient-left section-bg--gradient-left--1">&nbsp;</div>
			<div class="section-bg section-bg--gradient-left section-bg--gradient-left--2">&nbsp;</div>
		</div>


		<div class="profile section-hero--height">
			<img id="profile_picture" src="@/assets/imgs/profile.png" alt="profile-picture">
		</div>


		<div class="section-bg--overlay section-bg--overlay--1 
		section-hero--height">&nbsp;</div>
		<div class="section-bg--overlay section-bg--overlay--2">&nbsp;</div>
		<div class="section-bg--gradient-top section-hero--height">&nbsp;</div>
		<div class="section-bg--gradient-bottom section-hero--height">&nbsp;</div>
	</section>
</template>

<script>

</script>

<style scoped lang="scss">
@use "./../../sass/abstracts/abstracts" as abs;

.section {

	&-hero {
		width: 100%;
		padding: 14rem 0 7rem;
		display: flex;
		align-items: center;

		position: relative;
		// background: blue;

		&--height {
			height: 80rem;

			@include abs.fns-respond(sptab) {
				height: 130rem;
				padding-bottom: 14rem;
			}
			@include abs.fns-respond(lphone) {
				height: 120rem;
				padding-bottom: 10rem;
			}
		}

		& > * {
			display: flex;
			align-items: center;


			@include abs.fns-respond(sptab) {
				display: flex;
				align-items: flex-end;

				color: abs.$vars-c-white;
			}
		}
	}

	&-margin {
		height: 100%;
		position: relative;
		z-index: 100;

		@include abs.fns-respond(sptab) {
		}
	}
}


.headline {

	&-block {
		width: 100%;
	}
	
	&-primary {
		font-family: headline;
		text-transform: uppercase;
		color: abs.$vars-c-darkblue;
		
		// font-size: 7.8rem;
		font-size: 8.4rem;
		letter-spacing: -.5rem;
		line-height: 1;

		margin-bottom: .5rem;
		text-shadow: .2rem .2rem .2rem abs.$vars-c-black;

		@include abs.fns-respond(mptab) {
			font-size: 7.4rem;
		}
		@include abs.fns-respond(sptab) {
			color: abs.$vars-c-lightblue;
			font-size: 6.4rem;
		}		
		@include abs.fns-respond(cphone) {
			// text-shadow: none;
		}
		

		& > span.text-fade {
			font-size: inherit;
			margin-left: -.4rem;
			color: abs.$vars-c-black;
			opacity: .6;
	
			text-transform: capitalize;
			text-shadow: none;

			@include abs.fns-respond(sptab) {
				color: abs.$vars-c-white;
			}
		}

		&--nickname {
			margin-right: .8rem;
			text-shadow: inherit;

			@include abs.fns-respond(cphone) {
				margin-right: .1rem;
			}
		}
	}
	
	
	&-secondary {
		text-transform: uppercase;
		letter-spacing: .8rem;

		display: inline-block;
		margin-bottom: 3rem;

		@include abs.fns-respond(mptab) {
			letter-spacing: .6rem;
		}
		@include abs.fns-respond(sptab) {
			letter-spacing: .3rem;
			font-family: tthin;
		}
	}

	& > p {
		max-width: 45ch;

		margin-bottom: 3rem;

		@include abs.fns-respond(mptab) {
			max-width: 42ch;
		}
		@include abs.fns-respond(sptab) {
			max-width: 58ch;
			font-family: tthin;
		}
		@include abs.fns-respond(cphone) {
			max-width: 50ch;
			font-family: tthin;
		}
		@include abs.fns-respond(lphone) {
			max-width: 32ch;
			font-family: tthin;
		}
		@include abs.fns-respond(mphone) {
			font-family: tthin;
		}
		@include abs.fns-respond(sphone) {
			max-width: 25ch;
		}
	}
	& p span {
		text-transform: capitalize;

		@include abs.fns-respond(sptab) {
			color: abs.$vars-c-lightblue !important;
		}
	}
	& p span:first-child {
	} 
	& p span:nth-child(2) {
	} 
	& p span:last-child {
	} 
}

.btn {

	// &-group {
	// 	width: 100%;
	// }

	&-group ul {
		width: 100%;
		display: flex;
		
		// background: green;

		@include abs.fns-respond(lphone) {
			flex: 1 1 auto;
			width: 100%;
			flex-wrap: wrap;
		}
	}
	&-group ul li {

		@include abs.fns-respond(lphone) {
			width: 100%;

			display: flex;
			justify-content: center;
		}
	}

	&-headline {

		margin-right: 3rem;
		color: abs.$vars-c-darkblue;
		border-radius: 10rem;
		border: .2rem solid abs.$vars-c-darkblue;
		cursor: pointer;

		padding: .6rem 3rem;

		@include abs.fns-respond(sptab) {
			border-color: abs.$vars-c-lightblue;
			color: abs.$vars-c-lightblue;
		}
		@include abs.fns-respond(lphone) {
			margin-right: 0;

			display: block;
			width: 100%;
			text-align: center;

			margin-bottom: 1.5rem;
		}

		& > * {
			width: 100%;
		}

		&--primary {
			background: abs.$vars-c-darkblue;
			color: abs.$vars-c-white;
			font-family: tthin;

			filter: drop-shadow(0rem .2rem .2rem rgba(abs.$vars-c-black,.6));

			@include abs.fns-respond(sptab) {
				background: abs.$vars-c-lightblue;
				color: abs.$vars-c-darkblue;
				font-family: tbody;
			}
		}
		&--secondary {

		}
	}
}


.section-bg {
	width: 100%;
	max-width: 50%;

	position: absolute;
	top: 0;
	right: 0;
	z-index: -10;

	& * {
		max-width: unset;
	}


	@include abs.fns-respond(sptab) {
		max-width: unset;
		// display: none;
		// filter: blur(.1rem);s
	}

	&--color {
		height: inherit;
		background: abs.$vars-c-darkblue; 
		

		@include abs.fns-respond(sptab) {
			background: rgba(abs.$vars-c-lightblue,.4); 
		}
	}
	&--gradient-left {

		&--1 {
			background: linear-gradient(to right, abs.$vars-c-white, transparent 60%);
		}
		&--2 {
			background: linear-gradient(to right, abs.$vars-c-white, transparent 30%);
		}

		height: inherit;
		right: unset;
		left: -.5rem;

		@include abs.fns-respond(sptab) {
			display: none;
		}
	}
	&--gradient-bottom {
		height: inherit;
		width: 100%;
		background: linear-gradient(to top, abs.$vars-c-white, rgba(abs.$vars-c-white,0) 5%, transparent 15%);

		position: absolute;
		top: 0;
		left: 0;
		z-index: 30;
	}
	&--gradient-top {
		height: inherit;
		width: 100%;
		background: linear-gradient(to bottom, rgba(abs.$vars-c-black,.6), transparent 6%);

		position: absolute;
		top: 0;
		left: 0;
		z-index: 10;

		display: none;

		@include abs.fns-respond(cphone) {
			display: unset;
		}
	}
	&--overlay {
		width: 100%;

		position: absolute;
		bottom: 0;
		left: 0;
		z-index: 20;

		// background: rgba(abs.$vars-c-black,.6);
		background: linear-gradient(to top, rgba(abs.$vars-c-black,.6), transparent);
		display: none;

		&--2 {
			background: linear-gradient(to top, rgba(abs.$vars-c-black,.4) 80%, transparent);
			height: 50%;
			// filter: blur(10rem);
		}

		@include abs.fns-respond(sptab) {
			display: unset;
		}	
	}
}


.profile {
	width: 100%;

	position: absolute;
	top: 0;
	right: 0;	
	z-index: 15;

	overflow: hidden;
}
#profile_picture {

	width: 88rem;
	position: absolute;
	top: -5%;
	right: -10%;

	filter: drop-shadow(1.5rem 1rem .5rem rgba(abs.$vars-c-black,.3));	

	@include abs.fns-respond(mlaptop) {
		right: -15%;
	}
	@include abs.fns-respond(slaptop) {
		right: -25%;
	}
	@include abs.fns-respond(mptab) {
		right: -32%;
	}
	@include abs.fns-respond(sptab) {
		width: 100rem;
		right: unset;
		left: 50%;
		transform: translateX(-40%);
	}	
	@include abs.fns-respond(cphone) {
		// filter: blur(2rem);
	}
	@include abs.fns-respond(lphone) {
		width: 85rem;
		transform: translateX(-45%);
	}
}
#bg_whiteboxes {
	height: 100%;
	width: 100%;

	background-image: url(./../../assets/imgs/bg-whitebox.png);
	background-size: cover;
	background-repeat: no-repeat;
}


</style>
