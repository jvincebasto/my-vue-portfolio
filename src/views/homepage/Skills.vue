<template>
	<section class="section section-skills" id="skills">
		<div class="section-margin">

			<hr>
			<div class="section-title">
				<h2>Skills</h2>
			</div>

			<div class="row">

				<div class="col col-left">

					<div class="category category-skills category-skills--left interpersonal">
						<h3 class="category-title">Interpersonal</h3>
						<ul class="category-list category-list--skills">
							<li>
								<span>Problem Solving</span>
								<div class="btn-radio btn-radio--4">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
							<li>
								<span>Time Management</span>
								<div class="btn-radio btn-radio--3">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
							<li>
								<span>Attention to<span class="text-darkblue"> Detail</span></span>
								<div class="btn-radio btn-radio--4">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
							<li>
								<span>Multi Tasking</span>
								<div class="btn-radio btn-radio--3">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
							<li>
								<span>Organized</span>
								<div class="btn-radio btn-radio--4">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
						</ul>
					</div>

					<div class="category category-skills category-skills--left technical-skills">
						<h3 class="category-title">Technical Skills</h3>
						<ul class="category-list category-list--skills">
							<li>
								<span>Microsoft Skills</span>
								<div class="btn-radio btn-radio--4">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
							<li>
								<span>Electronic Cicuitry</span>
								<div class="btn-radio btn-radio--3">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
							<li>
								<span>Web Development</span>
								<div class="btn-radio btn-radio--4">
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
									<div>&nbsp;</div>
								</div>
							</li>
						</ul>
					</div>
				</div>

				<div class="col col-right">
					<div class="category category-skills category-skills--right web-languages">
						<h3 class="category-title">Web Languages</h3>
						<ul class="category-list category-list--skills">
							<li>
								<span>CSS</span>
								<div class="progress-bar">
									<div class="progress-bar--css">&nbsp;</div>
									<span class="progress-bar--center-line">&nbsp;</span>
								</div>
							</li>
							<li>
								<span>JavaScript</span>
								<div class="progress-bar">
									<div class="progress-bar--js">&nbsp;</div>
									<span class="progress-bar--center-line">&nbsp;</span>
								</div>
							</li>
							<li>
								<span>PHP</span>
								<div class="progress-bar">
									<div class="progress-bar--php">&nbsp;</div>
									<span class="progress-bar--center-line">&nbsp;</span>
								</div>
							</li>
							<li>
								<span>SQL</span>
								<div class="progress-bar">
									<div class="progress-bar--sql">&nbsp;</div>
									<span class="progress-bar--center-line">&nbsp;</span>
								</div>
							</li>
							<li>
								<span>Laravel</span>
								<div class="progress-bar">
									<div class="progress-bar--laravel">&nbsp;</div>
									<span class="progress-bar--center-line">&nbsp;</span>
								</div>
							</li>
							<li>
								<span>Vue Js</span>
								<div class="progress-bar">
									<div class="progress-bar--vue">&nbsp;</div>
									<span class="progress-bar--center-line">&nbsp;</span>
								</div>
							</li>
						</ul>
					</div>
				</div>

			</div>
		</div>
	</section>
</template>

<script>

</script>

<style lang="scss">
@use "./../../sass/abstracts/abstracts" as abs;


.category {

	&-list {
		// background: green;
	}
	&-list--skills {

		& li {

			@include abs.fns-respond(mphone) {
				flex-wrap: wrap;
				margin-bottom: 1.5rem;
			}
		}
		& li > span {
			margin-right: auto;
			min-width: 50%;
		

			@include abs.fns-respond(mphone) {
				margin-right: unset;
				min-width: 100%;
				margin-bottom: .5rem;
			}
		}
		& li > * {

			// background: crimson;
		}
	}
}


.btn {

	&-radio {
		display: flex;

		// background: green;
	}

	&-radio div {
		height: 2.2rem;
		width: 2.2rem;

		border-radius: 10rem;
		border: .3rem solid abs.$vars-c-black;

		margin-right: .6rem;
		background: abs.$vars-c-lightblue;
	}
	&-radio div:last-child {
		margin-right: 0rem;
	}


	&-radio--4 div:last-of-type {
		background: transparent;
	}
	&-radio--3 div:nth-of-type(4),
	&-radio--3 div:last-of-type {
		background: transparent;
	}
}


.progress-bar {
	height: 2.2rem;
	width: 40rem;


	border-radius: 10rem;
	border: .3rem solid black;


	display: flex;
	align-items: center;
	overflow: hidden; 


	position: relative;


	& div {
		background-image: linear-gradient(to right, abs.$vars-c-lightblue, rgba(abs.$vars-c-lightblue,.8) 90%, rgba(abs.$vars-c-lightblue,0));
	}


	&--css {
		width: 80%;
	}
	&--js {
		width: 78%;
	}
	&--php { 
		width: 68%;
	}
	&--sql {
		width: 75%;
	}
	&--laravel {
		width: 65%;
	}
	&--vue {
		width: 75%;
	}


	&--center-line {
		width: 50%;
		position: absolute;
		top: 0;
		left: 0;

		border-right: .1rem dashed rgba(0,0,0,.8);

		// background: orange;
	}
}


</style>
