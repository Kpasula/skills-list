<template>
  <div class="container">
    <div class="holder">
      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter Your Skills"  v-model="skill">
      </form>

      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" :key='index'>{{index}}. {{data.skill}}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skills: [
          { "skill": "Vue.js" },
          { "skill": "Frontend Developer" },
          { "skill": "Python"},
          { "skill": "Django"},
    ]
    }
  },
  methods : {
      addSkill(){
          this.skills.push({skill: this.skill});
          this.skill = ''; 
       },
        remove(id) {
          this.skills.splice(id,1);
        }
    }
}
</script>

<style scoped>

@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 

  .holder {
    background: rgb(134, 33, 117);
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #408fb9;
    border-left: 5px solid #ac8125;
    margin-bottom: 2px;
    color: #0d0425;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: rgb(192, 119, 70);
  }

  .container {
    box-shadow: 0px 0px 40px rgb(192, 25, 25);
  }

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #dd6f26;
    color: #f5f1f2;

  }
   .alert {
    background: #e9bc29;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }
  .alert-in-enter-active {
    animation: bounce-in .5s;
  }
  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
i {
  float:right;
  cursor:pointer;
}
</style>