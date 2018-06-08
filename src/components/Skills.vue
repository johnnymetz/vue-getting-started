<template>
  <div class="hello">
    <!-- {{ name }} -->

    <!-- {{ btnState ? 'The button is disabled' : 'The button is active' }}
    <button v-on:click="changeName" v-bind:disabled="btnState">Change Name</button> -->

    <div class="holder">

      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'required|min:5'" name="skill">

        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>

        <!-- {{ skill }} -->

        <!-- <input type="checkbox" id="checkbox" v-model="checked"> -->
      </form>

      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for='(data, index) in skills' :key='index'>
            <!-- {{ index }}. -->
            {{ data.skill }}
            <!-- SVG icon -->
            <!-- <symbol id="icon-cross" viewBox="0 0 32 32">
              <title>cross</title>
              <path d="M31.708 25.708c-0-0-0-0-0-0l-9.708-9.708 9.708-9.708c0-0 0-0 0-0 0.105-0.105 0.18-0.227 0.229-0.357 0.133-0.356 0.057-0.771-0.229-1.057l-4.586-4.586c-0.286-0.286-0.702-0.361-1.057-0.229-0.13 0.048-0.252 0.124-0.357 0.228 0 0-0 0-0 0l-9.708 9.708-9.708-9.708c-0-0-0-0-0-0-0.105-0.104-0.227-0.18-0.357-0.228-0.356-0.133-0.771-0.057-1.057 0.229l-4.586 4.586c-0.286 0.286-0.361 0.702-0.229 1.057 0.049 0.13 0.124 0.252 0.229 0.357 0 0 0 0 0 0l9.708 9.708-9.708 9.708c-0 0-0 0-0 0-0.104 0.105-0.18 0.227-0.229 0.357-0.133 0.355-0.057 0.771 0.229 1.057l4.586 4.586c0.286 0.286 0.702 0.361 1.057 0.229 0.13-0.049 0.252-0.124 0.357-0.229 0-0 0-0 0-0l9.708-9.708 9.708 9.708c0 0 0 0 0 0 0.105 0.105 0.227 0.18 0.357 0.229 0.356 0.133 0.771 0.057 1.057-0.229l4.586-4.586c0.286-0.286 0.362-0.702 0.229-1.057-0.049-0.13-0.124-0.252-0.229-0.357z"></path>
            </symbol>
            <svg class="icon icon-cross" v-on:click="remove(index)"><use xlink:href="#icon-cross"></use></svg> -->
            <!-- Font Awesome icon -->
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>

      <p>These are the skills that you possess.</p>

      <!-- <p v-if='skills.length >= 1'>You have more than 1 skill</p>
      <p v-else>You have less than or equal to 1 skill</p>

      <div v-bind:class="{ 'alert': showAlert, 'another-class': showClass }">showAlert and showClass</div>

      <div v-bind:class="alertObject">alertObject</div>

      <div v-bind:style="{ backgroundColor: bgColor, width: bgWidth, height: bgHeight }">style binding</div> -->

    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      // name: 'Coursetro',
      // btnState: true,
      skills: [
        {"skill": "Vue.js"},
        {"skill": "Frontend Developer"}
      ],
      // showAlert: true,
      // showClass: true,
      // alertObject: {
      //   alert: true,
      // },
      // bgColor: 'cyan',
      // bgWidth: '50%',
      // bgHeight: '30px'

      skill: '',
      // checked: false
    }
  },
  methods: {
    addSkill() {
      this.$validator.validate().then(result => {
        //console.log("Here: " + result);
        if (result) {
          this.skills.push({skill: this.skill});
          this.skill = '';
          // console.log("This checkbox value is: " + this.checked);
        } else {
          console.log('Not valid');
        }
      });
    },
    remove(id) {
      this.skills.splice(id, 1);
    }
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<!-- <style scoped>
  .alert {
    background-color: yellow;
    width: 100%;
    height: 30px;
  }
  .another-class {
    border: 5px solid black;
  }
</style> -->

<style src="./Skills.css"></style>
