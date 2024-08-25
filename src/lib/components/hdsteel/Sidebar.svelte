<script>
	let isDashboardOpen = false; // Dashboard 메뉴가 열려 있는지 상태를 저장합니다.
	let isLnbOpen = true; // LNB 패널이 열려 있는지 상태를 저장합니다.

	function toggleDashboard() {
		isDashboardOpen = !isDashboardOpen;
	}

	function toggleLnb() {
		isLnbOpen = !isLnbOpen;
	}
</script>

<!-- Sidebar -->
<aside
	class={`transition-all ${isLnbOpen ? "w-64" : "w-18.5"} bg-gray-900 text-gray-300 font-semibold hds border-r-4 border-r-blue-600 box-border`}
>
	<div>
		<div class="p-4">
			{#if isLnbOpen}
				<img src="/hdsteel/logo-white.svg" alt="HYUNDAI STEEL SMP Logo" class="mb-6" />
			{:else}
				<div class="fcc text-4xl mt-4 mb-8">S</div>
			{/if}
		</div>
		<div class="relative">
			<hr class="border-gray-500 {isLnbOpen ? '' : 'hidden'}" />
			<div class="absolute right-0 -top-6 pl-5 bg-gray-900">
				<button type="button" class="px-2 py-2 rounded-tl-lg rounded-bl-lg bg-gray-700" id="navigator" on:click={toggleLnb}>
					<img src="/hdsteel/ic-lnb-navigator.svg" alt="lnb navigator" />
				</button>
			</div>
		</div>
		<nav class="p-4">
			<div class={`text-gray-500 my-5 ${!isLnbOpen ? "hidden" : ""}`}>MENU</div>
			<ul class={isLnbOpen ? "" : "mt-16"}>
				<li class="mb-4">
					<a
						href="javascript:void(0);"
						on:click={toggleDashboard}
						class="relative flex items-center p-2 rounded {isLnbOpen ? '' : 'bg-gray-700'} hover:bg-gray-700"
					>
						<img src="/hdsteel/ic-menu-01.svg" alt="dashboard" />
						<span class={`ml-4 transition-opacity ${!isLnbOpen ? "opacity-0" : "opacity-100"}`}>Dashboard</span>
						<img
							src={isDashboardOpen ? "/hdsteel/ic-btn-dropdown.svg" : "/hdsteel/ic-btn-dropdown-arrow.svg"}
							alt="dashboard submenu"
							class="absolute right-0 {isLnbOpen ? '' : 'hidden'}"
						/>
					</a>
					{#if isDashboardOpen && isLnbOpen}
						<ul class="pl-8 mt-2">
							<li class="mb-2">
								<a href="/dashboard/system" class="flex items-center p-2">
									<span class="w-3 h-3 border-3 border-blue-600 bg-gray-900 rounded-full inline-block mr-2"></span> 시스템 Dashboard
								</a>
							</li>
							<li class="mb-2">
								<a href="/dashboard/plant" class="flex items-center p-2">
									<span class="w-2 h-2 bg-gray-300 rounded-full inline-block mr-4"></span> 공장 Dashboard
								</a>
							</li>
							<li class="mb-2">
								<a href="/dashboard/business" class="flex items-center p-2">
									<span class="w-2 h-2 bg-gray-300 rounded-full inline-block mr-4"></span> 업무별 Dashboard
								</a>
							</li>
							<li>
								<a href="/dashboard/user" class="flex items-center p-2">
									<span class="w-2 h-2 bg-gray-300 rounded-full inline-block mr-4"></span> 사용자 Dashboard
								</a>
							</li>
						</ul>
					{/if}
				</li>
				<li class="mb-4">
					<a href="/alarm" class="relative flex items-center p-2 rounded hover:bg-gray-700">
						<img src="/hdsteel/ic-menu-02.svg" alt="alarm" />
						<span class={`ml-4 transition-opacity ${!isLnbOpen ? "opacity-0" : "opacity-100"}`}>Alarm</span>
						<img src="/hdsteel/ic-btn-dropdown-arrow.svg" alt="alarm submenu" class="absolute right-0 {isLnbOpen ? '' : 'hidden'}" />
					</a>
				</li>
				<li class="mb-4">
					<a href="/issue" class="relative flex items-center p-2 rounded hover:bg-gray-700">
						<img src="/hdsteel/ic-menu-03.svg" alt="issue" />
						<span class={`ml-4 transition-opacity ${!isLnbOpen ? "opacity-0" : "opacity-100"}`}>Issue</span>
						<img src="/hdsteel/ic-btn-dropdown-arrow.svg" alt="issue submenu" class="absolute right-0 {isLnbOpen ? '' : 'hidden'}" />
					</a>
				</li>
				<li class="mb-4">
					<a href="/report" class="relative flex items-center p-2 rounded hover:bg-gray-700">
						<img src="/hdsteel/ic-menu-04.svg" alt="report" />
						<span class={`ml-4 transition-opacity ${!isLnbOpen ? "opacity-0" : "opacity-100"}`}>Report</span>
						<img src="/hdsteel/ic-btn-dropdown-arrow.svg" alt="report submenu" class="absolute right-0 {isLnbOpen ? '' : 'hidden'}" />
					</a>
				</li>
				<li class="mb-4">
					<a href="/setup" class="relative flex items-center p-2 rounded hover:bg-gray-700">
						<img src="/hdsteel/ic-menu-05.svg" alt="setup" />
						<span class={`ml-4 transition-opacity ${!isLnbOpen ? "opacity-0" : "opacity-100"}`}>Setup</span>
						<img src="/hdsteel/ic-btn-dropdown-arrow.svg" alt="setup submenu" class="absolute right-0 {isLnbOpen ? '' : 'hidden'}" />
					</a>
				</li>
				<li>
					<a href="/background" class="relative flex items-center p-2 rounded hover:bg-gray-700">
						<img src="/hdsteel/ic-menu-06.svg" alt="background" />
						<span class={`ml-4 transition-opacity ${!isLnbOpen ? "opacity-0" : "opacity-100"}`}>Background</span>
						<img src="/hdsteel/ic-btn-dropdown-arrow.svg" alt="background submenu" class="absolute right-0 {isLnbOpen ? '' : 'hidden'}" />
					</a>
				</li>
			</ul>
		</nav>
	</div>
</aside>
