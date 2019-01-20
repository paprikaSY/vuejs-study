<template>
	<div class="input-box shadow">
		<input type="text" v-model="newTodoItem" placeholder="Type what you have to do" @keyup.enter="addTodo">
		<span class="add-container" @click="addTodo">
			<i class="add-btn fa fa-plus" aria-hidden="true"></i>
		</span>
	</div>
</template>

<script>
export default {
	data() {
		return {
			newTodoItem: ''
		}
	},
	methods: {
		addTodo() {
			if(this.newTodoItem !== "") {
				var value = this.newTodoItem && this.newTodoItem.trim()
				this.$emit('addTodo', value)
				this.clearInput()
			}
		},
		clearInput() {
			this.newTodoItem = ''
		}
	}
}
</script>

<style>
input:focus {
	outline: none;
}

.input-box {
	background-color: #ffffff;
	height: 50px;
	line-height: 50px;
	border-radius: 5px;
}

.input-box input {
	border-style: none;
	font-size: 0.9rem;
}

.add-container {
	float: right;
	background: linear-gradient(to right, #6478fb, #8763fb);
	display: inline-block;
	width: 3rem;
	border-radius: 0 5px 5px 0;
}
.add-btn {
	color: #ffffff;
	vertical-align: middle;
	cursor: pointer;
}
</style>