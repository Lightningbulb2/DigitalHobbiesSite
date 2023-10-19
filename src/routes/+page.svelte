<script>
	import {Card, CardBody, CardFooter, CardHeader, CardTitle} from 'sveltestrap';
	import Logo from "../lib/assets/LightningbulbLogo.png"
</script>

<svelte:head>
	<title>Digital Hobbies</title>
	<meta name="description" content="Digital Hobbies" />
</svelte:head>

<div class="d-flex justify-content-center p-5">
	<h1 class="test">HIHIHI</h1>

	<Card class="w-25 shadow-lg bg-myown">
		<CardHeader>
			<CardTitle class="text-center text-light">Welcome to Digital Hobbies</CardTitle>
		</CardHeader>
		<CardBody>
			<img src={Logo} class="w-100 rounded-2" alt="Lightningbulb Logo">
		</CardBody>
		<CardFooter class="text-center text-light">
			A Lightningbulb website.
		</CardFooter>
	</Card>

</div>
