<script setup>

import { useHouseStore } from '@/stores/counter.js';
import HouseSimple from '@/components/HouseSimple.vue';
import NavigationDivision from "@/components/NavigationDivision.vue";
import HouseNewsList from '@/components/HouseNewsList.vue';

const houseStore = useHouseStore();

</script>

<template>

	<NavigationDivision/>

	<!-- 네비게이션 바 [ 전체, 아파트, 다세대 주택, 오피스텔 ] -->
	<div id="navigation-bar">
		<router-link :to="{ name: 'navi-all' }" class="nav-bt">전체</router-link>
		<router-link :to="{ name: 'navi-apt' }" class="nav-bt">아파트</router-link>
		<router-link :to="{ name: 'navi-villa' }" class="nav-bt">주택</router-link>
		<router-link :to="{ name: 'navi-officetel' }" class="nav-bt">오피스텔</router-link>
	</div>

	<NavigationDivision/>
	
	<!-- 주변 실거래가 정보 -->
	<div id="house-list">
		<div id="list-title">📌 주변 실거래가 정보</div>
		<template v-for="(house) in houseStore.getHouses" :key="house.id">
			<HouseSimple :house="house"/>
		</template>
	</div>

	<NavigationDivision/>

  <!-- 부동산 뉴스 -->
	<HouseNewsList/>

</template>

<style scoped>

#navigation-bar {
  width: 420px;
  height: 48px;

  display: flex;

  justify-content: space-around;
  /* 요소들을 수평으로 고르게 분배 */
  align-items: center;
  /* 요소들을 수직 가운데 정렬 */

}

#navigation-bar .nav-bt {
  /* border: 1px solid black; */
  /* UI 확인 */

  width: auto;
  height: 32px;

  text-align: center;
  line-height: 30px;

  font-size: 20px;
  font-weight: bold;

  color: #3A1D1D;
  text-decoration: none;
}

#list-title {
  margin-left: 24px;
  margin-top: 12px;
  margin-bottom: 12px;
  
  font-size: 20px;
  font-weight: bold;
}

#house-list {
  height: 360px;
  overflow-y: scroll;
}

#house-list::-webkit-scrollbar {
  width: 3px;
  /* display: none; */
}

#house-list::-webkit-scrollbar-thumb {
  background-color: #c9c9c9;
  border-radius: 10px;
}

#house-list::-webkit-scrollbar-track {
  background-color: #e0e0e0;
  border-radius: 10px;
  box-shadow: inset 0px 0px 5px white;
}

</style>