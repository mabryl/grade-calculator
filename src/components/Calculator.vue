<script setup>
import { reactive, ref } from 'vue'

const percentageMessage = ref('Uzupełnij oba pola...')
const gradeMessage = ref('Uzupełnij oba pola...')

</script>

<template>
<div class="calc-container">

	<h1>Kalkulator ocen</h1>

		<div class="points-div">

			<div class="box">
				<h3>Zdobyte punkty</h3>
				<input :value="number" type="number" placeholder="Liczba zdobytych punktów">
			</div>

			<div class="box">
				<h3>Maksymalne punkty</h3>
				<input :value="number" type="number" placeholder="Maksymalna liczba punktów">
			</div>

		</div>

		<div class="grade-div">

			<div class="box">
				<h3>Procent zdobytych punktów</h3>
				<p>{{ percentageMessage }}</p>
			</div>

			<div class="box">
				<h3>Sugerowana ocena</h3>
				<p>{{ gradeMessage }}</p>
			</div>

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

.calc-container {
  flex: 1 0 auto;
}

.box {
	padding-bottom: 1em;
}
</style>