<script setup>
import { ref } from 'vue'

const gotPoints = ref('')
const maxPoints = ref('')

let percentage
let grade

// I know that this is bad and not DRY at all...
function getPercentage() {
	if (!gotPoints.value || !maxPoints.value) {
		percentage = 'Uzupełnij oba pola...'
		return percentage
	} else if (gotPoints.value > maxPoints.value) {
		percentage = 'Maksymalne punkty muszą być większe od zdobytych...'
		return percentage
	} else {
		percentage = gotPoints.value / maxPoints.value * 100
		return `${percentage.toFixed(1)} %`
	}
}

function gradeFivePoints() {
	if (!gotPoints.value || !maxPoints.value) {
		grade = '...'
		return grade
	} else if (gotPoints.value > maxPoints.value) {
			grade = '...'
			return grade
		} else {
				grade = percentage / 10 * 0.5
				return grade.toFixed(1)
			}
}

function gradeTenPoints() {
	if (!gotPoints.value || !maxPoints.value) {
		grade = '...'
		return grade
	} else if (gotPoints.value > maxPoints.value) {
			grade = '...'
			return grade
		} else {
				grade = percentage / 10
				return grade.toFixed(1)
			}
	}

function gradeTwentyPoints() {
	if (!gotPoints.value || !maxPoints.value) {
		grade = '...'
		return grade
	} else if (gotPoints.value > maxPoints.value) {
			grade = '...'
			return grade
		} else {
				grade = percentage / 10 * 2
				return grade.toFixed(1)
			}
}

</script>

<template>
	<div class="calc-container">

		<h1>Kalkulator ocen</h1>

				<div class="box">
					<h3>Zdobyte punkty</h3>
					<input v-model.number="gotPoints" type="number" placeholder="Liczba zdobytych punktów">
				</div>

				<div class="box">
					<h3>Maksymalne punkty</h3>
					<input v-model.number="maxPoints" type="number" placeholder="Maksymalna liczba punktów">
				</div>

				<div class="box">
					<h3>Procentowo</h3>
					<p>{{ getPercentage() }}</p>
				</div>

				<div class="box">
					<h3>5 punktów</h3>
					<p>{{ gradeFivePoints() }}</p>
				</div>

				<div class="box">
					<h3>10 punktów</h3>
					<p>{{ gradeTenPoints() }}</p>
				</div>

				<div class="box">
					<h3>20 punktów</h3>
					<p>{{ gradeTwentyPoints() }}</p>
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