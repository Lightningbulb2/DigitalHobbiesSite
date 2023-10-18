
<script>
	import Logo from "../lib/assets/DigitialHobbiesLogo.png"
	import {
		Collapse,
		Navbar,
		NavbarToggler,
		NavbarBrand,
		Nav,
		NavItem,
		NavLink,
		Dropdown,
		DropdownToggle,
		DropdownMenu,
		DropdownItem
	} from 'sveltestrap';

	import { page } from '$app/stores';

	let activeClasses = "active bg-dark rounded-2";

	let isOpen = false;

	function handleUpdate(event) {
		isOpen = event.detail.isOpen;
	}
</script>

<header>

	<Navbar color="black" class="d-flex justify-content-md-center" dark expand="lg">


		<NavbarToggler on:click={() => (isOpen = !isOpen)} />
		<Collapse class="justify-content-md-center" {isOpen} navbar expand="lg" on:update={handleUpdate}>

			<NavbarBrand class="d-none d-lg-block p-1 bg-dark rounded-2" href="/"><img class="img-fluid" style="width: 3rem; height: auto;" src={Logo} alt="logo"></NavbarBrand>
			<Nav navbar>
				<NavItem>
					<NavLink href="/" class={$page.url.pathname === "/" ? activeClasses: ""}>Home</NavLink>
				</NavItem>
				<NavItem>
					<NavLink href="/videoProduction" class={$page.url.pathname === "/videoProduction" ? activeClasses: ""}>Video Production</NavLink>
				</NavItem>
				<NavItem>
					<NavLink href="/gaming" class={$page.url.pathname === "/gaming" ? activeClasses: ""}>Gaming</NavLink>
				</NavItem>
				<NavItem>
					<NavLink href="/programming" class={$page.url.pathname === "/programming" ? activeClasses: ""}>Programming</NavLink>
				</NavItem>
				<NavItem>
					<NavLink href="/music" class={$page.url.pathname === "/music" ? activeClasses: ""}>Music</NavLink>
				</NavItem>
				<NavItem>
					<NavLink href="/art" class={$page.url.pathname === "/art" ? activeClasses: ""}>Art</NavLink>
				</NavItem>
				<NavItem>
					<NavLink href="/productivity" class={$page.url.pathname === "/productivity" ? activeClasses: ""}>Productivity</NavLink>
				</NavItem>
				<!--
				<Dropdown nav inNavbar>
					<DropdownToggle nav caret>Options</DropdownToggle>
					<DropdownMenu end>
						<DropdownItem>Home</DropdownItem>
						<DropdownItem>Video Production</DropdownItem>
						<DropdownItem Gaming />
						<DropdownItem>Programming</DropdownItem>
						<DropdownItem>Music</DropdownItem>
						<DropdownItem>Art</DropdownItem>
						<DropdownItem>Productivity</DropdownItem>
					</DropdownMenu>
				</Dropdown>
				-->
			</Nav>
		</Collapse>
	</Navbar>




</header>

<style>

</style>