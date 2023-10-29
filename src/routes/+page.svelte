<script>
	import {Card, CardBody, CardFooter, CardHeader, CardTitle} from 'sveltestrap';
	import Logo from "../lib/assets/LightningbulbLogo.png"
	import { onMount } from "svelte";

	let fadeElems;

	onMount(() => {
		fadeElems = document.querySelectorAll('.fadeCard');
		let length = fadeElems.length;


		document.addEventListener('scroll', function () {

			for (let index = 0; index < length; index++) {

				if (isInViewport(fadeElems[index], true)) {
					fadeElems[index].classList.add("isVisible");
					console.log("element is visible");
				}else{
					fadeElems[index].classList.remove("isVisible");
					console.log("element is not visible");
				}
			}
		}, {
			passive: true
		});

	});


	/*
	function isInViewport(element) {
		const rect = element.getBoundingClientRect();
		return (
				rect.top >= 0 &&
				rect.left >= 0 &&
				rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
				rect.right <= (window.innerWidth || document.documentElement.clientWidth)
		);
	}*/

	const isInViewport = (el, partiallyVisible = false) => {
		const { top, left, bottom, right } = el.getBoundingClientRect();
		const { innerHeight, innerWidth } = window;
		return partiallyVisible
				? ((top > 0 && top < innerHeight) ||
						(bottom > 0 && bottom < innerHeight)) &&
				((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
				: top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth;
	};

</script>


<svelte:head>
	<title>Digital Hobbies</title>
	<meta name="description" content="Digital Hobbies" />
</svelte:head>

<div class="d-flex flex-column justify-content-center p-5">


	<Card style="width: 25%" class="shadow-lg bg-notquiteblack text-center text-light align-self-center">

		<div class="slidingCard shadow-lg bg-notquiteblack text-center text-light align-self-center" style="height: 25rem; width: 100%;">


				<div class="slidingCardDefault">

					<CardHeader>
						<CardTitle>Welcome to Digital Hobbies</CardTitle>
					</CardHeader>
					<CardBody>
						<img src={Logo} class="w-100 rounded-2" alt="Lightningbulb Logo">
					</CardBody>
					<CardFooter>
						A Lightningbulb website.
					</CardFooter>

				</div>


				<div class="slidingCardHover">

					<CardHeader>
						<CardTitle>Lightningbulb.png</CardTitle>
					</CardHeader>
					<CardBody>
						I made this image in photoshop,<br> March of 2020.
					</CardBody>

				</div>


		</div>
	</Card>

	<div style="font-size: 100px; text-shadow: 0px 5px 5px #000;" class="align-self-center m-5 p-5">
		Who am I?
	</div>
	<div style="font-size: 100px; text-shadow: 0px 5px 5px #000;" class="align-self-center m-5">
		What is this site?
	</div>


	<div class="fadeCard vh-100">
		<Card style="width: 60rem" class="shadow-lg bg-notquiteblack m-auto text-center text-light vh-100">
			<CardHeader>
				<CardTitle>A Note has appeared...</CardTitle>
			</CardHeader>
			<CardBody>
				Hi, I'm Levi or "Lightningbulb" as I go by online
			</CardBody>
		</Card>

	</div>




</div>


<style>

	.slidingCard {
		position: relative;
		overflow: hidden
	}
	.slidingCardDefault {
		position: absolute;
		clip-path: inset(0);
		transition: clip-path 0.5s;
		width: 100%;
		height: 100%;
	}
	.slidingCardHover {
		position: absolute;
		transition: clip-path 0.5s, transform 0.5s;
		width: 100%;
		height: 100%;
		transform: translateY(100%);
	}

	.slidingCard:hover .slidingCardDefault {
		clip-path: inset(0% 0% 100% 0%);
	}
	.slidingCard:hover .slidingCardHover {
		transform: translateY(0);
	}

	.fadeCard {
		opacity: 0;
		transition: opacity 0.5s;
		transition-timing-function: linear;
	}

	:global(.isVisible) {
		opacity: 1 !important;
	}


</style>