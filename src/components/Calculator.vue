<script setup>
import { ref } from 'vue'

const gotPoints = ref('')
const maxPoints = ref('')

let percentage
let grade

function getPercentage() {
	if (!gotPoints.value || !maxPoints.value) {
		percentage = 'Uzupełnij oba pola...'
		return percentage
	} else if (gotPoints.value > maxPoints.value) {
		percentage = 'Maksymalne punkty muszą być większe od zdobytych...'
		return percentage
	} else {
		percentage = gotPoints.value / maxPoints.value * 100
		return `${percentage.toFixed(2)} %`
	}
}

function getGrade() {
	if (!gotPoints.value || !maxPoints.value) {
		grade = 'Uzupełnij oba pola...'
		return grade
	} else if (gotPoints.value > maxPoints.value) {
		grade = 'Maksymalne punkty muszą być większe od zdobytych...'
		return grade
	} else if (percentage >= 99) {
		grade = '6'
		return grade
	} else if (percentage >= 95) {
		grade = '5'
		return grade
	} else if (percentage >= 90) {
		grade = '5 -'
		return grade
	} else if (percentage >= 85) {
		grade = '4 +'
		return grade
	} else if (percentage >= 80) {
		grade = '4'
		return grade
	} else if (percentage >= 75) {
		grade = '4 -'
		return grade
	} else if (percentage >= 70) {
		grade = '3 +'
		return grade
	} else if (percentage >= 60) {
		grade = '3'
		return grade
	} else if (percentage >= 50) {
		grade = '3 -'
		return grade
	} else if (percentage >= 47) {
		grade = '2 +'
		return grade
	} else if (percentage >= 44) {
		grade = '2'
		return grade
	} else if (percentage >= 40) {
		grade = '2 -'
		return grade
	} else {
		grade = '1'
		return grade
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
				<p>{{ getGrade() }}</p>
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