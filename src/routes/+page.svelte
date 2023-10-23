<script>
	import {Card, CardBody, CardFooter, CardHeader, CardTitle} from 'sveltestrap';
	import Logo from "../lib/assets/LightningbulbLogo.png"
	import { onMount } from "svelte";
	import { slide, fade } from 'svelte/transition';
	let showingCard = true;

	function toggleCard() {
		showingCard = !showingCard;
	}

	let y = 0;
	$: console.log(y);


	let thechosenone;
	onMount(() => {
		thechosenone = document.querySelector('#note');
		document.addEventListener('scroll', function () {

			if(isInViewport(thechosenone, true)) {showNote=true;
				thechosenone.style.visibility ="visible";}else {
				thechosenone.style.visibility ="hidden";
				showNote=false}



		}, {
			passive: true
		});
	});

	let showNote = false;

	const isInViewport = (el, partiallyVisible = false) => {
		const { top, left, bottom, right } = el.getBoundingClientRect();
		const { innerHeight, innerWidth } = window;
		return partiallyVisible
				? ((top > 0 && top < innerHeight) ||
						(bottom > 0 && bottom < innerHeight)) &&
				((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
				: top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth;
	};


/*
	function isInViewport(element) {
		console.log("checking viewport");
		const rect = element.getBoundingClientRect();
		console.log(rect.top >= 0 &&
				rect.left >= 0 &&
				rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
				rect.right <= (window.innerWidth || document.documentElement.clientWidth))
		return (
				rect.top >= 0 &&
				rect.left >= 0 &&
				rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
				rect.right <= (window.innerWidth || document.documentElement.clientWidth)
		);
	}

*/


</script>

<svelte:head>
	<title>Digital Hobbies</title>
	<meta name="description" content="Digital Hobbies" />
</svelte:head>
<svelte:window bind:scrollY={y}/>
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

	<div></div>

	<!--{#if y >= 120}-->
	<!--{#if showNote}-->

		<div transition:fade|local id="note"  class="align-self-center">
		<Card style="width: 60rem" class="shadow-lg bg-notquiteblack text-center text-light vh-100">
			<CardHeader>
				<CardTitle>A Note has appeared...</CardTitle>
			</CardHeader>
			<CardBody>
				Hi, I'm Levi or "Lightningbulb" as I go by online
			</CardBody>
		</Card>
		</div>
	<!--{/if}-->
</div>


