<template>
  <div class="container">
    <form class="card" @submit.prevent="submitForms">
      <h1>Анкета на Vue разработчика!</h1>
     
      <appInput 
      placeholder="Введите имя" 
      :error="errors.name"
      label="Как тебя зовут?"
      v-model="name" 
      >
      </appInput>
      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input type="number" id="age" v-model.number="age">
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="city" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="kgd">Калининград</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Готов к переезду в Токио?</span>
        <div class="checkbox">
          <label><input type="radio" name="trip" value="yes" v-model="choose"/> Да</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" name="trip" value="no" v-model="choose"/> Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Что знаешь во Vue?</span>
        <div class="checkbox">
          <label><input type="checkbox"  name="vuex" value="Vuex" v-model="skills"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox"  name="vue_Cli" value="Vue Cli" v-model="skills"/> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox"  name="vue_Router" value="Vue Router" v-model="skills"/> Vue Router</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Правила нашей компании</span>
        <div class="checkbox">
          <label><input type="checkbox" name="agree" value="agree" v-model="rules">С правилами согласен</label>
        </div>
      </div>

      <button  type="submit" class="btn primary">Отправить</button>
    </form>
  </div>
</template>

<script>
import appInput from './appInput.vue'
  export default {
    components:{appInput},
    name:"App",
    data(){
        return{
          name:'',
          age: 23,
          city: '',
          choose: '',
          skills: [],
          rules: '',
          errors:{
            name:null,
          }
        }
      },
    methods:{
      formIsValid(){
        let isValid = true
        if(this.name.length === 0){
          this.errors.name="Имя не может быть пустым"
          isValid = false
        }
        else{
          this.errors.name = null
        }
        return isValid
      },
      submitForms(){
        if(this.formIsValid()){
          console.group('Form Data');
          console.log('Name:', this.name)
          console.log('Age:', this.age)
          console.log('City:', this.city)
          console.log('Choose:', this.choose)
          console.log('Your skills:', this.skills)
          console.log('Our rules:', this.rules)
          console.groupEnd()
        }
        
      },
      
    },
  }
  
</script>

<style>
.form-control small{
  color: red;
}
.form-control .invalid input{
  border: 2px solid red;
}
</style>
