<template>
  <form @submit.prevent="submitdata">
      <label>Email:</label>
      <input type="email" v-model="email" required>
      <label>Password:</label>
      <input type="password" v-model="password" required>
      <div v-if="passworderror">{{passworderror}}</div>
      <label>Role:</label>
      <select v-model="role">
          <option value="Developer">Web Developer</option>
          <option value="Designer">Web Designer</option>
      </select>
      <label>Skills</label>
      <input type="text" v-model="Tempskill" @keyup="addskill">
      <div v-for="skill in skills" :key="skill">{{skill}}</div>
      <div class="terms" >
          <input type="checkbox" v-model="terms" required>
          <label>Accept Terms And conditions</label>
      </div>
      <div class="submit">
          <button>Create An Account</button>
      </div>

  </form>
</template>

<script>
export default {
    data(){
        return{
            email:'',
            password:'',
            role:'',
            terms:false,
            Tempskill:'',
            skills:[],
            passworderror:''
        }
    },
    methods:{
        addskill(e){

            if(e.key===',' && this.Tempskill){
                    if(!this.skills.includes(this.Tempskill)){
                        this.skills.push(this.Tempskill)
                    }
                
                this.Tempskill=''

            }
        },
        submitdata(){
         
                
                console.log('form submutted')
         
                this.passworderror=this.password.length>5 ?
                '' :"password must contain atleast 6 chars"
            if(!this.passworderror)
            {
                console.log('email:', this.email)
                console.log('password:', this.password)
                console.log('role:', this.role)
                console.log('skill:', this.skills)
                console.log('terms accepted:', this.terms)

            }
            


        }
    }

}
</script>

<style>
form{
    max-width: 400px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 20px;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 10px 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing:1px;
    font-weight: bold;
}
input,select{
    display: block;
    padding: 10px 6px;
    width:100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin:0px 10px 0px 0px;
   position: relative;
   top: 2px;
}
button{
    background: lightcoral;
    border: 0;
    padding: 10px 20px;
    margin-top: 10px;
    color: white;
    border-radius: 20px;
}
.submit{
    text-align: center;
}

</style>