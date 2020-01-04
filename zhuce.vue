<template>

 <div class="zong" style="height: 1000px;background-image: url(../../static/login_bg_m1.jpg);background-position: -500px -100px; width: 100%;  ">
   <div class="erceng" >
   <table>
         <tr>
           <td>用&nbsp; 户&nbsp; 名:</td>
           <td><input type="text" class="form-control" placeholder="请填写用户名"/> </td>
         </tr>
         <tr>
             <td >密 &nbsp;&nbsp;&nbsp;&nbsp; &nbsp; 码:</td>
       <td><input type="password" class="form-control" placeholder="请输入密码:6-12位" /></td>
         </tr>
         <tr>
             <td>确认密码:</td>
           <td><input type="password" class="form-control" placeholder="请输入密码"/> </td>
         </tr>

          <tr>

            <td>  </td>


            <td><input type="text" v-model="keycode" placeholder="验证码"   class="form-control pull-left" /> <img @click="changeKeycode($event)" id="sys_keycode" class="pull-left" src="http://127.0.0.1:8090/backstage/defaultKaptcha" />  </td>

          </tr>


          <tr>
          <td  colspan="2">
            <button class="btn btn-danger btn-block" @click="doRegiste()"
            style="background-color: #FE5F7B;border: 0px;border-radius: 0px;height: 40px;">注册</button>


          </td>
         </tr>
   </table>
   </div>
 </div>

</template>

<script>
export default{
  data(){
    return{
 logname:"",
 password:"",
 password_repeat:"",
   keycode:"",
   msg:"",
   showmsg:false,
   msgtext:[
       "验证码有误","注册成功","用户名已存在"


   ]


 };


  },
  methods:{
    changeKeycode(event){

      event.target.src="http://127.0.0.1:8090/backstage/defaultKaptcha";

    },
    doRegiste(){
      var ob =this;
      if(ob.logname.length==0){
        ob.msg="用户名不能为空";
        ob.showmsg=true;
        return
      }
      if(ob.password.length==0){
        ob.msg="密码不能为空";
        ob.showmsg=true;
        return;
      }
      if(ob.password!=ob.password_repeat){
        ob.msg="两次密码不一致";
        ob.showmsg=true;
        return
      }
      if(ob.keycode,length==""){
        ob.showmsg="验证码不能为空";
        ob.showmsg=true;
        return
      }

    }
  }

}

</script>



<style>
  .zong{
  width: 1349px;
  height: 500px;
  padding: 0px;
  margin: 0px;
  }
  .erceng{
    width: 1850px;
  }
  .erceng table{
    margin-left: 700px;
  }
  td{
    line-height: 60px;
  }

</style>
