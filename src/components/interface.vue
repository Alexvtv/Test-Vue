<template>
  <div class="interface" :style="{ animation: this.additionalArea ? '0.6s show-area forwards' : '0.6s hide-area forwards'}">
    <img src="./../assets/logo.png" />
    <div class="search-menu">
      <input v-model.lazy="searchValue" v-on:change="changeSearchValue" type="text" class="form-control"> <p>Поиск</p>
    </div>
    <button class="btn btn-primary" v-on:click="changeAdditionalArea">{{this.additionalArea ? 'Скрыть' : 'Добавить'}}</button>
    <div class="area">
    	<input v-model="newTaskText" type="text" class="form-control">
    	<button class="btn btn-success" v-on:click="addTask">Создать</button>
    </div>
  </div>
</template>

<script>
	export default {
		data() {
			return {
				searchValue: "",
				newTaskText: "",
				additionalArea: false,
        src: './assets/logo.png'
			}
		}, methods: {
			changeAdditionalArea() {
				this.additionalArea = !this.additionalArea
			},
			addTask() {
				if(/\S/.test(this.newTaskText)) {
					this.$emit('addNewTask', {
    			  text: this.newTaskText
    			});
    			this.newTaskText = ""
				}
			},
			changeSearchValue() {
				this.$emit('setSearchValue', {
    		  value: this.searchValue
    		});
			}
		}
	}
</script>

<style lang="scss">
	.interface {
		overflow-y: hidden;
    padding: 40px 100px 0 100px;
    height: 100px;
    border-bottom: 2px solid #cacacc;
    &>img {
      position: absolute;
      left: 20px;
      top: 28px;
      height: 60px
    }
    input {
    	border: 2px solid #212121;
    }
    button {
    	background-color: #50a197;
    	border: 2px solid #cacacc;
    	width: 150px;
      display: inline-block;
      float: right;
      transition: none;
    }
    button:active, button:focus {
    	background-color: #50a197;
    	border: 2px solid #858585;
    	box-shadow: none;
    }
    button:hover {
      background-color: #77ebdd;
      border: 2px solid #858585;
    }
    .search-menu {
      display: inline-block;
      width: 220px;
      p {
        display: inline-block;
        width: 60px;
        font-size: 20px;
      }
      input {
        display: inline-block;
        width: 150px;
        margin: 0;
      }
    }
    .area {
    	margin-top: 20px;
    	input {
    		width: 400px;
    		display: inline-block;
    		float: left;
    	}
    	button {
    		margin-left: 20px;
    		float: left;
    	}
    }
  }

  @media (max-width: 784px) {
  	.interface {
  		button {
  			width: 100px;
  		}
  		.area {
  			input {
  				width: 300px;
  			}
  		}
  	}
  }

  @media (max-width: 634px) {
  	.interface {
  		padding: 40px 30px 0 90px;
  		.area {
  			input {
  				width: 224px;
  			}
  		}
  	}
  }

  @media (max-width: 464px) {
  	.interface {
      padding: 40px 30px 0 80px;
      &>img {
        top: 33px;
        height: 50px
      }
			button {
				width: 90px;
				font-size: 15px;
			}
			.search-menu {
  			width: 200px;
      	p {
      		width: 40px;
      		font-size: 16px;
      	}
        input {
          width: 130px;
        }
      }
  		.area {
  			input {
  				width: 200px;
  			}
  		}
  	}
  }

  @keyframes show-area {
		from {height: 100px}
		to {height: 170px}
  }

  @keyframes hide-area {
		from {height: 170px}
		to {height: 100px}
  }
</style>