<script>
	export let segment;

	import { stores } from "@sapper/app";
	const { session } = stores();
</script>

<!-- This example requires Tailwind CSS v2.0+ -->
<nav class="bg-gray-800">
	<div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
		<div class="relative flex items-center justify-between h-16">
			<div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
				<!-- Mobile menu button-->
				<button
					type="button"
					class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700"
					aria-controls="mobile-menu"
					aria-expanded="false"
				>
					<span class="sr-only">Open main menu</span>
					<!--
				Icon when menu is closed.
	
				Heroicon name: outline/menu
	
				Menu open: "hidden", Menu closed: "block"
			  -->
					<svg
						class="block h-6 w-6"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/>
					</svg>
					<!--
				Icon when menu is open.
	
				Heroicon name: outline/x
	
				Menu open: "block", Menu closed: "hidden"
			  -->
					<svg
						class="hidden h-6 w-6"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					</svg>
				</button>
			</div>
			<div
				class="flex-1 flex items-center justify-center sm:items-stretch sm:justify-start"
			>
				<div class="flex-shrink-0 flex items-center">
					<img
						class="block lg:hidden h-8 w-auto"
						src="https://cdn.discordapp.com/attachments/897728408811888652/916266201167052800/logo.png"
						alt="Workflow"
					/>
					<img
						class="hidden lg:block h-8 w-auto"
						src="https://cdn.discordapp.com/attachments/897728408811888652/916266201167052800/logo.png"
						alt="Workflow"
					/>
				</div>
				<div class="hidden sm:block sm:ml-6">
					<div class="flex space-x-4">
						<!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
						<a
							class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium  active:bg-gray-900"
							aria-current={segment === "home"
								? "page"
								: undefined}
							href=".">Home</a
						>

						<a
							class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium active:bg-gray-900"
							aria-current={segment === "dashboard"
								? "page"
								: undefined}
							href="dashboard">Dashboard</a
						>

						<a
							class="text-gray-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium active:bg-gray-900"
							aria-current={segment === "about"
								? "page"
								: undefined}
							href="about">About</a
						>
						{#if $session.isAuthenticated}
							<a href="/logout"
								class="text-red-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium" 
							>Logout</a>
						{:else}
							<a href="/login"
								class="text-green-300 hover:bg-gray-700 hover:text-white px-3 py-2 rounded-md text-sm font-medium" 
							>Login</a>
						{/if}
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Mobile menu, show/hide based on menu state. -->
	<div class="sm:hidden" id="mobile-menu">
		<div class="px-2 pt-2 pb-3 space-y-1">
			<!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
			<a
				class="bg-gray-900 text-white block px-3 py-2 rounded-md text-base font-medium"
				aria-current={segment === undefined ? "page" : undefined}
				href=".">Heim</a
			>
			<a
				class="text-gray-300 hover:bg-gray-700 hover:text-white block px-3 py-2 rounded-md text-base font-medium"
				aria-current={segment === "dashboard" ? "page" : undefined}
				href="dashboard">Dashboard</a
			>
			<a
				class="text-gray-300 hover:bg-gray-700 hover:text-white block px-3 py-2 rounded-md text-base font-medium"
				aria-current={segment === "about" ? "page" : undefined}
				href="about">Über</a
			>
		</div>
	</div>
</nav>
