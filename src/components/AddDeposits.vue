<template>
  <el-main>
    <el-form label-width="100px" >
    <el-form-item label="cantidad">
      <el-input v-model="deposit.amount"></el-input>
    </el-form-item>
    <el-form-item label="username">
      <el-input v-model="deposit.username.username"></el-input>
    </el-form-item>
    <el-form-item label="btca">
      <el-input v-model="deposit.username.btca"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="add">Create</el-button>
      <el-button  @click="test">Generar</el-button>
    </el-form-item>
  </el-form>
  </el-main>
</template>

<script>
import faker from 'faker'
import moment from 'moment'
import momentRandom from 'moment-random'
import axios from 'axios'
const url = 'http://localhost:5000/api/deposits/'

export default {
  name: 'AddDeposits',
  data(){
    return {
      deposit:{
        amount: 0,
        payout: 0,
        status: false,
        date: new Date(),
        username:{
          username: '',
          email:'',
          btca: '',
          refby: '',
          uid:''
        }
      }
    }
  },
  methods:{
    test(){
      this.deposit.username.username = faker.internet.userName()
      this.deposit.username.btca = faker.finance.bitcoinAddress()
      this.deposit.date = new Date() //momentRandom(moment(),moment('2019-05-20 00:00:00'))._d
      // eslint-disable-next-line
    },
    async add(){
      this.deposit.amount = parseFloat(this.deposit.amount)
      this.deposit.payout = this.deposit.amount*2
      //this.deposit.date = new Date(this.deposit.date)
      await axios.post(url,this.deposit)
    }
  }

}
</script>

<style >
  
</style>
