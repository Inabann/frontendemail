<template>
	<el-main>
		<el-table
	    :data="data"
	    style="width: 100%">
	    <el-table-column
	      label="Date"
	      width="180">
	      <template slot-scope="scope">
	        <span style="margin-left: 10px">{{ scope.row.date }}</span>
	      </template>
	    </el-table-column>
	    <el-table-column
	      label="Username"
	      width="80">
	      <template slot-scope="scope">
	        <span>{{scope.row.username.username}}</span>
	      </template>
	    </el-table-column>
	    <el-table-column
	      label="monto"
	      width="80">
	      <template slot-scope="scope">
	        <span>{{scope.row.amount}}</span>
	      </template>
	    </el-table-column>
	    <el-table-column
	      label="pagar"
	      width="80">
	      <template slot-scope="scope">
	        <span>{{scope.row.payout}}</span>
	      </template>
	    </el-table-column>
	    <el-table-column
	      label="wallet"
	      width="180">
	      <template slot-scope="scope">
	        <span>{{scope.row.username.btca}}</span>
	      </template>
	    </el-table-column>
	    <el-table-column
	      label="email"
	      width="180">
	      <template slot-scope="scope">
	        <span>{{scope.row.username.email}}</span>
	      </template>
	    </el-table-column>
	    <el-table-column
	      label="Operations">
	      <template slot-scope="scope">
	        <el-button
	          size="mini"
	          @click="pay(scope.$index, scope.row)">Pagar</el-button>
	        <el-button
	          size="mini"
	          type="danger"
	          @click="email(scope.$index, scope.row)">email</el-button>
	      </template>
	    </el-table-column>
	  </el-table>
	</el-main>
</template>

<script>
import axios from 'axios'
const url = 'http://localhost:5000/api/deposits/'

export default {

  name: 'Deposits',

  data () {
    return {
    	data: []
    }
  },
  methods:{
  	async pay(index,datos){
  		await axios.post(url+'change',datos)
  		this.data.splice(index,1)
  	},
  	async email(index, datos){
  		await axios.post(url+'email',datos)
  		console.log('enviado')
  	}
  },
  async mounted(){
  	const a = await axios.get(url)
  	this.data = a.data
  }
}
</script>

<style lang="css" scoped>
</style>