<template>
    <div class="form-control"
    :class="{invalid:error}">
      <label :for="id">{{label}}</label>
      <input type="text" 
      :id="id" 

      :placeholder="placeholder" 
      :value="modelValue" 
      @input="change">
      <small style="fontSize:20px" v-if="error"><b>{{error}}</b></small>
    </div>
</template>

<script>
    export default{
      name: 'appInput',
      data(){
        return{
          id: 'input'+Math.random(),
        }
      },
      props:{
        label: String,
        error: String,
        placeholder: String,
        modelValue: String,
      },
      emits:['update:modelValue'],
      methods:{
        change(event){
          this.$emit('update:modelValue',event.target.value)
        }
      },
    }
</script>