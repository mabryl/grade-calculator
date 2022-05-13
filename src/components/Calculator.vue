<script setup>
import { computed, ref } from 'vue'

const gotPoints = ref('')
const maxPoints = ref('')

function getPercentage() {
	let percentage
	if (!gotPoints.value || !maxPoints.value) {
		percentage = 'Uzupełnij oba pola'
		return percentage
	} else {
		percentage = gotPoints.value / maxPoints.value * 100
		return `${percentage.toFixed(2)} %`
	}
}

</script>

<template>
<div class="calc-container">

	<h1>Kalkulator ocen</h1>

			<div class="box">
				<h3>Zdobyte punkty</h3>
				<input v-model.number="gotPoints" placeholder="Liczba zdobytych punktów">
			</div>

			<div class="box">
				<h3>Maksymalne punkty</h3>
				<input v-model.number="maxPoints" placeholder="Maksymalna liczba punktów">
			</div>


			<div class="box">
				<h3>Procent zdobytych punktów</h3>
				<p>{{ getPercentage() }}</p>
			</div>

			<div class="box">
				<h3>Sugerowana ocena</h3>
				<p></p>
			</div>

</div>
</template>

<style>
input {
	padding: 1em 2em;
	min-width: 200px;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
	-webkit-appearance: none;
	margin: 0;
}

input[type=number] {
	-moz-appearance: textfield;
}

p {
	font-size: large;
}

.calc-container {
  flex: 1 0 auto;
}

.box {
	padding-bottom: 1em;
}
</style>