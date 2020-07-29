<template>
    <div class="form">
        <div class="form__body">
          <form @submit.prevent="submit">
            <div class="data">
            <div class="container">
              <h2>Ваши данные</h2>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.last_name.$error }">
                  <label for="">Фамилия <span>*</span></label><br/>
                  <input v-model.trim="$v.defaultState.last_name.$model" type="text" placeholder="Салимова" id="last_name">
                  <div class="error" v-if="$v.defaultState.last_name.$error">Этот пункт обязателен</div>
                </div>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.first_name.$error }">
                  <label for="">Имя <span>*</span></label><br/>                 
                  <input v-model.trim="$v.defaultState.first_name.$model" type="text" placeholder="Мехрибону" id="first_name">
                  <div class="error" v-if="$v.defaultState.first_name.$error">Этот пункт обязателен</div>                  
                </div>
                <div class="form-group">
                  <label for="">Отчество <span></span></label><br/>
                  <input type="text" placeholder="Абдурауфовна" id="major_name">
                </div>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.date_of_birth.$error}">
                  <label for="">Дата рождения <span>*</span></label><br/>
                  <input v-model.trim="$v.defaultState.date_of_birth.$model" type="text" placeholder="07-03-02" id="date_of_birth">
                  <div class="error" v-if="$v.defaultState.date_of_birth.$error">Этот пункт обязателен</div>
                </div>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.phone_number.$error}">
                  <label for="">Номер телефона <span></span></label><br/>
                  <input v-model="$v.defaultState.phone_number.$model" type="text" placeholder="7**********" id="phone_number">
                  <div class="error" v-if="!$v.defaultState.phone_number.numeric">Номер телефона должен состоять только из цифр</div>
                  <div v-if="$v.defaultState.phone_number.$error">
                    <div class="error" v-if="!$v.defaultState.phone_number.isValidPhoneLenght">Номер телефона должен состоять из 11 цифр</div>
                  <div class="error" v-if="!$v.defaultState.phone_number.isValidFirstPhoneDigit">Номер телефона должен должен начинаться с 7</div>
                    </div>
                 
                </div>
                <div class="form-group">
                  <label for="">Пол <span></span></label><br/>
                  <select v-model='defaultState.gender'>
                    <option>М</option>
                    <option>Ж</option>
                  </select>
                </div>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.client.$error }">
                  <label for="">Группа клиентов <span>*</span></label><br/>                 
                  <select v-model='defaultState.client'>
                    <option v-for="clients in defaultState.client_group" :value="clients" :key ="clients" id='clients'>
                      {{ clients }}
                    </option>
                  </select>
                  <div class="error" v-if="$v.defaultState.client.$error">Этот пункт обязателен</div>                  
                </div>
                <div class="form-group">
                  <label for="">Лечащий врач <span></span></label><br/>                 
                  <select v-model="defaultState.doctor">
                    <option v-for="doctor in defaultState.doctors_type" :value="doctor" :key ="doctor" id='doctor'>
                      {{ doctor }}
                    </option>
                  </select>
                </div>
                <div class="form-group">
                  <label for="">Не отправлять СМС <span></span></label><br/>
                  <input type="checkbox" id="sms">
                </div>
            </div>
            </div>
            <div class="address">
            <div class="container">
              <h2>Ваш адрес</h2>
                <div class="form-group">
                  <label for="">Индекс <span></span></label><br/>
                  <input v-model="defaultState.post_index" type="text" id="index" placeholder="******">
                </div>
                <div class="form-group">
                  <label for="">Страна <span></span></label><br/>
                  <input v-model="defaultState.country" type="text" id="country" placeholder="Страна">
                </div>
                <div class="form-group">
                  <label for="">Область <span></span></label><br/>
                  <input  v-model="defaultState.district" type="text" id="district" placeholder="Область"> 
                </div>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.city.$error }">
                  <label for="">Город <span>*</span></label><br/>
                  <input v-model.trim="$v.defaultState.city.$model" type="text" id="city" placeholder="Город">
                  <div class="error" v-if="$v.defaultState.city.$error">Этот пункт обязателен</div>
                </div>
                <div class="form-group">
                  <label for="">Улица <span></span></label><br/>
                  <input  v-model="defaultState.street" type="text" id="street" placeholder="Улица">
                </div>
                <div class="form-group">
                  <label for="">Дом <span></span></label><br/>
                  <input  v-model="defaultState.house" type="text" id="house" placeholder="Дом">
                </div>
            </div>
            </div>
            <div class="passport">
            <div class="container">
              <h2>Ваши паспортные данные</h2>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.document_type.$error }">
                <label for="">Тип документа <span>*</span></label><br/>
                <select v-model='defaultState.document_type'>
                    <option v-for="document in defaultState.doc_type" :key ="document" id='clients'>
                      {{ document }}
                    </option>
                  </select>
                  <div class="error" v-if="$v.defaultState.document_type.$error">Этот пункт обязателен</div>
              </div>
              <div class="form-group">
                  <label for="">Серия <span></span></label><br/>
                  <input v-model="defaultState.passport_series" type="text" id="passport_series" placeholder="Серия паспорт">
                </div>
                <div class="form-group">
                  <label for="">Номер <span></span></label><br/>
                  <input v-model="defaultState.passport_number" type="text" id="passport_number" placeholder="Номер паспорт">
                </div>
                <div class="form-group">
                  <label for="">Кем выдан <span></span></label><br/>
                  <input v-model="defaultState.passport_giver" type="text" id="passport_giver" placeholder="Кем выдан">
                </div>
                <div class="form-group" :class="{ 'form-group--error': $v.defaultState.date_of_document.$error }">
                  <label for="">Дата выдачи <span>*</span></label><br/>
                  <input v-model.trim="$v.defaultState.date_of_document.$model" type="text" id="data_of_document" placeholder="Дата">
                  <div class="error" v-if="$v.defaultState.date_of_document.$error">Этот пункт обязателен</div>
                </div>
            </div>
            </div>
            <div class="container">
              <button type="submit" :disabled="submitStatus === 'PENDING'" class='btn'>Submit</button>
              <p class="typo__p success" v-if="submitStatus === 'OK'">Вы успешно зарегистрированы!</p>
              <p class="typo__p fail" v-else-if="submitStatus === 'ERROR'" >Пожалуйста, заполните форму правильно!</p>
              <p class="typo__p" v-else-if="submitStatus === 'PENDING'">Загрузка...</p>
              <p class="typo__p" v-else></p>

            </div>
          </form>
        </div>

    </div>
</template>

<script>
import { required,numeric} from 'vuelidate/lib/validators'
const isValidPhoneLenght=(phone_number)=> phone_number.length===11;
const isValidFirstPhoneDigit=(phone_number)=>phone_number.charAt(0)==='7';
export default {
  name: 'Forms',

  data(){
    return {
      defaultState:{
        last_name: null,
    first_name: null,
    major_name: null,
    date_of_birth:null,
    phone_number: '',
    client_group:['VIP', 'Проблемные', 'ОМС'],
    client:null,
    document_type:null,
    doctors_type:['Иванов', 'Захаров', 'Чернышева'],
    doc_type:['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение'],
    city:null,
    document: null,
    date_of_document: null,
    gender: null,
    post_index: null,
    country: null,
    district: null,
    house: null,
    street: null,
    passport_series: null,
    passport_number: null,
    passport_giver: null,
    },
    submitStatus: null,

    }
  },
  validations: {
    defaultState:{
    last_name: {
      required
    },
    first_name:{required},
    date_of_birth:{required},
    client:{required},
    city:{required},
    document_type:{required},
    date_of_document:{required},
    phone_number: {
 numeric, isValidPhoneLenght, isValidFirstPhoneDigit
    }
    }
  },



  methods: {
    submit() {
      if (this.$v.$invalid) {
        this.$v.$touch()
        this.submitStatus = 'ERROR';
        return;
      } else{
          this.submitStatus = 'PENDING';
          setTimeout(() => {
          this.submitStatus = 'OK';
        }, 500)
      }

    },

    }
    
  
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang = 'scss'>
@import './Forms.scss';
</style>