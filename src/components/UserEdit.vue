<template>
  <div class="yellow lighten-3 pa-3">
    <h3>회원 정보를 수정할 수 있습니다.</h3>
    <p>수정사항</p>
      <v-container class = "px-0" fluid>
      <v-text-field
        label="이름"
        v-model="user.name"
      ></v-text-field>
      <v-text-field
        label="주소"
        v-model="user.address"
      ></v-text-field>
      <v-text-field
        label="전화번호"
        v-model="user.phone"
      ></v-text-field>
      <v-radio-group v-model="user.hasDog">
        <v-radio
          label="반려견 있음"
          :value="true"
        ></v-radio>
      </v-radio-group>
      <v-radio-group v-model="user.hasDog">
        <v-radio
          label="반려견 없음"
          :value="false"
        ></v-radio>
      </v-radio-group>
      <v-btn @click = "chanegeuser">수정 완료</v-btn>
    </v-container>
  </div>
</template>

<script>
import {eventBus} from "../main"
  export default{
    proops: ['name', 'address', 'phone', 'hasDog'],
    data(){
      return{
        user:{}
      }
    },
    created(){
      this.user.name = this.name
      this.user.addrss=this.address
      this.user.phone=this.phone
      this.user.hasDog=this.hasDog
    },
    methods:{
      chanegeuser(){
        this.$emit('child', this.user)
        //eventBus.$emit("userWasEdited", new Date())
        eventBus.userWasEdited(new Date())
      }
    }
  }
</script>
