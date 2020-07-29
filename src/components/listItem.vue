<template>
  <div class="item">
    <p>{{item.description}}</p>
    <button v-on:click="removeTask">&#215;</button>
  </div>
</template>

<script>
export default {
	props: {
    item: {
      type: Object,
      required: true
    }
  },
  methods: {
  	removeTask() {
  		this.$emit('removeTask', {
    	  id: this.item.id
    	});
  	}
  }
}
</script>

<style lang="scss">
	.item {
		position: relative;
		padding: 9px 40px 6px 5px;
		width: 550px;
		margin: 0 auto;
		border-bottom: 1px solid #cacacc;
		p {
			color: #cacacc;
			margin-bottom: 0;
		}
		button {
			color: #cacacc;
			border: 0;
			background: inherit;
			position: absolute;
			right: 2px;
			top: 0
		}
	}

	@media (max-width: 634px) {
    .item {
    	width: 400px;
    }
  }

  @media (max-width: 464px) {
  	.item {
    	width: 300px;
    }
  }
</style>