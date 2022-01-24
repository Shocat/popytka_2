<template>
  <form  class="registr" @submit.prevent="on_submit">
    <h1>Регистрация</h1>
    
   
    <div>
<input type="text" placeholder="Имя"  v-model.trim="name"  title="Введите свое имя" :class="{invalid: ($v.name.$dirty && !$v.name.required)||($v.name.$dirty && !$v.name.alpha)}" > 
      <p v-if="$v.name.$dirty && !$v.name.required">Поле имя не должно быть пустым</p>
      <p v-else-if="$v.name.$dirty && !$v.name.alpha">Введите корректно свое имя на английском языке не используя цифры и пробелы</p>
    </div>

      <div>
      <input type="text"  placeholder="Введите номер серию паспорта" v-model.trim="passport" title="Введите номер серию паспорта" :class="{invalid: ($v.passport.$dirty && !$v.passport.required)||($v.passport.$dirty && !$v.passport.numeric)}" >
      <p v-if="$v.passport.$dirty && !$v.passport.required">Поле Паспорт не должно быть пустым</p>
    <p v-else-if="$v.passport.$dirty && !$v.passport.numeric">Введите корректно свой паспорт</p>
    </div>

    
        <div> <input type="date"   v-model.trim="year"  title="Введите дату своего рождения"  :class="{invalid: ($v.year.$dirty && !$v.year.required)}"> 
        <p v-if="$v.year.$dirty && !$v.year.required">Поле Дата не должно быть пустым</p>
        </div>

    <div><input type="email" id="email"   v-model.trim="email" placeholder="Электронный адрес" title="Введите свой email" :class="{invalid: ($v.email.$dirty && !$v.email.required)||($v.email.$dirty && !$v.email.email)}" > 
    <p v-if="$v.email.$dirty && !$v.email.required">Поле Email не должно быть пустым</p>
    <p v-else-if="$v.email.$dirty && !$v.email.emai">Введите корректно свой Email</p>
    </div>
    <div><input type="tel" id="tel" v-model.trim="tel"   placeholder="+7(___)___-__-__"  title="Введите свой номер телефона" :class="{invalid: ($v.tel.$dirty && !$v.tel.required)||($v.tel.$dirty && !$v.tel.numeric)}" >
    <p v-if="$v.tel.$dirty && !$v.tel.required">Поле Телефон не должно быть пустым</p>
    <p v-else-if="$v.tel.$dirty && !$v.tel.numeric">Введите корректно свой номер телефона</p>
    </div>
   
   

    <button  type="submit"  class="btn">
      Регистрация
    </button>
  </form>
</template>

<script>
import { required, maxLength, alpha, email, numeric} from 'vuelidate/lib/validators';


export default {
  data() {
    return {
     passport:'' ,
      name: '',
      year:'' ,
      tel: '',
      email:'',} 
  },
  methods:{
    on_submit(){
      if (this.$v.$invalid){
        this.$v.$touch()
        return
      }
      alert("Удачная рега")

    }
  },

 
  validations: {
    // helpers.regex(/^[а-яА-ЯёЁa-zA-Z0-9]+$/
    name: {
      required,
      maxLength: maxLength(10), alpha
    },
     passport: { numeric,
      required,
      
    },
    year: {
      required,
    },
     tel:{required,numeric
    },
    
    email:{ required, email }

  },
  

};
</script>








<style>
* {
    
    padding: 0;
    box-sizing: border-box;}


.registr {
    background: #F1F5FE;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    
}
.registr input{
    padding: 5px;
    margin: 5px;
    width: 250px;
    height: 50px;
    border-radius: 10px;
}
.registr input:hover{
    background-color: aquamarine;}


.btn{
    border-radius: 10px;
    height: 40px;
    width: 100px;

}
.btn:hover{
    background-color: rgb(51,255,153);  
}


input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>




