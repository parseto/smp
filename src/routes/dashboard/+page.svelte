<script>
	import { onMount } from "svelte";
	import Chart from "chart.js/auto";
	import Sidebar from "$lib/components/hdsteel/Sidebar.svelte";
	import Tabs from "$lib/components/hdsteel/Tabs.svelte";
	import ContentPanel from "$lib/components/hdsteel/ContentPanel.svelte";
	import Footer from "$lib/components/hdsteel/Footer.svelte";
	import Badge from "$lib/components/hdsteel/Badge.svelte";

	let chart1, chart2, chart3;

	onMount(() => {
		const ctx1 = document.getElementById("chart1").getContext("2d");
		document.getElementById("chart1").height = 260; // 캔버스 높이를 설정

		chart1 = new Chart(ctx1, {
			type: "line",
			data: {
				labels: ["6.10", "6.10", "6.15", "6.20", "6.25", "6.30", "6.35"],
				datasets: [
					{
						label: "일관생산",
						data: [35, 50, 15, 70, -10, 40, 50],
						borderColor: "#42a5f5",
						fill: false,
						pointStyle: "circle",
						pointRadius: 5,
						pointHoverRadius: 7,
						pointBorderColor: "#42a5f5",
						pointBackgroundColor: "#ffffff", // 빈 원을 만들기 위한 설정
						pointBorderWidth: 2, // 원의 테두리 두께
					},
					{
						label: "철강생산",
						data: [100, 30, 60, 50, 10, 0, 100],
						borderColor: "#0c3274",
						fill: false,
						pointStyle: "circle",
						pointRadius: 5,
						pointHoverRadius: 7,
						pointBorderColor: "#0c3274",
						pointBackgroundColor: "#ffffff", // 빈 원을 만들기 위한 설정
						pointBorderWidth: 2, // 원의 테두리 두께
					},
				],
			},
			options: {
				plugins: {
					legend: {
						position: "bottom", // 레이블을 아래로 배치
						labels: {
							usePointStyle: true, // 레이블 모양을 데이터셋의 pointStyle로 변경
							padding: 20, // 레이블과 그래프 사이의 간격 설정
						},
					},
				},
			},
		});

		const ctx2 = document.getElementById("chart2").getContext("2d");

		chart2 = new Chart(ctx2, {
			type: "doughnut",
			data: {
				labels: ["통계", "연주", "진행", "품질"],
				datasets: [
					{
						data: [60, 20, 10, 10],
						backgroundColor: ["#0E3271", "#0D68F8", "#4190F9", "#9BC4FB"],
					},
				],
			},
			options: {
				plugins: {
					legend: {
						position: "bottom", // 레이블을 아래로 배치
						labels: {
							usePointStyle: true, // 레이블 앞에 원형을 표시
							padding: 20, // 레이블과 차트 사이의 간격을 조정
						},
					},
				},
			},
		});

		const ctx3 = document.getElementById("chart3").getContext("2d");
		document.getElementById("chart3").height = 220; // 캔버스 높이를 설정

		chart3 = new Chart(ctx3, {
			type: "bar",
			data: {
				labels: ["8/1", "8/2", "8/3", "8/4", "8/5", "8/6", "8/7"],
				datasets: [
					{
						label: "완료",
						data: [15, 11, 9, 8, 6, 6, 6],
						backgroundColor: function (context) {
							// 앞의 3개 막대는 파란색으로만 표시
							const index = context.dataIndex;
							return index < 3 ? "#0E3271" : "#0E3271";
						},
						stack: "Stack 0",
					},
					{
						label: "진행",
						data: [0, 0, 0, 4, 7, 2, 2],
						backgroundColor: "#0D68F8",
						stack: "Stack 0",
					},
					{
						label: "대기",
						data: [0, 0, 0, 4, 5, 7, 7],
						backgroundColor: "#9BC4FB",
						stack: "Stack 0",
					},
				],
			},
			options: {
				plugins: {
					legend: {
						display: false, // label을 숨김
					},
				},
				scales: {
					x: {
						stacked: true, // x축에 스택 적용
					},
					y: {
						stacked: true, // y축에 스택 적용
					},
				},
			},
		});

		// Doughnut Chart1
		const ctxDoughnut1 = document.getElementById("doughnutChart1").getContext("2d");
		document.getElementById("doughnutChart1").width = 140; // 캔버스 넓이 설정

		new Chart(ctxDoughnut1, {
			type: "doughnut",
			data: {
				labels: ["Normal", "Alarm", "Error"],
				datasets: [
					{
						data: [75, 0, 25],
						backgroundColor: ["#22c55e", "#ddd", "#ddd"],
					},
				],
			},
			options: {
				plugins: {
					legend: {
						display: false, // 레이블을 숨김
					},
				},
				cutout: "80%", // 가운데 부분을 비워둠
			},
		});

		// Doughnut Chart2
		const ctxDoughnut2 = document.getElementById("doughnutChart2").getContext("2d");
		document.getElementById("doughnutChart2").width = 140; // 캔버스 넓이 설정

		new Chart(ctxDoughnut2, {
			type: "doughnut",
			data: {
				labels: ["Normal", "Alarm", "Error"],
				datasets: [
					{
						data: [15, 0, 85],
						backgroundColor: ["#facc15", "#ddd", "#ddd"],
					},
				],
			},
			options: {
				plugins: {
					legend: {
						display: false, // 레이블을 숨김
					},
				},
				cutout: "80%", // 가운데 부분을 비워둠
			},
		});

		// Doughnut Chart3
		const ctxDoughnut3 = document.getElementById("doughnutChart3").getContext("2d");
		document.getElementById("doughnutChart3").width = 140; // 캔버스 넓이 설정

		new Chart(ctxDoughnut3, {
			type: "doughnut",
			data: {
				labels: ["Normal", "Alarm", "Error"],
				datasets: [
					{
						data: [25, 0, 75],
						backgroundColor: ["#ef4444", "#ddd", "#ddd"],
					},
				],
			},
			options: {
				plugins: {
					legend: {
						display: false, // 레이블을 숨김
					},
				},
				cutout: "80%", // 가운데 부분을 비워둠
			},
		});

		function generateRandomArray() {
			const result = []; // 결과를 담을 배열
			for (let i = 0; i < 100; i++) {
				// -10에서 20 사이의 랜덤한 숫자 생성
				const randomValue = Math.floor(Math.random() * 31) - 10;
				result.push(randomValue); // 생성된 숫자를 배열에 추가
			}
			return result; // 결과 배열 반환
		}

		function generateTimeLabels() {
			const result = []; // 결과를 담을 배열
			let hours = 6;
			let minutes = 0;

			for (let i = 0; i < 100; i++) {
				// 현재 시간을 "HH:MM" 형식의 문자열로 저장
				const timeLabel = `${hours.toString().padStart(2, "0")}:${minutes.toString().padStart(2, "0")}`;
				result.push(timeLabel); // 결과 배열에 추가

				// 10분 증가
				minutes += 10;
				if (minutes >= 60) {
					minutes = 0;
					hours += 1;
				}
			}
			return result; // 결과 배열 반환
		}

		// Line Chart
		const ctxLine = document.getElementById("lineChart").getContext("2d");
		new Chart(ctxLine, {
			type: "line",
			data: {
				labels: generateTimeLabels(),
				datasets: [
					{
						label: "로그 이슈 현황",
						data: generateRandomArray(),
						borderColor: "red",
						backgroundColor: "#0ea5e9",
						fill: false,
						tension: 0.1,
					},
				],
			},
			options: {
				plugins: {
					legend: {
						position: "bottom",
						display: false, // label을 숨김
					},
				},
				elements: {
					point: {
						radius: 0, // 포인트를 숨김
					},
				},
				scales: {
					x: {
						ticks: {
							autoSkip: false, // 자동으로 라벨 생략 비활성화
							callback: function (value, index, ticks) {
								// 첫 번째와 마지막 값만 반환
								if (index === 0 || index === ticks.length - 1) {
									return this.getLabelForValue(value);
								}
								return ""; // 중간 값은 비워둠
							},
						},
						grid: {
							drawBorder: false,
							display: false, // x축의 라인을 숨김
						},
					},
					y: {
						beginAtZero: true,
						ticks: {
							callback: function (value, index, ticks) {
								// 첫 번째와 마지막 값만 반환
								return index === 0 || index === ticks.length - 1 ? value : "";
							},
						},
						grid: {
							drawBorder: false,
							display: true, // y축의 라인을 유지
						},
					},
				},
			},
		});

		// Stacked Bar Chart
		const ctxStackedBar = document.getElementById("stackedBarChart").getContext("2d");
		document.getElementById("stackedBarChart").width = 120; // 캔버스 넓이 설정
		document.getElementById("stackedBarChart").height = 350; // 캔버스 높이 설정

		new Chart(ctxStackedBar, {
			type: "bar",
			data: {
				labels: [""],
				datasets: [
					{
						label: "완료",
						data: [20],
						backgroundColor: "#0E3271",
						stack: "Stack 0",
						barThickness: 30, // 막대의 폭을 30px로 설정
					},
					{
						label: "진행",
						data: [30],
						backgroundColor: "#0D68F8",
						stack: "Stack 0",
						barThickness: 30, // 막대의 폭을 30px로 설정
					},
					{
						label: "대기",
						data: [50],
						backgroundColor: "#9BC4FB",
						stack: "Stack 0",
						barThickness: 30, // 막대의 폭을 30px로 설정
					},
				],
			},
			options: {
				plugins: {
					legend: {
						display: false, // 레이블 숨김
					},
				},
				scales: {
					x: {
						stacked: true, // x축 스택 적용
						display: false, // x축 숨김
					},
					y: {
						stacked: true, // y축 스택 적용
						ticks: {
							stepSize: 20, // y축 간격을 20 단위로 설정
							callback: function (value) {
								return value + "%"; // 레이블에 % 기호 추가
							},
						},
						beginAtZero: true, // y축을 0에서 시작
					},
				},
				maintainAspectRatio: false, // 크기 비율 유지하지 않음
			},
		});
	});
</script>

<div class="flex h-screen bg-gray-100 hds">
	<!-- Sidebar -->
	<Sidebar />

	<!-- Main Content -->
	<div class="flex-1 p-8 px-10">
		<header class="flex justify-between items-center mb-8">
			<h2 class="text-4xl font-semibold text-blue-900">Dashboard</h2>
			<div class="flex items-center gap-4">
				<div class="fcc gap-2 mr-10">Home <img src="/hdsteel/ic-breadscrumb-arrow.svg" alt="breadscrumb arrow" /> Dashboard</div>
				<div class="relative">
					<input type="text" placeholder="검색어를 입력하세요" class="w-100 p-3 pl-12 mr-4 border-1 border-gray-300 rounded-lg" />
					<img src="/hdsteel/lnb-search.svg" alt="search" class="absolute left-3 top-3" />
				</div>
				<button type="button" class="p-3 bg-white border-1 border-gray-300 rounded-lg">
					<img src="/hdsteel/ic-gnb-alram.svg" alt="gnb alarm" class="" />
				</button>
				<button type="button" class="p-3 bg-blue-900 rounded-lg">
					<img src="/hdsteel/ic-gnb-user.svg" alt="gnb user" class="" />
				</button>
			</div>
		</header>

		<Tabs />

		<!-- Dashboard Grid -->
		<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
			<!-- 첫 번째 카드 -->
			<ContentPanel title={"일관생산 - 판재"}>
				<div class="text-sm">
					<div class="text-gray-500">지표별 현황</div>
					<div class="fcc justify-between py-2 border-b-1">
						<div class="fcc flex-col p-3 mb-4 gap-4 pr-10 border-r-1">
							<Badge text={"발생"} />
							<div>
								<span class="text-3xl font-bold text-gray-900 underline">10</span>
								<span class="text-sm">건</span>
							</div>
						</div>
						<div class="fcc flex-col p-3 mb-4 gap-4">
							<Badge text={"완료"} isOutline />
							<div>
								<span class="text-3xl font-bold text-gray-900 underline">5</span>
								<span class="text-sm">건</span>
							</div>
						</div>
						<div class="fcc flex-col p-3 mb-4 gap-4">
							<Badge text={"진행"} isOutline colorStrong="700" />
							<div>
								<span class="text-3xl font-bold text-gray-900 underline">3</span>
								<span class="text-sm">건</span>
							</div>
						</div>
						<div class="fcc flex-col p-3 mb-4 gap-4">
							<Badge text={"대기"} isOutline colorStrong="500" />
							<div>
								<span class="text-3xl font-bold text-gray-900 underline">2</span>
								<span class="text-sm">건</span>
							</div>
						</div>
					</div>
				</div>
				<div class="mt-6">
					<div class="flex justify-between text-sm text-gray-500">
						<div>이슈 처리 현황</div>
						<div>최종점검시간 : 2024-08-18 13:20</div>
					</div>
					<div class="fcc w-full text-white text-sm my-5">
						<div class="w-1/2 bg-green-500 fcc">50%</div>
						<div class="w-1/5 bg-yellow-500 fcc">20%</div>
						<div class="w-3/10 bg-red-500 fcc">30%</div>
					</div>
					<div class="fcc gap-4">
						<div>
							<span class="w-2 h-2 bg-green-500 rounded-full inline-block mr-1"></span>
							<span class="text-sm">정상</span>
						</div>
						<div>
							<span class="w-2 h-2 bg-yellow-500 rounded-full inline-block mr-1"></span>
							<span class="text-sm">알람</span>
						</div>
						<div>
							<span class="w-2 h-2 bg-red-500 rounded-full inline-block mr-1"></span>
							<span class="text-sm">이상</span>
						</div>
					</div>
				</div>
			</ContentPanel>

			<!-- 두 번째 카드 (그래프) -->
			<ContentPanel title={"지표 인터페이스 추이"}>
				<div>
					<canvas id="chart1"></canvas>
				</div>
			</ContentPanel>

			<!-- 세 번째 카드 (도넛 차트) -->
			<ContentPanel title={"업무별 Issue 발생 현황"}>
				<div>
					<div class="fcc pl-20">
						<canvas id="chart2"></canvas>
						<div class="fcc flex-col gap-5">
							<div class="flex items-center w-50">
								<span class="w-2 h-2 bg-blue-900 rounded-full inline-block mr-1"></span>
								<span class="text-3xl font-bold text-gray-900 ml-2 mr-1">164</span>
								건
							</div>
							<div class="flex items-center w-50">
								<span class="w-2 h-2 bg-blue-700 rounded-full inline-block mr-1"></span>
								<span class="text-3xl font-bold text-gray-900 ml-2 mr-1">15</span>
								건
							</div>
							<div class="flex items-center w-50">
								<span class="w-2 h-2 bg-blue-500 rounded-full inline-block mr-1"></span>
								<span class="text-3xl font-bold text-gray-900 ml-2 mr-1">8</span>
								건
							</div>
						</div>
					</div>
					<div class="fcc gap-4 mt-5">
						<div>
							<span class="w-2 h-2 bg-blue-900 rounded-full inline-block mr-1"></span>
							<span class="text-sm">완료</span>
						</div>
						<div>
							<span class="w-2 h-2 bg-blue-700 rounded-full inline-block mr-1"></span>
							<span class="text-sm">진행</span>
						</div>
						<div>
							<span class="w-2 h-2 bg-blue-500 rounded-full inline-block mr-1"></span>
							<span class="text-sm">대기</span>
						</div>
					</div>
				</div>
			</ContentPanel>

			<!-- 네 번째 카드 (막대 차트) -->
			<ContentPanel title={"일자별 Issue 처리 현황"}>
				<div>
					<canvas id="chart3"></canvas>
					<div class="fcc gap-4 mt-5">
						<div>
							<span class="w-2 h-2 bg-blue-900 rounded-full inline-block mr-1"></span>
							<span class="text-sm">완료</span>
						</div>
						<div>
							<span class="w-2 h-2 bg-blue-700 rounded-full inline-block mr-1"></span>
							<span class="text-sm">진행</span>
						</div>
						<div>
							<span class="w-2 h-2 bg-blue-500 rounded-full inline-block mr-1"></span>
							<span class="text-sm">대기</span>
						</div>
					</div>
				</div>
			</ContentPanel>
		</div>

		<!-- 시스템 종합 및 Issue 처리 현황 -->
		<div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-4">
			<!-- 시스템 종합 -->
			<ContentPanel title={"시스템 종합"}>
				<div class="fcc">
					<div>
						<div class="fcc justify-start mb-3 text-gray-500 text-sm">지표별 현황</div>
						<div class="fcc gap-5">
							<!-- Doughnut Chart -->
							<div class="relative">
								<canvas id="doughnutChart1" width="150"></canvas>
								<div class="absolute inset-0 flex items-center justify-center">
									<div class="text-center pt-2">
										<div class="text-3xl text-black font-bold">75%</div>
										<div class="text-sm text-gray-500">Normal</div>
									</div>
								</div>
							</div>
							<!-- Doughnut Chart -->
							<div class="relative">
								<canvas id="doughnutChart2" width="150"></canvas>
								<div class="absolute inset-0 flex items-center justify-center">
									<div class="text-center pt-2">
										<div class="text-3xl text-black font-bold">15%</div>
										<div class="text-sm text-gray-500">Alarm</div>
									</div>
								</div>
							</div>
							<!-- Doughnut Chart -->
							<div class="relative">
								<canvas id="doughnutChart3" width="150"></canvas>
								<div class="absolute inset-0 flex items-center justify-center">
									<div class="text-center pt-2">
										<div class="text-3xl text-black font-bold">25%</div>
										<div class="text-sm text-gray-500">Error</div>
									</div>
								</div>
							</div>
						</div>
						<div class="fcc gap-4">
							<div>
								<span class="w-2 h-2 bg-green-500 rounded-full inline-block mr-1"></span>
								<span class="text-sm">정상</span>
							</div>
							<div>
								<span class="w-2 h-2 bg-yellow-500 rounded-full inline-block mr-1"></span>
								<span class="text-sm">알람</span>
							</div>
							<div>
								<span class="w-2 h-2 bg-red-500 rounded-full inline-block mr-1"></span>
								<span class="text-sm">이상</span>
							</div>
						</div>
						<!-- Line Chart -->
						<div>
							<div class="fcc justify-start mb-3 text-gray-500 text-sm">로그 이슈 현황</div>
							<canvas id="lineChart"></canvas>
						</div>
					</div>
					<!-- Stack Bar Chart -->
					<div>
						<div class="fcc mb-3 text-gray-500 text-sm">이슈 처리 현황</div>
						<div class="px-10">
							<canvas id="stackedBarChart"></canvas>
						</div>
						<div class="fcc gap-4 mt-5">
							<div>
								<span class="w-2 h-2 bg-blue-900 rounded-full inline-block mr-1"></span>
								<span class="text-sm">완료</span>
							</div>
							<div>
								<span class="w-2 h-2 bg-blue-700 rounded-full inline-block mr-1"></span>
								<span class="text-sm">진행</span>
							</div>
							<div>
								<span class="w-2 h-2 bg-blue-500 rounded-full inline-block mr-1"></span>
								<span class="text-sm">대기</span>
							</div>
						</div>
					</div>
				</div>
			</ContentPanel>

			<!-- Issue 처리 현황 -->
			<ContentPanel title={"Issue 처리 현황"}>
				<div class="flex justify-end py-2 mb-2">
					<button type="button" class="border-1 px-3 py-1">연간</button>
					<button type="button" class="border-1 px-3 py-1">월간</button>
					<button type="button" class="border-1 px-3 py-1 border-2 border-blue-900">주간</button>
				</div>
				<table class="table-auto w-full text-left">
					<thead>
						<tr class="text-gray-400 font-thin">
							<th class="px-4 py-2">Issue ID</th>
							<th class="px-4 py-2">Issue 명</th>
							<th class="px-4 py-2">상세설명</th>
							<th class="px-4 py-2">담당자</th>
							<th class="px-4 py-2">진행상태</th>
						</tr>
					</thead>
					<tbody>
						<tr class="border-t-1">
							<td class="px-4 py-2">IS24060001</td>
							<td class="px-4 py-2">주문 오류</td>
							<td class="px-4 py-2">냉연 밀배분 오류 주문</td>
							<td class="px-4 py-2">황정연</td>
							<td class="">
								<Badge text={"대기"} isOutline colorStrong="300" />
							</td>
						</tr>
						<tr class="border-t-1">
							<td class="px-4 py-2">IS24060001</td>
							<td class="px-4 py-2">주문 오류</td>
							<td class="px-4 py-2">냉연 밀배분 오류 주문</td>
							<td class="px-4 py-2">황정연</td>
							<td class="">
								<Badge text={"대기"} isOutline colorStrong="300" />
							</td>
						</tr>
						<tr class="border-t-1">
							<td class="px-4 py-2">IS24060001</td>
							<td class="px-4 py-2">주문 오류</td>
							<td class="px-4 py-2">냉연 밀배분 오류 주문</td>
							<td class="px-4 py-2">황정연</td>
							<td class="">
								<Badge text={"진행"} isOutline colorStrong="500" />
							</td>
						</tr>
						<tr class="border-t-1">
							<td class="px-4 py-2">IS24060001</td>
							<td class="px-4 py-2">주문 오류</td>
							<td class="px-4 py-2">냉연 밀배분 오류 주문</td>
							<td class="px-4 py-2">황정연</td>
							<td class="text-center">
								<Badge text={"진행"} isOutline colorStrong="500" />
							</td>
						</tr>
						<tr class="border-t-1">
							<td class="px-4 py-2">IS24060001</td>
							<td class="px-4 py-2">주문 오류</td>
							<td class="px-4 py-2">냉연 밀배분 오류 주문</td>
							<td class="px-4 py-2">황정연</td>
							<td>
								<Badge text={"완료"} isOutline colorStrong="700" />
							</td>
						</tr>
					</tbody>
				</table>
			</ContentPanel>
		</div>
		<Footer />
	</div>
</div>
