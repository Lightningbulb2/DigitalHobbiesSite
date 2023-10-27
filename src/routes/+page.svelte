<script>
	import {Card, CardBody, CardFooter, CardHeader, CardTitle} from 'sveltestrap';
	import Logo from "../lib/assets/LightningbulbLogo.png"
	import { onMount } from "svelte";
	import { slide, fade } from 'svelte/transition';
	let showingCard = true;

	function toggleCard() {
		showingCard = !showingCard;
	}


	let elems

	onMount(() => {
		elems = document.querySelectorAll('.fadeCard');
		let length = elems.length;


		document.addEventListener('scroll', function () {

			for (let index = 0; index < length; index++) {

				if (isInViewport(elems[index], true)) {
				elems[index].isVisible = true;
					console.log("element is visible");
				}else{
					elems[index].isVisible = false;
					console.log("element is invisible");
				}

			}


		}, {
			passive: true
		});
	});


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


	<Card style="width: 20rem" class="shadow-lg bg-notquiteblack text-center text-light align-self-center">
		<div style="height: 25rem" class=" shadow-lg bg-notequiteblack"
			 on:mouseenter={() => {toggleCard();}}
			 on:mouseleave={() => {toggleCard();}}>

		{#if showingCard}

			<div transition:slide|local>

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

		{/if}

		{#if !showingCard}

			<div transition:slide|local>

				<CardHeader>
					<CardTitle>Lightningbulb.png</CardTitle>
				</CardHeader>
				<CardBody>
					I made this image in photoshop,<br> March of 2020.
				</CardBody>

			</div>

		{/if}

		</div>
	</Card>


	<div style="font-size: 100px; text-shadow: 0px 5px 5px #000;" class="align-self-center m-5 p-5">
		Who am I?
	</div>
	<div style="font-size: 100px; text-shadow: 0px 5px 5px #000;" class="align-self-center m-5">
		What is this site?
	</div>


	<div class="fadeCard vh-100">
	{#if elems && elems[0].isVisible}
		<div transition:fade|local class="align-self-center">

		<Card style="width: 60rem" class="shadow-lg bg-notquiteblack text-center text-light vh-100">
			<CardHeader>
				<CardTitle>A Note has appeared...</CardTitle>
			</CardHeader>
			<CardBody>
				Hi, I'm Levi or "Lightningbulb" as I go by online
			</CardBody>
		</Card>

		</div>
		{/if}
	</div>




</div>


