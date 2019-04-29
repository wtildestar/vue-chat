<template>
  <div class="welcome container">
    <div class="card">
      <div class="card-content center-align">
        <h2 class="teal-text">Vue Chat</h2>
        <form @submit.prevent="enterChat">
          <label for="name">Введите ваше имя:</label>
          <input type="text" name="name" v-model="name">
          <p v-if="feedback" class="red-text">{{ feedback }}</p>
          <button class="btn-large btn-floating teal pulse">Вход</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Welcome',
  data () {
    return {
	  name: null,
	  feedback: null
    }
  },
  methods:{
    enterChat(){
		if(this.name){
			this.$router.push({ name: 'Chat', params: { name: this.name } })
		} else {
			this.feedback = 'Введите имя чтобы продолжить'
		}
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.welcome{
	max-width: 350px;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%,-50%);
}
.welcome h2{
	font-size: 2.5em;
}
.welcome .btn-floating{
  margin-top: 15px;
}
</style>
