<template>
  <div class="blue lighten-3 pa-3">
    <h1>User 컴포넌트</h1>
    <p>이름: {{name}}</p>
    <p>{{helloToMixin}}</p>
    <p>{{getDateAndTime(createAt)}}</p>
    <v-btn @click = "changeName()">이름 변경</v-btn>
    <hr>
    <v-layout row wrap>
      <v-flex xs12 sm6>
        <UserDetail
          :name = 'name'
          :address="address"
          :phone="phone"
          :hasDog="hasDog">
        </UserDetail>
      </v-flex>
      <v-flex xs12 sm6>
        <UserEdit
          :name = 'name'
          :address="address"
          :phone="phone"
          :hasDog="hasDog"
          @child="parents">
        </UserEdit>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import UserDetail from "./UserDetail.vue"
import UserEdit from "./UserEdit.vue"
import {dateFormat} from "../mixins/dateFormat"
export default {
  components: {
    UserDetail,
    UserEdit
  },
  data(){
    return{
      name: 'Kibum',
      address: 'Goyang',
      phone: '010-3419-0582',
      hasDog: true,
      createdAt: null
    }
  },
  methods:{
    changeName(){
      if(this.name == "Kibum"){
        this.name = '뷰 제이에스'
      }else{
        this.name = "Kibum"
      }

    },
    parents(user){
      this.name = user.name
      this.address = user.address
      this.phone = user.phone
      this.hasDog = user.hasDog
    }
  },
  created(){
    this.createAt = new Date()
  },
  computed:{
    helloToMixin(){
      return this.mixinData + '안녕하세요!'
    }
  },
  mixins:[dateFormat]
}
</script>
