<template>
<transition name="fade">

  <div class="login-box" v-if="flag" key="login">
      <h2>OnlieJudge登录界面</h2>
      <form>
        <div class="user-box">
          <input type="text" name="" required="">
          <label>Username</label>
        </div>
        <div class="user-box">
          <input type="password" name="" required="">
          <label>Password</label>
        </div>
        
        <a class="forget" href="#">忘记密码?</a>
        <a class="register" @click="toRegister" href="#">注册</a>
        <a href="#">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
          Submit
        </a>
      </form>
    </div>

  <div class="login-box" v-else key="register">
    <h2>OnlieJudge注册界面</h2>
    <form>
      <div class="user-box">
        <input type="text" name="" required="">
        <label>Username</label>
      </div>
      <div class="user-box">
        <input type="password" name="" required="">
        <label>Password</label>
      </div>
      <div class="user-box">
        <input type="text" name="" required="">
        <label>Email</label>
      </div>
      <div class="user-box">
          <input type="text" name="" required="">
          <label>Verification Code</label>
          <a href="#">发送验证码</a>
        </div>
      <a href="#" class="register-commit">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        提交
      </a>
      <a href="#" @click="toLogin">
        取消
      </a>
    </form>
  </div>

</transition>

</template>

<script>
import { ref, reactive } from 'vue';
export default {
  setup() {
  let user = {
    flag : true,
    
  }
  let flag = ref(true);
  function toRegister(){
      console.log("6666")
      flag.value = false
      console.log(flag)
    }
    function toLogin(){
      console.log("6666")
      flag.value = true
      console.log(flag)
    }  
    return{
      toRegister,
      flag,
      toLogin
    }  
  }  
}

</script>

<style scoped type='text/css'>
.register-commit{
  margin-right: 50px;
}  
/** 动画进行时的class **/
.fade-enter-active{
    transition: opacity .5s;
  }
.fade-enter{
    opacity: 0;
}
.fade-leave-active{
  transition: opacity .5s;
}
.fade-leave-to{
  opacity: 0;
}

.forget {
  margin-right: 124px;
  margin-left: -15px;
}
.register {
  margin-right: -17px;
}

html {
  height: 100%;
}
body {
  margin:0;
  padding:0;
  font-family: sans-serif;
  background: linear-gradient(#141e30, #243b55);
}

.login-box {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 400px;
  padding: 40px;
  transform: translate(-50%, -50%);
  background: rgba(0,0,0,.5);
  box-sizing: border-box;
  box-shadow: 0 15px 25px rgba(0,0,0,.6);
  border-radius: 10px;
}

.login-box h2 {
  margin: 0 0 30px;
  padding: 0;
  color: #fff;
  text-align: center;
}

.login-box .user-box {
  position: relative;
}

.login-box .user-box input {
  width: 100%;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  margin-bottom: 30px;
  border: none;
  border-bottom: 1px solid #fff;
  outline: none;
  background: transparent;
}
.login-box .user-box label {
  position: absolute;
  top:0;
  left: 0;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  pointer-events: none;
  transition: .5s;
}

.login-box .user-box input:focus ~ label,
.login-box .user-box input:valid ~ label {
  top: -20px;
  left: 0;
  color: #03e9f4;
  font-size: 12px;
}

.login-box form a {
  position: relative;
  display: inline-block;
  padding: 10px 20px;
  color: #03e9f4;
  font-size: 16px;
  text-decoration: none;
  text-transform: uppercase;
  overflow: hidden;
  transition: .5s;
  margin-top: 40px;
  letter-spacing: 4px
}

.login-box a:hover {
  background: #03e9f4;
  color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 5px #03e9f4,
              0 0 25px #03e9f4,
              0 0 50px #03e9f4,
              0 0 100px #03e9f4;
}

.login-box a span {
  position: absolute;
  display: block;
}

.login-box a span:nth-child(1) {
  top: 0;
  left: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #03e9f4);
  animation: btn-anim1 1s linear infinite;
}

@keyframes btn-anim1 {
  0% {
    left: -100%;
  }
  50%,100% {
    left: 100%;
  }
}

.login-box a span:nth-child(2) {
  top: -100%;
  right: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(180deg, transparent, #03e9f4);
  animation: btn-anim2 1s linear infinite;
  animation-delay: .25s
}

@keyframes btn-anim2 {
  0% {
    top: -100%;
  }
  50%,100% {
    top: 100%;
  }
}

.login-box a span:nth-child(3) {
  bottom: 0;
  right: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(270deg, transparent, #03e9f4);
  animation: btn-anim3 1s linear infinite;
  animation-delay: .5s
}

@keyframes btn-anim3 {
  0% {
    right: -100%;
  }
  50%,100% {
    right: 100%;
  }
}

.login-box a span:nth-child(4) {
  bottom: -100%;
  left: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(360deg, transparent, #03e9f4);
  animation: btn-anim4 1s linear infinite;
  animation-delay: .75s
}

@keyframes btn-anim4 {
  0% {
    bottom: -100%;
  }
  50%,100% {
    bottom: 100%;
  }
}

</style>
