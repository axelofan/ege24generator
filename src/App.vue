<template>
	<p><span class='number'>24</span> <span v-html='task.txt'></span> Стажёр торопился и написал программу неправильно (ниже для Вашего удобства программа представлена на пяти языках программирования).</p>
		<table class='code' cellspacing="0">
	<tr>
		<td><p class='header'>Бейсик</p></td>
		<td><p class='header'>Python</p></td>
	</tr>
	<tr>
		<td v-html='replaceTab(task.bas)'></td>
		<td v-html='replaceTab(task.py)'></td>
	</tr>
	<tr>
		<td><p class='header'>Алгоритмический язык</p></td>
		<td><p class='header'>Паскаль</p></td>
	</tr>
	<tr>
		<td v-html='replaceTab(task.alg)'></td>
		<td v-html='replaceTab(task.pas)'></td>
	</tr>
	<tr>
		<td colspan=2><p class='header'>С++</p></td>
	</tr>
	<tr>
		<td colspan=2 v-html='replaceTab(task.cpp)'></td>
	</tr>
	</table><br>
	<p>Последовательно выполните следующее.</p>
	<ol>
		<li>Что выведет программа при вводе числа {{question1}}?</li>
		<li>Приведите пример числа, такого что несмотря на ошибки программа выдаёт верный результат.</li>
		<li>Найдите в программе все ошибки (известно, что их не более двух) и исправьте их. Для каждой ошибки выпишите строку, в которой она допущена, и приведите эту же строку в исправленном виде.</li>
	</ol><br>
	
	<!--Решение задания -->
	<span class='hintButton'  v-on:click='answer = !answer'>Примерное решение</span>
	<div v-if=answer>
		<p class=header>Задание 1</p>
		<p>При вводе числа {{question1}} программа выведет {{task.error(question1)}}</p>
		<br><p class=header>Задание 2</p>
		<p class=annotation>В качестве ответа достаточно привести любое число, дающее верный ответ. Ниже представлены примеры чисел.</p>
		<p v-for='n in task.answer2.random(3)' :key="n"> При вводе числа {{n}} программа выведет верный ответ {{task.error(n)}}</p>
		<br><p class=header>Задание 3</p>
		<p class=annotation>Пример исправления для языка Python. В программах на других языках ошибочные строки и их исправления аналогичны.</p>
		<p v-for='item in task.answer3' :key="item">Строка {{item.before}} заменяется на строку {{item.after}}</p>
	</div>
</template>

<script>
import task from './task.js'

export default {
	name: 'App',
	data() {
		return {
			answer : false,
			task,
			question1: task.answer1.random()
		}
	},
	methods: {
		replaceTab: (str) => str.replace(/\t/g,'&nbsp;&nbsp;&nbsp;'),
	}
}
</script>

<style>
body {
	font-size: 1.5em;
	max-width: 1000px;
	margin: 0 auto;
	line-height: 1.4;
	font-family: sans-serif;
	padding: 20px;
}
p {
	text-align: justify;
}
.code {
	font-family: monospace;
}
.number {
	border: 2px solid;
	padding: 4px;
	font-weight: bolder;
}
table {
	width: 100%;
}
td {
	padding: 10px;
	border: 1px solid;
	vertical-align: top;
}
.header {
	font-weight: bolder;
}
ol {
	list-style: decimal inside;
	text-align: justify;
}
.hintButton {
	color: #0066B3;
	cursor: pointer;
	font-weight: bolder;
	border-bottom: 2px dashed;
}
input {
	font-size: 1em;
	width: 2.5em;
}
.annotation {
	font-style: italic;
	font-size: 0.7em;
}
</style>
